---
name: npx-skills
description: >-
  Install, find, update, and manage agent skills using the npx skills CLI tool. You MUST load this skill when asked to use the npx skills command.
  Helps to discover and install agent skills when they ask questions like "how do I do X", "find a skill for X", "is there a skill that can...", or express interest in extending capabilities. This skill should be used when the user is looking for functionality that might exist as an installable skill.
  Use this skill to discover, install, update, and manage reusable agent skills from the open agent skills ecosystem.
license: MIT
---

# npx-skills

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

The Skills CLI (`npx skills`) is the package manager for the open agent skills ecosystem. Skills are modular packages that extend agent capabilities with specialized knowledge, workflows, and tools.
This skill helps you discover and install skills from the open agent skills ecosystem.

## WHEN TO USE

- **Skill Discovery & Search**: Searching the skills ecosystem via `npx skills find`.
- **Skill Installation**: Installing open agent skills from repositories (e.g., `vercel-labs/agent-skills`) for various autonomous agents.
- **Skill Updates**: Updating previously installed skills via `npx skills update`.
- **Skill Scaffolding**: Initializing a new agent skill boilerplate via `npx skills init`.
- Asks "how do I do X" where X might be a common task with an existing skill
- Says "find a skill for X" or "is there a skill for X"
- Asks "can you do X" where X is a specialized capability
- Expresses interest in extending agent capabilities
- Wants to search for tools, templates, or workflows
- Mentions they wish they had help with a specific domain (design, testing, deployment, etc.)

## WHEN NOT TO USE

- **Content Creation**: Do not use this skill to write the internal markdown content of `SKILL.md` files (use `agent-skill-md-writer` or `agentskills` instead).

## Core Process

### Install Skills

1. **Diverse Source Formats**: Add skills from GitHub, GitLab, Bitbucket, or local paths.
   ```bash
   # GitHub shorthand
   npx skills add vercel-labs/agent-skills
   # Full GitHub URL
   npx skills add https://github.com/vercel-labs/agent-skills
   # Direct path to a skill in a repo
   npx skills add https://github.com/vercel-labs/agent-skills/tree/main/skills/web-design-guidelines
   # GitLab URL
   npx skills add https://gitlab.com/org/repo
   # Local path
   npx skills add ./my-local-skills
   ```
2. **Target Specific Agents**: Use `-a` or `--agent` to install to specific agents (e.g., `claude-code`, `opencode`, `cursor`, `github-copilot`).
   ```bash
   npx skills add vercel-labs/agent-skills -a claude-code -a opencode
   ```
3. **Target Specific Skills**: Use `-s` or `--skill` to limit which skills to install from a repository.
   ```bash
   npx skills add vercel-labs/agent-skills --skill frontend-design
   ```
4. **Global Installation**: Use `-g` or `--global` to install the skill globally across all projects for the user.
   ```bash
   npx skills add vercel-labs/agent-skills -g
   ```
5. **Force Copying**: Use `--copy` to copy files instead of symlinking (default).
   ```bash
   npx skills add vercel-labs/agent-skills --copy
   ```

### Manage Skills

1. **List Installed Skills**:
   ```bash
   # List all installed skills (project and global)
   npx skills list
   # List only global skills
   npx skills ls -g
   # Filter by specific agents
   npx skills ls -a claude-code -a cursor
   ```
2. **Update Skills**: Update all installed skills or specific ones.
   ```bash
   # Update all skills (interactive scope prompt)
   npx skills update
   # Update specific skill(s)
   npx skills update frontend-design web-design-guidelines
   # Update only global or project skills
   npx skills update -g
   npx skills update -p
   # Non-interactive update
   npx skills update -y
   ```
3. **Remove Skills**:
   ```bash
   # Remove interactively
   npx skills remove
   # Remove specific skill(s)
   npx skills remove web-design-guidelines
   # Remove from global scope
   npx skills remove --global web-design-guidelines
   # Remove from specific agents only
   npx skills remove --agent claude-code my-skill
   # Remove all installed skills without confirmation
   npx skills remove --all
   ```
4. **Search Skills**:
   ```bash
   # Interactive fzf-style search
   npx skills find
   # Search by keyword
   npx skills find typescript
   ```

### Scaffold Skills

1. **Initialize New Skill**: Create a boilerplate `SKILL.md` in the current directory or a new subdirectory.
   ```bash
   npx skills init
   npx skills init <skill-name>
   ```

## Examples

**Key commands:**

- `npx skills find [query]` - Search for skills interactively or by keyword
- `npx skills add <package>` - Install a skill from GitHub or other sources
- `npx skills check` - Check for skill updates
- `npx skills update` - Update all installed skills

```bash
# List skills in a repository without installing
npx skills add vercel-labs/agent-skills --list

# Install specific skills from a repository
npx skills add vercel-labs/agent-skills --skill frontend-design --skill skill-creator

# Install a skill with spaces in the name (must be quoted)
npx skills add owner/repo --skill "Convex Best Practices"

# Install to specific agents
npx skills add vercel-labs/agent-skills -a claude-code -a opencode

# Non-interactive installation (CI/CD friendly)
npx skills add vercel-labs/agent-skills --skill frontend-design -g -a claude-code -y

# Install all skills from a repo to all agents
npx skills add vercel-labs/agent-skills --all

# Update only global skills non-interactively
npx skills update -g -y

# Remove all installed skills from a specific agent
npx skills remove --skill '*' -a cursor

# Remove a specific skill from all agents (global and project)
npx skills remove my-skill --agent '*' --yes

# Remove multiple skills at once
npx skills remove frontend-design web-design-guidelines

# Use 'rm' alias to remove a skill
npx skills rm my-skill
```

## Environment Variables

| Variable | Description |
| -------- | ----------- |
| `INSTALL_INTERNAL_SKILLS` | Set to `1` or `true` to show and install skills marked as `internal: true`. |
| `DISABLE_TELEMETRY` | Set to `1` to disable anonymous usage telemetry. |

Example:
```bash
INSTALL_INTERNAL_SKILLS=1 npx skills add vercel-labs/agent-skills --list
```

## Core Principles

- **Automatic Discovery**: The CLI detects installed agents automatically; manually specifying `-a` is only needed to override this.
- **Symlinking Strategy**: Interactive installations use symlinks by default (creating a canonical copy linked from agent directories). Use `--copy` to force copying.
- **Scope Awareness**: Project scope is default. It commits skills within `.agents/skills/` (or agent-specific paths). Global scope (`-g`) applies across all projects.
- **Non-Interactive Execution**: When executing via an autonomous agent, use the `-y` or `--yes` flag to bypass all confirmation prompts.

## How to Find Skills

### Step 1: Understand What Skill is Needed

When a user or agent asks for help with something, identify:

1. The domain (e.g., React, testing, design, deployment)
2. The specific task (e.g., writing tests, creating animations, reviewing PRs)
3. Whether this is a common enough task that a skill likely exists

### Step 2: Check the Leaderboard First

Before running a CLI search, check the [skills.sh leaderboard](https://skills.sh/) to see if a well-known skill already exists for the domain. The leaderboard ranks skills by total installs, surfacing the most popular and battle-tested options.

For example, top skills for web development include:
- `vercel-labs/agent-skills` — React, Next.js, web design (widely used across the ecosystem)
- `anthropics/skills` — Frontend design, document processing (popular on the leaderboard)

### Step 3: Search for Skills

If the leaderboard doesn't cover the user's need, run the find command:

```bash
npx skills find [query]
```

For example:

- User asks "how do I make my React app faster?" → `npx skills find react performance`
- User asks "can you help me with PR reviews?" → `npx skills find pr review`
- User asks "I need to create a changelog" → `npx skills find changelog`

### Step 4: Verify Quality Before Recommending

**Do not recommend a skill based solely on search results.** Always verify:

1. **Install count** — Prefer skills with 1K+ installs. Be cautious with anything under 100.
2. **Source reputation** — Official sources (`vercel-labs`, `anthropics`, `microsoft`) are more trustworthy than unknown authors.
3. **GitHub stars** — Check the source repository. A skill from a repo with <100 stars should be treated with skepticism.

### Step 5: Present Options to the User

When you find relevant skills, present them to the user with:

1. The skill name and what it does
2. The install count and source
3. The install command they can run
4. A link to learn more at skills.sh

Example response:

```
I found a skill that might help! The "react-best-practices" skill provides
React and Next.js performance optimization guidelines from Vercel Engineering.
(install count and source)

To install it:
npx skills add vercel-labs/agent-skills@react-best-practices

Learn more: https://skills.sh/vercel-labs/agent-skills/react-best-practices
```

### Step 6: Offer to Install

If the user wants to proceed, you can install the skill for them:

```bash
npx skills add <owner/repo@skill> -g -y
```

The `-g` flag installs globally (user-level) and `-y` skips confirmation prompts.

## Common Skill Categories

When searching, consider these common categories:

| Category        | Example Queries                          |
| --------------- | ---------------------------------------- |
| Web Development | react, nextjs, typescript, css, tailwind |
| Testing         | testing, jest, playwright, e2e           |
| DevOps          | deploy, docker, kubernetes, ci-cd        |
| Documentation   | docs, readme, changelog, api-docs        |
| Code Quality    | review, lint, refactor, best-practices   |
| Design          | ui, ux, design-system, accessibility     |
| Productivity    | workflow, automation, git                |

## Tips for Effective Searches

1. **Use specific keywords**: "react testing" is better than just "testing"
2. **Try alternative terms**: If "deploy" doesn't work, try "deployment" or "ci-cd"
3. **Check popular sources**: Many skills come from `vercel-labs/agent-skills` or `ComposioHQ/awesome-claude-skills`

## When No Skills Are Found

If no relevant skills exist:

1. Acknowledge that no existing skill was found
2. Offer to help with the task directly using your general capabilities
3. Suggest the user could create their own skill with `npx skills init`

Example:

```
I searched for skills related to "xyz" but didn't find any matches.
I can still help you with this task directly! Would you like me to proceed?

If this is something you do often, you could create your own skill:
npx skills init my-xyz-skill
```

## Limitations

- Connecting to remote repositories or the `skills.sh` registry requires an active internet connection.
- Global installation might require correct filesystem permissions for the user's home directory.

## Common Pitfalls

- **Hangs on Interactive Prompts**: Forgetting to use the `-y` flag in automated agent workflows.
  *Prevention*: Always append `-y` or `--yes` for CI/CD or agent-driven non-interactive execution.
- **Unquoted Spaces or Wildcards**: The shell prematurely expanding `*` or mishandling spaces in skill names.
  *Prevention*: Always quote names with spaces (e.g., `"Convex Best Practices"`) and asterisks (e.g., `--skill '*'`).

## Related Skills

- **agent-skill-md-writer**:
  You MUST load this skill when creating or updating `SKILL.md` files.
- **agentskills**:
  You MUST load this skill to understand the technical structure of an agent skill.

## References

- [The Open Agent Skills Ecosystem](https://www.skills.sh/)
- [Official skills from the companies and organizations](https://www.skills.sh/official)
- [CLI Reference](https://www.skills.sh/docs/cli)
- <https://github.com/vercel-labs/skills>
