# Cogni AI Collections for Copilot

[![PR Reviews][pr-reviews-image]][pr-reviews-link]
[![License][license-image]][license-link]

## Installation

### Agents

```bash
# Clone agents.
git clone --depth=1 https://github.com/Cogni-AI-OU/cogni-ai-agents ~/.copilot/agents
```

### Instructions

```bash
# Clone instructions.
git clone --depth=1 https://github.com/Cogni-AI-OU/cogni-ai-agent-instructions ~/.copilot/instructions
```

### Plugins

To install plugins (which includes agents and corresponding skills):

#### GitHub Copilot

```console
# Install plugins from this collection as a marketplace
copilot plugin marketplace add Cogni-AI-OU/cogni-ai-agentic-collections
# Then install individual plugins by name (e.g. cogni-ai-architect):
copilot plugin install cogni-ai-architect@cogni-ai-agentic-collections
```

#### Claude Code

```console
# Install plugins from this collection as a marketplace
claude plugin marketplace add Cogni-AI-OU/cogni-ai-agentic-collections
# Then install individual plugins by name (e.g. cogni-ai-architect):
claude plugin install cogni-ai-architect@cogni-ai-agentic-collections
```

### Skills

How to install a skill (non-interactive):

```console
gh skills install Cogni-AI-OU/cogni-ai-agent-skills --scope user <skill-name>
```

How to install all or selected skills (interactive with override):

```console
gh skills install Cogni-AI-OU/cogni-ai-agentic-collections --agent github-copilot --force --scope user
```

For all skills (including from plugins), select `(all skills)`.

### Devcontainer

The repository includes `.devcontainer/devcontainer.json` for a reproducible local
setup with GitHub Actions tooling, Docker support, and common CLI dependencies.

## References

- [About custom agents](https://gh.io/customagents)
- [Custom Agents Documentation](https://gh.io/customagents/config).
- [Create custom agents](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents)
- [Copilot CLI](https://gh.io/customagents/cli)
- [GitHub Awesome Copilot repository](https://github.com/github/awesome-copilot)
- [Supported Models](https://docs.github.com/en/copilot/reference/ai-models/supported-models)

## License

This repository is licensed under MIT. See [LICENSE](LICENSE) for the full text.

<!-- Named links -->

[pr-reviews-image]: https://img.shields.io/github/issues-pr/Cogni-AI-OU/cogni-ai-agentic-collections?label=PR+Reviews&logo=github
[pr-reviews-link]: https://github.com/Cogni-AI-OU/cogni-ai-agentic-collections/pulls
[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
