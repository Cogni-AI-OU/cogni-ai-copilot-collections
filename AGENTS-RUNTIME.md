# AGENTS-RUNTIME.md

Persistent single-source truth for autonomous agent behavior in runtime environments.

## Agents Catalog

This repository is the source of truth for Cogni AI agent files.
Agent files live at the repository root so they are accessible directly when
this repo is cloned into `.github/agents`.

- [**Cogni AI Architect**](cogni-ai-architect/cogni-ai-architect.agent.md):
  Primary autonomous coding agent with critical thinking, robust problem-solving, and context-aware resource management.
- [**Cogni AI DevOps**](cogni-ai-devops/cogni-ai-devops.agent.md):
  Elite autonomous DevOps and Site Reliability Engineering agent focusing on task
  automation, CI/CD pipeline precision, and infrastructure-as-code.
- [**Cogni AI Elite**](cogni-ai-elite/cogni-ai-elite.agent.md):
  Elite autonomous systems architect engineered for structural perfection and recursive problem decomposition.
- [**Cogni AI Fact Ops**](cogni-ai-fact-ops/cogni-ai-fact-ops.agent.md):
  Autonomous fact operator responsible for maintaining canonical fact files and information consistency.
- [**Cogni AI Context7 Ops**](cogni-ai-context7-ops/cogni-ai-context7-ops.agent.md):
  Autonomous context gathering agent specialized in retrieving and filtering documentation from the Context7 service.
- [**Cogni AI GitHub Ops**](cogni-ai-github-ops/cogni-ai-github-ops.agent.md):
  Autonomous GitHub Operator responsible for GitHub operations such as
  modifying comments, issues, or discussions on behalf of other agents.
- [**Cogni AI Keeper**](cogni-ai-keeper/cogni-ai-keeper.agent.md):
  Canonical fact custody and mindmap stewardship kernel for structured knowledge management.
- [**Cogni AI Python Dev**](cogni-ai-python-dev/cogni-ai-python-dev.agent.md):
  Autonomous Python Developer responsible for writing, testing, and debugging Python 3 code.
- [**Cogni AI Code Reviewer**](cogni-ai-code-reviewer/cogni-ai-code-reviewer.agent.md):
  Elite autonomous code reviewer for PR analysis, quality enforcement, and zero-defect security validation.
- [**Cogni AI Plan Reviewer**](cogni-ai-plan-reviewer/cogni-ai-plan-reviewer.agent.md):
  Elite autonomous architectural reviewer for plan validation and ensuring strategic alignment.
- [**Cogni AI Tester**](cogni-ai-tester/cogni-ai-tester.agent.md):
  Autonomous Tester responsible for executing test tasks, ensuring quality, and verifying system behavior.
- [**Cogni AI Weaver**](cogni-ai-weaver/cogni-ai-weaver.agent.md):
  Canonical flow custody and diagram stewardship kernel specializing in flowchart and dependency memory.

### Structural Invariant

- **Agents Location**: Agents are located directly in the root directory of this repository.

## Subagent Delegation

- **Spawning Sub-agents**:
  If subagent delegation is enabled in the runtime, agents are encouraged to spawn new
  sub-agents to handle complex, multi-step, or parallelizable tasks.
  This promotes modular problem-solving and efficient resource utilization.
