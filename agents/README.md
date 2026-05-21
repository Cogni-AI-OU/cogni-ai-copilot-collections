# Cogni AI Agents

This directory is the **source of truth** for Cogni AI autonomous agent configurations.
Agent files are stored here so they are accessible directly when this repo is cloned
into `.github/agents`.

## Agent Catalog

| File | Audience | Purpose |
| ---- | -------- | ------- |
| [cogni-ai-architect.agent.md](cogni-ai-architect.agent.md) | Orchestrators | Primary Cogni AI Architect agent definition |
| [cogni-ai-context7-ops.agent.md](cogni-ai-context7-ops.agent.md) | All agents | Autonomous Context7 Ops for gathering and filtering documentation |
| [cogni-ai-devops.agent.md](cogni-ai-devops.agent.md) | DevOps/SREs | Elite autonomous DevOps and SRE agent |
| [cogni-ai-elite.agent.md](cogni-ai-elite.agent.md) | Orchestrators | Cogni AI Elite autonomous systems architect |
| [cogni-ai-fact-ops.agent.md](cogni-ai-fact-ops.agent.md) | Fact Ops | Autonomous fact operator for maintaining canonical fact files |
| [cogni-ai-manager.agent.md](cogni-ai-manager.agent.md) | Managers | Autonomous orchestration and coordination manager |
| [cogni-ai-keeper.agent.md](cogni-ai-keeper.agent.md) | Keepers | Canonical Fact Custody & Mindmap Stewardship Kernel |
| [cogni-ai-programmer](../plugins/cogni-ai-programmer/agents/cogni-ai-programmer.agent.md) | Python Devs | Autonomous programmer assistant specializing in Python |
| [cogni-ai-code-reviewer.agent.md](cogni-ai-code-reviewer.agent.md) | Reviewers | Elite autonomous code, PR analysis, and zero-defect enforcer |
| [cogni-ai-plan-reviewer.agent.md](cogni-ai-plan-reviewer.agent.md) | Reviewers | Elite autonomous architectural reviewer for plan validation |
| [cogni-ai-weaver.agent.md](cogni-ai-weaver.agent.md) | Weavers | Canonical Flow Custody & Diagram Stewardship Kernel |
| [cogni-ai-agent-auditor.agent.md](cogni-ai-agent-auditor.agent.md) | Auditors | Expert autonomous auditor for analyzing agent session logs |
| [cogni-ai-brain-ops.agent.md](cogni-ai-brain-ops.agent.md) | Planners | Autonomous brainstorming agent for gathering facts and planning |
| [cogni-ai-docs-editor.agent.md](cogni-ai-docs-editor.agent.md) | Docs | Autonomous documentation operator |
| [cogni-ai-github-ops.agent.md](cogni-ai-github-ops.agent.md) | GitHub | Autonomous GitHub Operator for PRs, issues, discussions |
| [cogni-ai-security-auditor.agent.md](cogni-ai-security-auditor.agent.md) | Security | Elite autonomous security auditor |
| [cogni-ai-tester.agent.md](cogni-ai-tester.agent.md) | Testers | Autonomous Tester for quality and verification |

See also:

- [AGENTS.md](../AGENTS.md) for agent execution protocols and architecture principles
- [AGENTS-RUNTIME.md](../AGENTS-RUNTIME.md) for runtime loading protocols and execution logic
- [AGENTS.mmd](../AGENTS.mmd) for initialization sequence diagrams
- [CONSTRAINTS.mzn](../CONSTRAINTS.mzn) for formal constraint declarations
- [docs/FLOWS.mmd](../docs/FLOWS.mmd) for operational protocols
- [docs/FACTS.mmd](../docs/FACTS.mmd) for canonical fact store

## Available Agents

### [Cogni AI Architect](cogni-ai-architect.agent.md)

Enhanced agent with critical thinking, robust problem-solving, and context-aware resource management. Features:

- Automatic file size checking before viewing
- Smart filtering for long outputs
- Command installation fallback logic
- Self-improvement capabilities
- Never-give-up problem-solving approach

### [Cogni AI Context7 Ops](cogni-ai-context7-ops.agent.md)

Autonomous Context7 Ops responsible for gathering and filtering documentation from Context7 into relevant context.

### [Cogni AI DevOps](cogni-ai-devops.agent.md)

Elite autonomous DevOps and Site Reliability Engineering agent. Focuses on task automation,
CI/CD pipeline precision, infrastructure-as-code (IaC), and resolving deployment challenges.

### [Cogni AI Elite](cogni-ai-elite.agent.md)

Elite autonomous systems architect engineered for structural perfection and recursive problem decomposition.

### [Cogni AI Fact Ops](cogni-ai-fact-ops.agent.md)

Autonomous fact operator responsible for maintaining canonical fact files and information consistency.

### [Cogni AI Manager](cogni-ai-manager.agent.md)

Autonomous orchestration and coordination manager responsible for routing work to specialized agents and ensuring end-to-end completion.

### [Cogni AI Keeper](cogni-ai-keeper.agent.md)

Canonical fact-custody kernel and mindmap steward.
Deep module for fact management via VCS-aligned plain-text mindmaps.

### [Cogni AI Programmer](../plugins/cogni-ai-programmer/agents/cogni-ai-programmer.agent.md)

Autonomous programmer assistant specializing in Python. Writes, refactors, and verifies Python 3 code with type safety and idiomatic patterns.

### [Cogni AI Code Reviewer](cogni-ai-code-reviewer.agent.md)

Elite autonomous agent for code review, PR analysis, and enforcing zero-defect quality and security validation.

### [Cogni AI Plan Reviewer](cogni-ai-plan-reviewer.agent.md)

Elite autonomous architectural reviewer for plan validation and ensuring strategic alignment.

### [Cogni AI Weaver](cogni-ai-weaver.agent.md)

Canonical flow-custody kernel and diagram steward. Specializes in flowchart memory:
decision chains, causal flows, dependencies, state transitions, timelines.
