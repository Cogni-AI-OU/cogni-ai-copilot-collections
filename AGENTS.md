# AGENTS.md

Persistent single-source truth for autonomous agent behavior.

For general project invariants see [README.md](README.md).

## Agents Catalog

This repository is the source of truth for Cogni AI agent files.
Agent files live at the repository root so they are accessible directly when
this repo is cloned into `.github/agents`.

- [**Cogni AI Agent Auditor**](cogni-ai-agent-auditor/cogni-ai-agent-auditor.agent.md):
  Expert autonomous auditor specializing in analyzing agent session logs, evaluating reasoning workflows,
  and generating visual reports.
- [**Cogni AI Architect**](cogni-ai-architect/cogni-ai-architect.agent.md):
  Primary autonomous coding agent with critical thinking, robust problem-solving,
  and context-aware resource management.
- [**Cogni AI DevOps**](cogni-ai-devops/cogni-ai-devops.agent.md):
  Elite autonomous DevOps and Site Reliability Engineering agent focusing on task
  automation, CI/CD pipeline precision, and infrastructure-as-code.
- [**Cogni AI Elite**](cogni-ai-elite/cogni-ai-elite.agent.md):
  Elite autonomous systems architect engineered for structural perfection
  and recursive problem decomposition.
- [**Cogni AI Fact Ops**](cogni-ai-fact-ops/cogni-ai-fact-ops.agent.md):
  Autonomous fact operator responsible for maintaining canonical fact files
  and information consistency.
- [**Cogni AI Context7 Ops**](cogni-ai-context7-ops/cogni-ai-context7-ops.agent.md):
  Autonomous context gathering agent specialized in retrieving and filtering
  documentation from the Context7 service.
- [**Cogni AI GitHub Ops**](cogni-ai-github-ops/cogni-ai-github-ops.agent.md):
  Autonomous GitHub Operator responsible for GitHub operations such as
  modifying comments, issues, or discussions on behalf of other agents.
- [**Cogni AI Keeper**](cogni-ai-keeper/cogni-ai-keeper.agent.md):
  Canonical fact custody and mindmap stewardship kernel for structured
  knowledge management.
- [**Cogni AI Python Dev**](cogni-ai-python-dev/cogni-ai-python-dev.agent.md):
  Autonomous Python Developer responsible for writing, testing,
  and debugging Python 3 code.
- [**Cogni AI Code Reviewer**](cogni-ai-code-reviewer/cogni-ai-code-reviewer.agent.md):
  Elite autonomous code reviewer for PR analysis, quality enforcement,
  and zero-defect security validation.
  Operates in a strict review-only mode via GitHub API/CLI (`gh pr`)
  without executing tests or mutating files.
- [**Cogni AI Plan Reviewer**](cogni-ai-plan-reviewer/cogni-ai-plan-reviewer.agent.md):
  Elite autonomous architectural reviewer for plan validation
  and ensuring strategic alignment.
- [**Cogni AI Security Auditor**](cogni-ai-security-auditor/cogni-ai-security-auditor.agent.md):
  Elite autonomous security auditor specializing in zero-defect threat modeling,
  vulnerability detection, and hardening boundaries.
- [**Cogni AI Tester**](cogni-ai-tester/cogni-ai-tester.agent.md):
  Autonomous Tester responsible for executing test tasks, ensuring quality,
  and verifying system behavior.
- [**Cogni AI Weaver**](cogni-ai-weaver/cogni-ai-weaver.agent.md):
  Canonical flow custody and diagram stewardship kernel specializing in
  flowchart and dependency memory.
- [**Cogni AI Brain Ops**](cogni-ai-brain-ops/cogni-ai-brain-ops.agent.md):
  Autonomous brainstorming agent responsible for gathering facts,
  describing constraints, and architecting suggested plans and tasks.

## Persistent Memory & Context Files

Read and merge these when operating inside corresponding sub-directories or repo root (order = precedence):

- `FACTS.mmd` (Root canonical fact store and project mindmap)
- `AGENTS.mmd` and `FLOWS.mmd` (Root canonical diagrams, flows, and booting sequence visualizations)
- `CONSTRAINTS.mzn` (Formal constraint declarations: scheduler-theoretic bounds, budget protocol, and loop arrest)
- [`.github/AGENTS.md`](.github/AGENTS.md) (Directory-specific health and agent guidance)
- [`.github/copilot-instructions.md`](.github/copilot-instructions.md) (Domain context and IDE constraints)
- [`.github/skills/AGENTS.md`](.github/skills/AGENTS.md) to discover the available
  skill catalog before interpreting the user request
- [`.vscode/AGENTS.md`](.vscode/AGENTS.md) (command permissions and tasks)
- Any other directory-specific `AGENTS.md` or `AGENTS.mmd` (which must be followed for sequence booting instructions),
  or `SKILL.md` in ancestor, then current directory tree

## Core Agent Execution Protocol

Autonomous agents operating in this repository MUST adhere to the core loading protocols
and execution logic defined in [AGENTS-RUNTIME.md](AGENTS-RUNTIME.md).

## Multi-Repository Architecture & Git Isolation

- **Directory Boundaries**:
  In consumer repositories where these agents are deployed (following the
  [setup instructions](README.md#installation) to install the required agents),
  `.github/agents/`, `.github/skills/`, and `.github/instructions/`
  are typically cloned as separate external repositories or git submodules.
  They are NOT standard native subdirectories of the root repository.
- **Git Context Switching**:
  When an agent performs modifications inside the root repository, and simultaneously
  modifies files inside one of these `.github/*` directories, they must be aware that they are touching
  separate `.git` instances.
- **Strict Prohibition**:
  NEVER attempt to run `git add`, `git commit`, or `git mv` from the root workspace
  to track changes in these subdirectories, as that will fail or corrupt the repository boundaries.
  All git operations must be correctly scoped (e.g. `cd .github/skills && git ...`) or entirely omitted
  (delegated to the user based on the interactive-editor protocol in `copilot-instructions.md`).

## Subagent Delegation

- **Spawning Sub-agents**:
  If subagent delegation is enabled in the runtime, agents are encouraged to spawn new
  sub-agents to handle complex, multi-step, or parallelizable tasks.
  This promotes modular problem-solving and efficient resource utilization.

## Architecture Principles: Agents vs Skills vs Instructions

To prevent redundancy and context drift, always enforce a strict conceptual boundary when authoring system components:

1. **Agents (`*.agent.md`) - The "Who" and "Why"**:
   - **Focus**:
     Persona, invariants, cognitive framework, escalation gates, and output constraints.
   - **Rule**:
     Do not embed explicit execution tutorials or command-by-command scripts here.
     Instruct the agent *who* they are, *what* constraints they must obey (e.g. "Never mutate files directly"),
     and explicitly tell them to invoke specific skills for mechanical processes.

2. **Skills (`SKILL.md`) - The "How" (Execution Playbooks)**:
   - **Focus**:
     Tools, commands, step-by-step procedures, and mechanical execution.
   - **Rule**:
     Isolates the exact `bash`, `gh`, or API mechanics.
     A skill is agnostic to *who* uses it.
     It exists strictly to define *how* an audit, a build, or a commit sync is correctly executed.

3. **Instructions (`*.instructions.md`) - The "Rules" (Domain Standards)**:
   - **Focus**:
     Formatting standards, coding conventions, and structural rules (e.g. JSON schema, Python dependencies).
   - **Rule**:
     Applied dynamically based on the file-type or project paths being modified.
     They govern the output structure regardless of which agent or skill generated it.

## Required References

- **Project overview & install**:
  [README.md](README.md)
- **Agent configuration & conventions**:
  [.github/copilot-instructions.md](.github/copilot-instructions.md)
- **Workflow navigation**:
  [.tours/getting-started.tour](.tours/getting-started.tour)
- **Latest org baseline**:
  <https://github.com/Cogni-AI-OU/.github/blob/main/AGENTS.md>

## Example Structure for New/Updated AGENTS.md Files

```markdown
# AGENTS.md  (subdir-specific)

## Setup & Environment Invariants

- ...

## Key Files & Context Injection

- ...

## Agent Directives (Contract Style)

- Role, then invariants, then ...
- NEVER ...
- MUST ...

## Testing & Verification Gates

- ...

## Troubleshooting Matrix

> signature error / smell
- root-cause vector
- isolation steps
- verified fix + prevention

## Final Assurance Gates

- Keep this file entropy-pruned and up-to-date.
- Inject full content into every sub-agent context.
- For latest version see:
  <https://github.com/Cogni-AI-OU/.github/blob/main/AGENTS.md>
- For latest standard see:
  <https://agents.md/>


## References

- **Main documentation**:
  [README.md](README.md)
