# Cogni AI Collections for Copilot

[![PR Reviews][pr-reviews-image]][pr-reviews-link]
[![License][license-image]][license-link]

## Installation

### Agents

```
# Clone agents.
git clone --depth=1 https://github.com/Cogni-AI-OU/cogni-ai-agents ~/.copilot/agents
```

### Instructions

```
# Clone instructions.
git clone --depth=1 https://github.com/Cogni-AI-OU/cogni-ai-agent-instructions ~/.copilot/instructions
```

### Plugins

To install plugins (which includes agents and corresponding skills):

```console
# Install plugins from this collection as a marketplace
copilot plugin marketplace add Cogni-AI-OU/cogni-ai-copilot-collections
# Then install individual plugins by name (e.g. cogni-ai-architect):
copilot plugin install cogni-ai-architect@cogni-ai-copilot-collections
```

### Skills

How to install skill (non-interactive):

```console
gh skills install Cogni-AI-OU/cogni-ai-agent-skills --scope user <skill-name>
```

How to install all or selected skills (interactive with override):

```console
gh skills install Cogni-AI-OU/cogni-ai-copilot-collections --agent github-copilot --force --scope user
```
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

[pr-reviews-image]: https://img.shields.io/github/issues-pr/Cogni-AI-OU/cogni-ai-copilot-collections?label=PR+Reviews&logo=github
[pr-reviews-link]: https://github.com/Cogni-AI-OU/cogni-ai-copilot-collections/pulls
[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
[customize-env]: https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/customize-the-agent-environment
[firewall-config]: https://gh.io/copilot/firewall-config
