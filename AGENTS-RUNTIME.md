# AGENTS-RUNTIME.md

Persistent single-source truth for autonomous agent behavior in runtime environments.

## Agents Catalog

This repository is the source of truth for Cogni AI agent files.
Agent files live in the `agents/` directory so they are accessible directly when
this repo is cloned into `.github/agents`.

- [**Cogni AI Architect**](agents/cogni-ai-architect.agent.md):
  Primary autonomous coding agent with critical thinking, robust problem-solving, and context-aware resource management.
- [**Cogni AI DevOps**](agents/cogni-ai-devops.agent.md):
  Elite autonomous DevOps and Site Reliability Engineering agent focusing on task
  automation, CI/CD pipeline precision, and infrastructure-as-code.
- [**Cogni AI Elite**](agents/cogni-ai-elite.agent.md):
  Elite autonomous systems architect engineered for structural perfection and recursive problem decomposition.
- [**Cogni AI Fact Ops**](agents/cogni-ai-fact-ops.agent.md):
  Autonomous fact operator responsible for maintaining canonical fact files and information consistency.
- [**Cogni AI Context7 Ops**](agents/cogni-ai-context7-ops.agent.md):
  Autonomous context gathering agent specialized in retrieving and filtering documentation from the Context7 service.
- [**Cogni AI GitHub Ops**](agents/cogni-ai-github-ops.agent.md):
  Autonomous GitHub Operator responsible for GitHub operations such as
  modifying comments, issues, or discussions on behalf of other agents.
- [**Cogni AI Manager**](agents/cogni-ai-manager.agent.md):
  Autonomous orchestration and coordination manager responsible for routing work
  to specialized agents and ensuring end-to-end completion.
- [**Cogni AI Keeper**](agents/cogni-ai-keeper.agent.md):
  Canonical fact custody and mindmap stewardship kernel for structured knowledge management.
- [**Cogni AI Programmer**](plugins/cogni-ai-programmer/agents/cogni-ai-programmer.agent.md):
  Autonomous programmer assistant specializing in Python. Writes, refactors, and verifies Python 3 code with type safety and idiomatic patterns.
- [**Cogni AI Code Reviewer**](agents/cogni-ai-code-reviewer.agent.md):
  Elite autonomous code reviewer for PR analysis, quality enforcement, and zero-defect security validation.
- [**Cogni AI Plan Reviewer**](agents/cogni-ai-plan-reviewer.agent.md):
  Elite autonomous architectural reviewer for plan validation and ensuring strategic alignment.
- [**Cogni AI Tester**](agents/cogni-ai-tester.agent.md):
  Autonomous Tester responsible for executing test tasks, ensuring quality, and verifying system behavior.
- [**Cogni AI Weaver**](agents/cogni-ai-weaver.agent.md):
  Canonical flow custody and diagram stewardship kernel specializing in flowchart and dependency memory.
- [**Cogni AI Brain Ops**](agents/cogni-ai-brain-ops.agent.md):
  Autonomous brainstorming agent responsible for gathering facts, describing constraints,
  and architecting suggested plans and tasks.

### Structural Invariant

- **Agents Location**: Agent files live in the `agents/` directory.
- **Skills Location**: Skill files live in the `skills/` directory.
- **Instructions Location**: Instruction files live in the `instructions/` directory.

## Subagent Delegation

- **Spawning Sub-agents**:
  If subagent delegation is enabled in the runtime, agents are encouraged to spawn new
  sub-agents to handle complex, multi-step, or parallelizable tasks.
  This promotes modular problem-solving and efficient resource utilization.
