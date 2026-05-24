# Cogni AI Agentic Ops Plugin

[![License][license-image]][license-link]

Autonomous operator plugin for managing, maintaining, and refining agentic systems, agent
configurations, skills, and agentic workflows.

| | |
| --- | --- |
| **Description** | Autonomous operator for agentic systems development and maintenance. |

## Slash Commands

| Command | Description |
| --- | --- |
| `/cogni-ai-agentic-ops:agent-md` | Agent metadata formatting and syntax |
| `/cogni-ai-agentic-ops:agent-md-writer` | Best practices for creating agent personas |
| `/cogni-ai-agentic-ops:agent-skill-md-writer` | Guidelines for creating agent skills |
| `/cogni-ai-agentic-ops:agents-md-writer` | Guidelines for creating AGENTS.md |
| `/cogni-ai-agentic-ops:agentskills` | Knowledge about the Agent Skills specification |
| `/cogni-ai-agentic-ops:ai-prompt-writer` | Guidelines for writing secure AI prompts |

And other related skills...

## Installation

### GitHub Copilot

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-agentic-collections:plugins/cogni-ai-agentic-ops
```

### Claude Code

```bash
claude plugin install cogni-ai-agentic-ops@cogni-ai-agentic-collections
```

## What's Included

### Agents

- **cogni-ai-agentic-ops** — Elite autonomous operator engineered to oversee, maintain, and refine
  agentic systems, skills, and workflows across environments.

### Skills

- **agent-log-analysis** — Procedures for analyzing agent session logs and telemetry.
- **agent-md** — Syntax and structure reference for custom agent persona files.
- **agent-md-writer** — Guidelines for writing high-performance agent personas.
- **agent-skill-md-writer** — Instructions for generating or refining agent skills (`SKILL.md`).
- **agents-md-writer** — Editor guidelines for maintaining `AGENTS.md` context files.
- **agentskills** — The Agent Skills open standard reference.
- **ai-prompt-writer** — Tools for designing secure and optimized AI prompts.
- **claude-llms** — Guides for Anthropic Claude LLMs.
- **copilot-cli** — Configuration and usage guides for Copilot CLI.
- **copilot-docs** — Copilot agent customization docs.
- **mcp-cli** — Specifications for MCP CLI usage.
- **opencode** — Guidelines for the OpenCode ecosystem.
- **squad-cli** — Automation workflows for the Squad CLI.
- **waza-cli** — Workflows for the Waza tool.
- **waza-docs** — References for the Microsoft/Waza docs.

## Usage

Once installed, invoke the agent via Copilot CLI:

```bash
copilot run --agent cogni-ai-agentic-ops "Refactor the SKILL.md file for..."
```

## License

MIT

<!-- Named links -->

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
