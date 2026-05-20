# AGENTS.md

Persistent single-source truth for autonomous agent behavior.

For general project invariants see [README.md](README.md).

## Agents Catalog

This repository is the source of truth for Cogni AI agent files.
Agent files live in the `agents/` directory so they are accessible
directly when this repo is cloned into `.github/agents`.

See [agents/README.md](agents/README.md) for the complete agent catalog with descriptions.

## Persistent Memory & Context Files

Read and merge these when operating inside corresponding sub-directories or repo root (order = precedence):

- `docs/FACTS.mmd` (Root canonical fact store and project mindmap)
- `AGENTS.mmd` (Booting sequence and initialization) and `docs/FLOWS.mmd` (Timelines and operational protocols)
- `CONSTRAINTS.mzn` (Formal constraint declarations: scheduler-theoretic bounds, budget protocol, and loop arrest)
- [`.github/AGENTS.md`](.github/AGENTS.md) (Directory-specific health and agent guidance)
- [`.github/copilot-instructions.md`](.github/copilot-instructions.md) (Domain context and IDE constraints)
- `AGENTS-RUNTIME.md` (runtime loading protocols and skill catalog)
- `.github/skills/AGENTS.md` (cloned in CI; skill catalog before interpreting the user request)
- [`.vscode/AGENTS.md`](.vscode/AGENTS.md) (command permissions and tasks)
- Any other directory-specific `AGENTS.md` or `*.agent.mmd` (which must be followed for sequence booting instructions),
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
