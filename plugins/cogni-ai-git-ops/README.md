# Cogni AI Git Ops Plugin

[![License][license-image]][license-link]

Autonomous Git Operations agent plugin for GitHub Copilot. Specializes in version control, complex git workflows, rebase operations, and repository management.

| | |
|---|---|
| **Description** | Autonomous Git Operations agent with git skills |
| **Contents** | 1 agent, 1 skill |
| **Slash Commands** | [`/cogni-ai-git-ops:git`](../AGENTS.md) |

## Installation

### Using Copilot CLI

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-agentic-collections:plugins/cogni-ai-git-ops
```

## What's Included

### Agents

- **cogni-ai-git-ops** — Autonomous Git Operations assistant that handles complex repository management tasks, merges, rebases, and history rewriting safely.

### Skills

- **git** — Guide for using git with non-interactive, safe operations. Includes advanced references to reflog, bisecting, merges, cherry-picking, rebase operations, and repository recovery.

## Usage

Once installed, invoke the agent via Copilot CLI:

```bash
copilot run --agent cogni-ai-git-ops "your git operations task"
```

## License

MIT

<!-- Named links -->

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
