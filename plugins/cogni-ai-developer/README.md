# Cogni AI Developer Plugin

[![License][license-image]][license-link]

Autonomous development agent plugin for GitHub Copilot. Specializes in building robust, end-to-end software solutions.

| | |
|---|---|
| **Description** | Autonomous developer agent with development and tdd skills |
| **Contents** | 1 agent, 2 skills |
| **Slash Commands** | [`/cogni-ai-developer:development`](../AGENTS.md) <br/> [`/cogni-ai-developer:tdd`](../AGENTS.md) |

## Installation

### Using Copilot CLI

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-copilot-collections:plugins/cogni-ai-developer
```

## What's Included

### Agents

- **cogni-ai-developer** — Autonomous developer assistant that architects, builds, and ships end-to-end solutions while adhering to high-quality development standards.

### Skills

- **development** — Workflow and guidelines for full-cycle software development, feature implementation, and architecture-compliant execution.
- **tdd** — Commands, step-by-step procedures, and mechanical execution for test engineering, testability audits, and the TDD lifecycle.

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
