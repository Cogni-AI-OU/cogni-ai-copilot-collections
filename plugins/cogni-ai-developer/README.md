# Cogni AI Developer Plugin

[![License][license-image]][license-link]

Autonomous development agent plugin for GitHub Copilot. Specializes in building and shipping complete, usable
software that delivers user and business value.

| | |
| --- | --- |
| **Description** | Autonomous developer agent with development, tdd, npm-cli, VS Code docs, and bun skills |

## Slash Commands

| Command | Description |
| --- | --- |
| `/cogni-ai-developer:development` | Full-cycle software development workflow from requirements to deployment |
| `/cogni-ai-developer:tdd` | Commands and procedures for test engineering and the TDD lifecycle |
| `/cogni-ai-developer:critical-thinking` | Cognitive framework for deep analytical reasoning |
| `/cogni-ai-developer:npm-cli` | Reference and index of documentation pages for npm CLI commands |
| `/cogni-ai-developer:bun-llms` | Reference and APIs for retrieving Bun documentation programmatically for LLMs |
| `/cogni-ai-developer:code-visualstudio-llms` | Reference and APIs for retrieving VS Code documentation for LLMs |

## Installation

### GitHub Copilot

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-agentic-collections:plugins/cogni-ai-developer
```

### Claude Code

```bash
claude plugin install cogni-ai-developer@cogni-ai-agentic-collections
```

## What's Included

### Agents

- **cogni-ai-developer** — Autonomous developer assistant that architects, builds, and ships end-to-end solutions
  while adhering to high-quality development standards.

### Skills

- **development** — Full-cycle software development workflow: from requirements and system design through deployment,
  monitoring, and iteration.
- **tdd** — Commands, step-by-step procedures, and mechanical execution for test engineering, testability audits,
  and the TDD lifecycle.
- **critical-thinking** — Deep analytical reasoning framework for deconstructing assumptions, evaluating trade-offs,
  and solving complex problems.
- **npm-cli** — Reference and index of documentation pages for npm CLI commands and configurations.
- **bun-llms** — Reference and APIs for retrieving Bun documentation programmatically for LLMs.
- **code-visualstudio-llms** — Reference and APIs for retrieving Visual Studio Code documentation programmatically for LLMs.

## Usage

Once installed, invoke the agent via Copilot CLI:

```bash
copilot run --agent cogni-ai-developer "your development task"
```

## License

MIT

<!-- Named links -->

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
