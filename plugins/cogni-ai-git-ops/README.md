# Cogni AI Git Ops Plugin

[![License][license-image]][license-link]

Autonomous Git Operations agent plugin for GitHub Copilot. Specializes in version control, complex git workflows,
rebase operations, and repository management.

| | |
| --- | --- |
| **Description** | Autonomous Git Operations agent with git skills |
| **Contents** | 1 agent, 2 skills |

## Slash Commands

| Command | Description |
| --- | --- |
| `/cogni-ai-git-ops:git` | Guide for using git with non-interactive, safe operations |
| `/cogni-ai-git-ops:git-docs` | Official Git documentation index |

## Installation

### GitHub Copilot

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-agentic-collections:plugins/cogni-ai-git-ops
```

### Claude Code

```bash
claude plugin install cogni-ai-git-ops@cogni-ai-agentic-collections
```

## What's Included

### Agents

- **cogni-ai-git-ops** — Autonomous Git Operations assistant that handles complex repository management tasks,
  merges, rebases, and history rewriting safely.

### Skills

- **git** — Guide for using git with non-interactive, safe operations. Includes advanced references to reflog,
  bisecting, merges, cherry-picking, rebase operations, and repository recovery.
- **git-docs** — Official Git documentation index. Use this skill when searching for specific Git commands,
  configuration options, how-to guides, and technical references.

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
