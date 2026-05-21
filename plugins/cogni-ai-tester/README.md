# Cogni AI Tester Plugin

[![License][license-image]][license-link]

Autonomous test engineering agent plugin for GitHub Copilot. Specializes in proving software correctness, preventing regressions, and designing refactor-resilient behavioral tests.

| | |
|---|---|
| **Description** | Autonomous tester agent with testing skill |
| **Contents** | 1 agent, 1 skill |
| **Slash Commands** | [`/cogni-ai-tester:testing`](../AGENTS.md) |

## Installation

### Using Copilot CLI

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-copilot-collections:plugins/cogni-ai-tester
```

## What's Included

### Agents

- **cogni-ai-tester** — Elite autonomous test engineering kernel focused on proving software correctness, preventing regressions, and designing refactor-resilient behavioral tests.

### Skills

- **testing** — Elite autonomous test engineering and reliability kernel.

## Usage

Once installed, invoke the agent via Copilot CLI:

```bash
copilot run --agent cogni-ai-tester "your testing task"
```

## License

MIT

<!-- Named links -->

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
