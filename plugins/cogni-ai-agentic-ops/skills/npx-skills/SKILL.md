---
name: npx-skills
description: >-
  Install, find, update, and manage agent skills using the npx skills CLI tool.
  You MUST load this skill when using the npx skills command or when discovering installable skills.
license: MIT
---

# npx-skills

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

The Skills CLI (`npx skills`) is the package manager for the open agent skills ecosystem. Skills are modular packages that extend agent capabilities with specialized knowledge, workflows, and tools.

## WHEN TO USE

- **Skill Discovery & Search**: Searching the skills ecosystem via `npx skills find`.
- **Skill Installation**: Installing open agent skills from repositories (e.g., `vercel-labs/agent-skills`).
- **Skill Updates**: Updating previously installed skills via `npx skills update`.
- **Skill Scaffolding**: Initializing a new agent skill boilerplate via `npx skills init`.
- Incoming request maps to a known capability domain (testing, design, deploy, etc.).
- Task is a common pattern that likely has an existing skill package.
- Capability extension is needed (e.g., adding PR review workflows, performance analysis).

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

### Step 1: Determine the Search Target

Before searching, determine:

1. **Target audience**: **user** (knowledge/guidance) or **agent** (execution workflows)
2. **Domain**: React, testing, design, deployment, etc.
3. **Specific task**: writing tests, creating animations, reviewing PRs, etc.
4. **Likelihood**: whether this is a common enough task that a skill likely exists

### Step 2: Check the Leaderboard First

Before running a CLI search, check the [skills.sh leaderboard](https://skills.sh/) to see if a well-known skill already exists for the domain. The leaderboard ranks skills by total installs, surfacing the most popular and battle-tested options.

For example (illustrative — actual leaderboard content changes over time):
- `vercel-labs/agent-skills` — React, Next.js, web design (widely used across the ecosystem)
- Official sources like `vercel-labs`, `microsoft`, or prominent community publishers

### Step 3: Search for Skills

If the leaderboard doesn't cover the need, run the find command:

```bash
npx skills find [query]
```

Search tips:
- **Use specific keywords**: "react testing" is better than just "testing"
- **Try alternative terms**: If "deploy" doesn't work, try "deployment" or "ci-cd"
- **Check popular sources**: Many skills come from `vercel-labs/agent-skills` or `ComposioHQ/awesome-claude-skills`

For example:

- Input: "React app performance optimization" → Command: `npx skills find react performance`
- Input: "PR review workflow" → Command: `npx skills find pr review`
- Input: "changelog generation" → Command: `npx skills find changelog`

### Step 4: Verify Quality Before Recommending

**Do not recommend a skill based solely on search results.** Always verify:

1. **Install count** — Prefer skills with 1K+ installs. Be cautious with anything under 100.
2. **Source reputation** — Official sources (`vercel-labs`, `anthropics`, `microsoft`) are more trustworthy than unknown authors.
3. **GitHub stars** — Check the source repository. A skill from a repo with <100 stars should be treated with skepticism.

### Step 5: Present Candidate Skills

Present each candidate skill with its metadata and install command:

1. Skill name and description
2. Install count and source (avoid hard-coded numbers — use relative terms like "high install count")
3. Install command
4. skills.sh reference link

Output template (skill names are illustrative):

```text
Skill: <skill-name>
Description: <description>
Source: <owner>/<repo>
Installs: <high/moderate/low>
Install: npx skills add <owner>/<repo>@<skill-name>
Learn more: https://skills.sh/<owner>/<repo>/<skill-name>
```

### Step 6: Install the Skill

To install a selected skill:

```bash
npx skills add <owner/repo@skill> -g -y
```

`-g` installs globally (user-level); `-y` skips confirmation prompts.

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

## When No Skills Are Found

If no relevant skills exist:

1. Report that no match was found
2. Proceed with direct task execution using available capabilities
3. Suggest creating a new skill: `npx skills init <skill-name>`

Output template:

```text
Query: <query>
Result: no matching skills found
Next step: execute task directly or create a skill with:
  npx skills init <skill-name>
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
