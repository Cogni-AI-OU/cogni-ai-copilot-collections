# Cogni AI Coder Plugin

[![License][license-image]][license-link]

Autonomous coding agent plugin for GitHub Copilot. Specializes in implementing code from specifications with
precision and speed.

| | |
| --- | --- |
| **Description** | Autonomous coding agent with coding and critical-thinking skills |
| **Contents** | 1 agent, 2 skills |

## Slash Commands

| Command | Description |
| --- | --- |
| `/cogni-ai-coder:coding` | Workflow for implementing code from clear specifications with precision |
| `/cogni-ai-coder:critical-thinking` | Cognitive framework for deep analytical reasoning |

## Installation

### GitHub Copilot

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-agentic-collections:plugins/cogni-ai-coder
```

### Claude Code

```bash
claude plugin install cogni-ai-coder@cogni-ai-agentic-collections
```

## What's Included

### Agents

- **cogni-ai-coder** — Autonomous coding assistant that translates specifications into functional code with
  precision, speed, and strict convention adherence.

### Skills

- **coding** — Workflow for implementing code from clear specifications. Focuses on syntax accuracy, convention
  compliance, and rapid delivery.
- **critical-thinking** — Deep analytical reasoning framework for deconstructing assumptions, applying Socratic
  questioning, and performing adversarial red-teaming to solve complex problems.

## Usage

Once installed, invoke the agent via Copilot CLI:

```bash
copilot run --agent cogni-ai-coder "your coding task"
```

## License

MIT

<!-- Named links -->

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
