---
name: waza-cli
description: 'Expert-level guide for using the waza CLI to automate the skill development workflow and run evaluation benchmarks. You MUST load this skill when working with the waza command.'
license: MIT
---

# Waza CLI Skill

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## When to Use This Skill

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

## Related Skills

- **waza-docs**:
  Documentation and references for waza CLI and its internals.
- **agentskills**:
  Reference for the Agent Skills open standard. Defines the schema, directory structure, formatting, and portability requirements for agent skills.

## References

- [Waza Quick Start](https://microsoft.github.io/waza/quick-start/)
- [Waza SKILL.md Example](https://github.com/microsoft/waza/blob/1dd4a7164638350708619a08fad83936b50ff813/skills/waza/SKILL.md?plain=1#L3)
