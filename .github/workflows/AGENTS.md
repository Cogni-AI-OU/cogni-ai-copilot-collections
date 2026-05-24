# GitHub Actions Workflows (Agent Catalog)

Authoritative, agent-facing catalog of workflows in this repository. Use this when loading or modifying
workflows and keep it in sync with the files in this directory.

For a human-readable overview, see [README.md](README.md).

## Workflow catalog

- **[check.yml](check.yml)**: Linting and quality gates via actionlint and pre-commit.
- **[check-pr-comment.yml](check-pr-comment.yml)**: PR feedback and label management for Check workflow results.
- **[cogni-ai-agent.yml](cogni-ai-agent.yml)**: Logic for the Cogni AI Agent.
- **[copilot-setup-steps.yml](copilot-setup-steps.yml)**: Environment setup utility.
- **[devcontainer-ci.yml](devcontainer-ci.yml)**: Build/test devcontainer and required tools/packages.
- **[waza-check.yml](waza-check.yml)**: Waza validation for skill files.

## Details

### check.yml

- Purpose: run actionlint and pre-commit to enforce workflow and repo standards.
- Triggers: `push`, `pull_request`, `schedule`, `workflow_call`, `workflow_dispatch`,
  `workflow_run` (after bot workflow completions).
- Bot-PR support: `workflow_run` trigger enables checks on PRs created by bots,
  since normal `pull_request` events don't trigger for bot actors.
- Reusable: `uses: Cogni-AI-OU/.github/.github/workflows/check.yml@main`.
- Jobs: `actionlint`, `link-checker`, `pre-commit`.

### check-pr-comment.yml

- Purpose: Extracts annotations from failed `Check` workflow runs and posts them as a PR comment.
- Triggers: `workflow_run` (after `Check` workflow completions).
- Details: Manages the `check-error` label and provides detailed PR feedback for failed runs.
- Reusable: `uses: Cogni-AI-OU/.github/.github/workflows/check-pr-comment.yml@main`.

### cogni-ai-agent.yml

- Purpose: provides the underlying logic to run the Cogni AI Agent.
- Triggers: `issue_comment`, `pull_request_review_comment`, `issues`, `pull_request`,
  `discussion`, `discussion_comment`, `workflow_dispatch`.
- Details: Installs Python dependencies from `.devcontainer/requirements.txt` and calls the
  `Cogni-AI-OU/cogni-ai-agent-action` to process instructions.
- Permissions: `contents: write`, `id-token: write`, `issues: write`, `pull-requests: write`,
  `discussions: write`.

### copilot-setup-steps.yml

- Purpose: utility workflow for setting up the environment.
- Triggers: `push` and `pull_request` on `copilot-setup-steps.yml` or `.devcontainer/requirements.txt`.
- Details: Checks out repo, sets up Python 3.12, restores cache, and installs dependencies.
- Permissions: `contents: read`.

### devcontainer-ci.yml

- Purpose: build and validate the dev container; ensure required tools and Python packages exist.
- Inputs: `required_commands` (defaults to common CLI tools), `required_python_packages`
  (defaults to ansible, ansible-lint, docker, molecule, pre-commit, uv).
- Triggers: pull_request/push affecting `.devcontainer/` or this workflow; weekly schedule;
  `workflow_call`.
- Permissions: callers must grant `packages: write` when pushing images to GHCR.
- Reusable: `uses: Cogni-AI-OU/.github/.github/workflows/devcontainer-ci.yml@main`.

### waza-check.yml

- Purpose: run Waza validation framework on skill files (SKILL.md, .agent.md) in PRs.
- Triggers: `pull_request` and `push` when `**/SKILL.md`, `**/*.agent.md`, or skill directories
  (`.github/skills/**`, `skills/**`, `plugins/**/skills/**`) are modified, and `workflow_dispatch`.
- Details: Installs Go, builds waza from source (github.com/microsoft/waza), detects changed
  skill files via `git diff`, and runs `waza check` on each for compliance validation.
  On `workflow_dispatch`, also supports running `waza run` with an optional eval path or auto-discovery.
  Saves results as artifacts for the comment workflow.
- Permissions: `contents: read`.

### waza-check-pr-comment.yml

- Purpose: Posts results from the "Waza Check" workflow as a PR comment.
- Triggers: `workflow_run` (after Waza Check), `workflow_call`, `workflow_dispatch`.
- Details: Downloads the waza-check-results artifact and posts a "Skill Readiness Check" comment
  with error/warning counts and findings. Updates existing comments via marker detection.
- Permissions: `issues: write`, `pull-requests: write`, `actions: read`.

## Synchronized Configuration

The following configuration values **MUST** be kept in sync across multiple files:

### Model options list

The `model` input options for `workflow_dispatch` must be identical in the corresponding workflow files:

| File | Location |
| ---- | -------- |
| [cogni-ai-agent.yml](cogni-ai-agent.yml) | `workflow_dispatch` inputs |

## Notes

- Keep this catalog updated when workflows are added, removed, or renamed.
