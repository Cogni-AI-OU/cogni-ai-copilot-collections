# Cogni AI Agents

This directory is the **source of truth** for Cogni AI autonomous agent configurations.
Agent files are stored here so they are accessible directly when this repo is cloned
into `.github/agents`.

## Agent Catalog

| File | Audience | Purpose |
| ---- | -------- | ------- |
| [cogni-ai-architect.agent.md](../plugins/cogni-ai-architect/agents/cogni-ai-architect.agent.md) | Orchestrators | Primary Cogni AI Architect agent definition (moved to plugin) |
| [cogni-ai-context7-ops.agent.md](cogni-ai-context7-ops.agent.md) | All agents | Autonomous Context7 Ops for gathering and filtering documentation |
| [cogni-ai-devops.agent.md](cogni-ai-devops.agent.md) | DevOps/SREs | Elite autonomous DevOps and SRE agent |
| [cogni-ai-elite.agent.md](cogni-ai-elite.agent.md) | Orchestrators | Cogni AI Elite autonomous systems architect |
| [cogni-ai-fact-ops.agent.md](cogni-ai-fact-ops.agent.md) | Fact Ops | Autonomous fact operator for maintaining canonical fact files |
| [cogni-ai-manager.agent.md](cogni-ai-manager.agent.md) | Managers | Autonomous orchestration and coordination manager |
| [cogni-ai-keeper.agent.md](cogni-ai-keeper.agent.md) | Keepers | Canonical Fact Custody & Mindmap Stewardship Kernel |
| [cogni-ai-git-ops](../plugins/cogni-ai-git-ops/agents/cogni-ai-git-ops.agent.md) | Git Ops | Autonomous Git Operations agent for version control and complex workflows |
| [cogni-ai-coder](../plugins/cogni-ai-coder/agents/cogni-ai-coder.agent.md) | Coders | Autonomous coding agent for spec-driven implementation with precision and speed |
| [cogni-ai-programmer](../plugins/cogni-ai-programmer/agents/cogni-ai-programmer.agent.md) | Programmers | Autonomous programmer for algorithmic problem-solving and robust code craftsmanship |
| [cogni-ai-developer](../plugins/cogni-ai-developer/agents/cogni-ai-developer.agent.md) | Developers | Autonomous developer for full-cycle product delivery and end-to-end feature ownership |
| [cogni-ai-code-reviewer.agent.md](cogni-ai-code-reviewer.agent.md) | Reviewers | Elite autonomous code, PR analysis, and zero-defect enforcer |
| [cogni-ai-plan-reviewer.agent.md](cogni-ai-plan-reviewer.agent.md) | Reviewers | Elite autonomous architectural reviewer for plan validation |
| [cogni-ai-weaver.agent.md](cogni-ai-weaver.agent.md) | Weavers | Canonical Flow Custody & Diagram Stewardship Kernel |
| [cogni-ai-agent-auditor.agent.md](cogni-ai-agent-auditor.agent.md) | Auditors | Expert autonomous auditor for analyzing agent session logs |
| [cogni-ai-brain-ops.agent.md](cogni-ai-brain-ops.agent.md) | Planners | Autonomous brainstorming agent for gathering facts and planning |
| [cogni-ai-docs-editor.agent.md](cogni-ai-docs-editor.agent.md) | Docs | Autonomous documentation operator |
| [cogni-ai-github-ops](../plugins/cogni-ai-github-ops/agents/cogni-ai-github-ops.agent.md) | GitHub | Autonomous GitHub Operator for PRs, issues, discussions |
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

### [Cogni AI Architect](../plugins/cogni-ai-architect/agents/cogni-ai-architect.agent.md)

Elite autonomous engineering kernel and systems architect. Specializes in maximal-fidelity problem decomposition, backpropagation-style recursive self-refinement, and neurosymbolic verification. Includes the software-architecture skill for architectural design workflows.

> **Note**: This agent has been moved to the [cogni-ai-architect plugin](../plugins/cogni-ai-architect/) for better distribution and maintenance.

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

### [Cogni AI Git Ops](../plugins/cogni-ai-git-ops/agents/cogni-ai-git-ops.agent.md)

Autonomous Git Operations agent. Specializes in version control, complex git workflows, rebase operations, and repository management.

### [Cogni AI Coder](../plugins/cogni-ai-coder/agents/cogni-ai-coder.agent.md)

Autonomous coding agent that translates specifications into functional code with precision, speed, and strict convention adherence. Applies Design-by-Contract, Single-Variable Delta Rule, and Exhaustive Validation.

### [Cogni AI Programmer](../plugins/cogni-ai-programmer/agents/cogni-ai-programmer.agent.md)

Autonomous programmer assistant specializing in designing correct, efficient, and maintainable solutions. Solves technical problems using algorithms, data structures, and comprehensive testing.

### [Cogni AI Developer](../plugins/cogni-ai-developer/agents/cogni-ai-developer.agent.md)

Autonomous developer assistant that architects, builds, and ships end-to-end solutions. Focuses on delivering user and business value through full-cycle product development.

### [Cogni AI Code Reviewer](cogni-ai-code-reviewer.agent.md)

Elite autonomous agent for code review, PR analysis, and enforcing zero-defect quality and security validation.

### [Cogni AI Plan Reviewer](cogni-ai-plan-reviewer.agent.md)

Elite autonomous architectural reviewer for plan validation and ensuring strategic alignment.

### [Cogni AI Weaver](cogni-ai-weaver.agent.md)

Canonical flow-custody kernel and diagram steward. Specializes in flowchart memory:
decision chains, causal flows, dependencies, state transitions, timelines.
