# Cogni AI Coder Plugin

[![License][license-image]][license-link]

Autonomous coding agent plugin for GitHub Copilot. Specializes in writing, refactoring, and testing code while adhering strictly to project conventions.

## Installation

### Using Copilot CLI

```bash
copilot plugin install https://github.com/Cogni-AI-OU/cogni-ai-copilot-collections/tree/main/plugins/cogni-ai-coder
```

### Manual Installation

Add the plugin directory to your Copilot configuration or clone it into your `.github/plugins` directory:

```bash
git clone --depth=1 https://github.com/Cogni-AI-OU/cogni-ai-copilot-collections .github/plugins/cogni-ai-coder
```

## What's Included

### Agents

- **cogni-ai-coder** — Autonomous coding assistant that generates, refactors, and verifies code. Applies Design-by-Contract, Single-Variable Delta Rule, and Exhaustive Validation before completing any task.

### Skills

- **critical-thinking** — Deep analytical reasoning framework for deconstructing assumptions, applying Socratic questioning, and performing adversarial red-teaming to solve complex problems.

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
