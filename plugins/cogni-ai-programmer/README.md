# Cogni AI Programmer Plugin

[![License][license-image]][license-link]

Autonomous programmer agent plugin for GitHub Copilot. Specializes in writing, refactoring, and testing Python code while adhering strictly to project conventions.

| | |
|---|---|
| **Description** | Autonomous programmer agent with Python skill |
| **Contents** | 1 agent, 1 skill |
| **Slash Commands** | [`/cogni-ai-programmer:python`](../AGENTS.md) |

## Installation

### Using Copilot CLI

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-copilot-collections:plugins/cogni-ai-programmer
```

## What's Included

### Agents

- **cogni-ai-programmer** — Autonomous programmer assistant specializing in Python. Writes, refactors, and verifies Python 3 code with type safety and idiomatic patterns.

### Skills

- **python** — Expert Python language skill for writing, refactoring, and testing idiomatic Python 3 code.

## Usage

Once installed, invoke the agent via Copilot CLI:

```bash
copilot run --agent cogni-ai-programmer "your python task"
```

## License

MIT

<!-- Named links -->

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
