# Cogni AI Programmer Plugin

[![License][license-image]][license-link]

Autonomous programmer agent plugin for GitHub Copilot. Specializes in solving technical problems with code — designing algorithms, data structures, and reliable solutions.

| | |
|---|---|
| **Description** | Autonomous programmer agent with programming and python skills |
| **Contents** | 1 agent, 3 skills |
| **Slash Commands** | [`/cogni-ai-programmer:programming`](../AGENTS.md) <br/> [`/cogni-ai-programmer:python`](../AGENTS.md) |

## Installation

### Using Copilot CLI

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-agentic-collections:plugins/cogni-ai-programmer
```

## What's Included

### Agents

- **cogni-ai-programmer** — Autonomous programmer assistant specializing in designing correct, efficient, and maintainable solutions across multiple languages.

### Skills

- **programming** — Expert workflow for solving technical problems: algorithm design, data structure selection, edge case handling, and code craftsmanship.
- **python** — Expert Python language skill for writing, refactoring, and testing idiomatic Python 3 code.
- **threejs-llms** — Expert guide for generating modern Three.js code using WebGL, WebGPU, and TSL.

## Usage

Once installed, invoke the agent via Copilot CLI:

```bash
copilot run --agent cogni-ai-programmer "your programming task"
```

## License

MIT

<!-- Named links -->

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
