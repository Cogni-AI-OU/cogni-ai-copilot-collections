# Cogni AI Copilot Collections

[![PR Reviews][pr-reviews-image]][pr-reviews-link]
[![License][license-image]][license-link]

Repository for applying Cogni-AI-OU operations standards, reusable workflows,
prompt catalogs, coding instructions, and agent guidance to a project repository.
This repository mirrors the structure and conventions of the
[Cogni-AI-OU/.github](https://github.com/Cogni-AI-OU/.github) organization repository.

## What This Repository Provides

This repository includes the standard operations infrastructure for
Cogni-AI-OU projects:

### Key Features

- **GitHub Actions Workflows**: CI/CD and automation (OpenCode, pre-commit, etc.)
- **AI Agent Configurations**: [agents/](agents/) directory with `*.agent.md` definitions and skills for automated development
- **Pre-commit Hooks**: Linting and validation tooling

### How to Use

1. Explore the available agents, skills, and plugins
2. Install the desired tools using GitHub CLI (`gh skill install ...`)
3. Access installed agents through the Copilot chat or CLI

## Getting Started

1. Install the local validation tooling:

   ```bash
   pip install pre-commit
   pip install -r .devcontainer/requirements.txt
   ```

2. Run the repository checks:

   ```bash
   pre-commit run -a
   ```

3. Review the core guidance:
   - This README for repository scope and the local workflow
   - [.tours/getting-started.tour](.tours/getting-started.tour) for a guided walkthrough
   - [AGENTS.md](AGENTS.md) for repository-specific agent guidance
   - [AGENTS-RUNTIME.md](AGENTS-RUNTIME.md) for runtime-specific loading protocols

## Development

### Setup

```bash
# Install pre-commit hooks
pip install pre-commit
pre-commit install

# Install Python dependencies (for devcontainer)
pip install -r .devcontainer/requirements.txt
```

### Testing and Validation

```bash
# Run all pre-commit checks
pre-commit run -a

# Run specific checks
pre-commit run markdownlint -a
pre-commit run yamllint -a
pre-commit run black -a
pre-commit run flake8 -a
```

## Project Layout

- `agents/`: Cogni AI autonomous agent configurations (see [agents/README.md](agents/README.md) for catalog)
- `skills/`: Cogni AI autonomous agent skills (see [skills/README.md](skills/README.md) for catalog)
- `plugins/`: Cogni AI plugin bundles (see [plugins/README.md](plugins/README.md) for catalog)
- `AGENTS.md`: agents catalog and repository-specific guidance
- `AGENTS-RUNTIME.md`: core loading protocols and execution logic for the GitHub Runtime
- `AGENTS.mmd`: root canonical diagram, flows, and booting sequence visualizations (Initialization primary source)
- `CONSTRAINTS.mzn`: formal constraint declarations (budgets, loop arrest, and guardrails)
- `docs/FACTS.mmd`: root canonical fact store and project mindmap
- `docs/FLOWS.mmd`: root canonical timelines, flows, and dependency graphs
- `.github/`: default templates, workflows, and GitHub-specific configurations
- `.tours/`: guided walkthroughs for repository onboarding
- `README.md`: repository overview and local development workflow

## Available Plugins

Plugins are portable bundles that package agents, skills, and configuration together
for easy installation. See [plugins/README.md](plugins/README.md) for the available plugins.

## AI Agents

This repository is the **source of truth** for Cogni AI agent configurations.
Agent files live in the `agents/` directory and are distributed to consumer
repositories through the documented installation flow (for example,
`gh skills install ...`). After installation, consumers receive the agent files
under `.github/agents/agents/` and the accompanying guidance at
`.github/agents/AGENTS.md`. Plugins are bundled in [`plugins/`](plugins/) as
portable agent distributions with manifests.

See [agents/README.md](agents/README.md) for the full agent catalog, descriptions, and
[AGENTS.md](AGENTS.md) for agent execution protocols and architecture principles.

### Installation

To set up the required agents, instructions, and skills in your repository:

```bash
# Install agent definitions
gh skills install Cogni-AI-OU/cogni-ai-agents --scope user <agent-name>
# Install custom instructions
gh skills install Cogni-AI-OU/cogni-ai-agent-instructions --scope user <instruction-name>
# Install agent skills
gh skills install Cogni-AI-OU/cogni-ai-agent-skills --scope user <skill-name>

# Install plugins from this collection as a marketplace
copilot plugin marketplace add Cogni-AI-OU/cogni-ai-copilot-collections
# Then install individual plugins by name (e.g. cogni-ai-architect):
copilot plugin install cogni-ai-architect@cogni-ai-copilot-collections
```

## How to Use Custom Agents

### Adding Custom Agents

- Download the desired agent configuration file (`*.agent.md`) and add it to your repository.
- Use the Copilot CLI for local testing: [Copilot CLI](https://gh.io/customagents/cli).
- Merge the agent configuration file into the default branch of your repository.
- Access installed agents through the VS Code Chat interface, Copilot CLI,
  or assign them in Copilot Coding Agent (CCA).

For more details, see:

- [About custom agents](https://gh.io/customagents)
- [Custom Agents Documentation](https://gh.io/customagents/config).
- [Create custom agents](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents)
- [Copilot CLI](https://gh.io/customagents/cli)
- [GitHub Awesome Copilot repository](https://github.com/github/awesome-copilot)
- [Supported Models](https://docs.github.com/en/copilot/reference/ai-models/supported-models)

## Customizing development environment

See: [Customizing the development environment for GitHub Copilot coding agent][customize-env].

## Firewall

See: [Customizing or disabling the firewall for GitHub Copilot coding agent][firewall-config].

### Firewall allowlist

See [.github/FIREWALL.md](.github/FIREWALL.md) for recommended hosts to allow and the official guidance link.

### MCP Server Setup

Some agents require MCP servers to function. The Claude Code Action provides
built-in MCP servers for GitHub operations (`github_comment` and
`github_inline_comment`).

#### Custom MCP Servers

You can add custom MCP servers for additional integrations.

**Important notes:**

- File-based config cannot use GitHub Actions secrets (`${{ secrets.* }}`). Use
  inline config for secrets.
- HTTP-based MCP servers (using `"type": "http"`) may work with inline config
  but can fail with file-based config due to how the Claude Code process loads
  external files.
- **Current configuration**: This repository uses inline `--mcp-config` for the
  GitHub Copilot MCP endpoint (see `.github/workflows/claude-review.yml`) as it's
  an HTTP-based server. File-based config is available for custom command-based
  MCP servers if needed.

Follow the instructions in the agent's documentation to configure the necessary MCP servers.

## Security Considerations

### Claude Code Agent Git Access

When using Claude Code (triggered via `@claude` in comments), the agent has broad
git access via `Bash(git:*)` to enable autonomous code changes. This requires
proper repository safeguards.

**Access controls in place:**

- Only trusted users (OWNER, MEMBER, COLLABORATOR, CONTRIBUTOR) can trigger Claude
- PR/issue authors can only trigger Claude on their own content
- External contributors are explicitly blocked

**Required repository protections:**

Repository administrators must configure:

1. **Branch protection rules** on main/protected branches requiring PR reviews
   and status checks
2. **GitHub audit log monitoring** for `github-actions[bot]` commit activity
3. **CODEOWNERS** files for sensitive directories requiring specific approvals

**Best practices:**

- Review Claude's commits before merging PRs
- Use draft PRs for Claude's work requiring explicit promotion
- Monitor workflow logs for unexpected behavior
- Rotate API keys periodically

## Troubleshooting

## GitHub Actions

For documentation on GitHub Actions workflows, problem matchers, and CI/CD
configuration, see [.github/workflows/README.md](.github/workflows/README.md).

## Organization Profile

For information about Cogni AI OÜ, our mission, and how to collaborate, see our
[organization profile](https://github.com/Cogni-AI-OU/.github/blob/main/profile/README.md).

## License

This repository is licensed under MIT. See [LICENSE](LICENSE) for the full text.

<!-- Named links -->

[pr-reviews-image]: https://img.shields.io/github/issues-pr/Cogni-AI-OU/cogni-ai-copilot-collections?label=PR+Reviews&logo=github
[pr-reviews-link]: https://github.com/Cogni-AI-OU/cogni-ai-copilot-collections/pulls
[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
[customize-env]: https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/customize-the-agent-environment
[firewall-config]: https://gh.io/copilot/firewall-config
