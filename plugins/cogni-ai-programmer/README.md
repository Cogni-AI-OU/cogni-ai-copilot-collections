# Cogni AI Programmer Plugin

[![License][license-image]][license-link]

Autonomous programmer agent plugin for GitHub Copilot. Specializes in solving technical problems with code —
designing algorithms, data structures, and reliable solutions.

| | |
| --- | --- |
| **Description** | Autonomous programmer agent with programming and python skills |
| **Contents** | 1 agent, 6 skills |

## Slash Commands

| Command | Description |
| --- | --- |
| `/cogni-ai-programmer:programming` | Expert workflow for solving technical problems with code |
| `/cogni-ai-programmer:python` | Expert Python language skill for writing and testing Python 3 code |
| `/cogni-ai-programmer:threejs-llms` | Expert guide for generating modern Three.js code |
| `/cogni-ai-programmer:react-llms` | Expert guide for generating React code |
| `/cogni-ai-programmer:nextjs-llms` | Expert guide for generating Next.js code |
| `/cogni-ai-programmer:reactnative-llms` | Expert guide for generating React Native code |

## Installation

### GitHub Copilot

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-agentic-collections:plugins/cogni-ai-programmer
```

### Claude Code

```bash
claude plugin install cogni-ai-programmer@cogni-ai-agentic-collections
```

## What's Included

### Agents

- **cogni-ai-programmer** — Autonomous programmer assistant specializing in designing correct, efficient, and
  maintainable solutions across multiple languages.

### Skills

- **programming** — Expert workflow for solving technical problems: algorithm design, data structure selection, edge
  case handling, and code craftsmanship.
- **python** — Expert Python language skill for writing, refactoring, and testing idiomatic Python 3 code.
- **threejs-llms** — Expert guide for generating modern Three.js code using WebGL, WebGPU, and TSL.
- **react-llms** — Expert guide for generating React code with modern patterns.
- **nextjs-llms** — Expert guide for generating Next.js applications.
- **reactnative-llms** — Expert guide for generating React Native mobile applications.

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
