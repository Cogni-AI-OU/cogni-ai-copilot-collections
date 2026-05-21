# Cogni AI GitHub Ops Plugin

[![License][license-image]][license-link]

Autonomous GitHub Operations agent plugin for GitHub Copilot. Specializes in GitHub workflows, pull requests, issues, actions, and agentic workflows.

| | |
|---|---|
| **Description** | Autonomous GitHub Operations agent with GitHub skills |
| **Contents** | 1 agent, 33 skills |
| **Slash Commands** | [`/cogni-ai-github-ops:gh`](../AGENTS.md) <br/> [`/cogni-ai-github-ops:github`](../AGENTS.md) |

## Installation

### Using Copilot CLI

```bash
copilot plugin install Cogni-AI-OU/cogni-ai-copilot-collections:plugins/cogni-ai-github-ops
```

## What's Included

### Agents

- **cogni-ai-github-ops** — Autonomous GitHub Operations assistant that handles repository management on GitHub, issues, pull requests, workflow runs, and agentic workflows safely and efficiently.

### Skills

- **gh** — GitHub CLI operations for issues, pull requests, workflow runs, reviews, and API.
- **github** — GitHub-specific features and collaborative practices.
- *(And 31 other specialized GitHub skills for actions, agentic workflows, API, codespaces, issues, models, PRs, runs, search, topics, and more.)*

## Usage

Once installed, invoke the agent via Copilot CLI:

```bash
copilot run --agent cogni-ai-github-ops "your github operations task"
```

## License

MIT

<!-- Named links -->

[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license