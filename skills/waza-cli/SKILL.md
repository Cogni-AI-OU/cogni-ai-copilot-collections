---
name: waza-cli
description: 'Expert-level guide for using the waza CLI to automate the skill development workflow and run evaluation benchmarks. You MUST load this skill when working with the waza command.'
license: MIT
---

# Waza CLI Skill

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## WHEN TO USE

- When initializing, configuring, or generating waza evaluation suites.
- When running evaluation benchmarks from a YAML spec file.
- When serving the interactive dashboard to view results.
- When comparing results from multiple evaluation runs side by side.
- When scoring current skills and suggesting improvements.

## Prerequisites

- Waza CLI (`waza`) must be installed.
- To install: `curl -fsSL https://raw.githubusercontent.com/microsoft/waza/main/install.sh | bash`
- By default, Waza uses the `copilot-sdk` executor and needs GitHub Copilot access for running evaluations.
  Run `copilot login` in your terminal to authenticate.

## Core Process

1. Use `waza init` to initialize a new evaluation suite.
2. Use `waza generate` to create an eval suite from an existing `SKILL.md` file.
3. Use `waza run` to execute evaluation benchmarks.
4. Use `waza serve` to view results.

## Step-by-Step Workflows

### Project Setup & Configuration

- **Initialize project**: `waza init` (Creates `eval.yaml`, `tasks/` with example task, `fixtures/` with example fixture)
- **Initialize in named directory**: `waza init my-eval-suite`
- **Generate eval from SKILL.md**: `waza generate path/to/SKILL.md` (Parses YAML frontmatter like name, description, and creates eval.yaml, starter tasks, and fixtures)
- **Generate with specific output dir**: `waza generate SKILL.md --output-dir ./my-eval`

### Running Evaluations (`waza run`)

Run an evaluation benchmark from a YAML spec file:
- **Run with default mock engine**: `waza run path/to/eval.yaml --context-dir path/to/fixtures`
- **Verbose output with results saved**: `waza run eval.yaml -c ./fixtures -v -o results.json`
- **Filter to specific tasks**: `waza run eval.yaml -t "task-name-1" -t "task-name-2"`
- **Parallel execution**: `waza run eval.yaml --parallel --workers 4`
- **Save per-task transcripts**: `waza run eval.yaml --transcript-dir ./transcripts`

### Viewing Results and Comparison (`waza serve` / `waza compare`)

- **Serve interactive dashboard**: `waza serve`
- **Compare two result files**: `waza compare run1.json run2.json`
- **Compare three or more**: `waza compare gpt4.json claude.json gemini.json`
- **JSON output format**: `waza compare run1.json run2.json --format json`
  *(Shows per-task score deltas, pass rate differences, and aggregate statistics)*

### Iteratively Improve SKILL.md (`waza dev`)

Iteratively improve `SKILL.md` frontmatter compliance with automated scoring:
- **Score skill and suggest improvements**: `waza dev skills/my-skill`
- **Target high compliance level**: `waza dev skills/my-skill --target high`
- **Auto-apply improvements**: `waza dev skills/my-skill --target medium --auto --max-iterations 3`

## Quick Start Example

```bash
# Create Your First Skill
# Initialize a project and create a skill:
mkdir my-eval-suite
cd my-eval-suite
waza init
waza new skill my-skill

# Run Eval:
waza run skills/my-skill/evals/eval.yaml -v
# (The -v flag shows verbose output. Omit it for a summary.)

# Serve the interactive dashboard:
waza serve
```

## Examples

```console
# Run all tasks
waza run eval.yaml -v

# Run specific skill
waza run code-explainer

# Specify fixtures directory
waza run eval.yaml -c ./fixtures -v

# Save results
waza run eval.yaml -o results.json

# Filter to specific tasks
waza run eval.yaml --task "basic*" --task "edge*"

# Multiple models (parallel)
waza run eval.yaml --model gpt-4o --model claude-sonnet-4.6

# Use a different judge model for LLM-as-judge graders
waza run eval.yaml --model gpt-4o --judge-model claude-opus-4.6

# Parallel execution with 8 workers
waza run eval.yaml --parallel --workers 8

# With caching
waza run eval.yaml --cache --cache-dir .waza-cache

# Generate JUnit XML for CI test reporting
waza run eval.yaml --reporter junit:results.xml

# A/B testing: baseline vs skill performance
waza run eval.yaml --baseline -o results.json
# Output includes improvement breakdown (quality, tokens, turns, time, completion)

# Auto-update diff grader snapshots
waza run eval.yaml --update-snapshots

# Auto skill discovery
waza run --discover ./skills/

# Auto discovery with strict mode (fail if any SKILL.md lacks eval coverage)
waza run --discover --strict ./skills/

# Skip grading, then grade separately
waza run eval.yaml --skip-graders -o results.json
waza grade eval.yaml --results results.json

# Session event logging
waza run eval.yaml --session-log --session-dir ./logs

# Multi-model comparison with recommendation
waza run eval.yaml --model gpt-4o --model claude-sonnet-4.6 --recommend

# Keep temp workspaces for debugging fixture issues
waza run eval.yaml --keep-workspace -v
```

## References

- [Waza Quick Start](https://microsoft.github.io/waza/quick-start/)
- [Waza repository](https://github.com/microsoft/waza)
- [Waza CLI Reference](https://github.com/microsoft/waza/blob/v0.33.0/site/src/content/docs/reference/cli.mdx)
  Complete reference for all waza CLI commands and their options.

## Related Skills

- **waza-docs**:
  Documentation and references for waza CLI and its internals.
- **agentskills**:
  Reference for the Agent Skills open standard. Defines the schema, directory structure, formatting, and portability requirements for agent skills.
