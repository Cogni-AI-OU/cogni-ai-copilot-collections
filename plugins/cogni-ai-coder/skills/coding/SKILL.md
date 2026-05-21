---
name: coding
description: >-
  Workflow and guidelines for translating specifications into functional code with precision.
  Focuses on rapid implementation, syntax accuracy, and strict adherence to defined requirements.
  You MUST load this skill when acting as a coder focused on writing code to given specifications.
license: MIT
---
# coding

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

A focused workflow for implementing code from clear specifications. Emphasizes speed, accuracy, and convention compliance rather than open-ended problem-solving.

## When to Use

- When given well-defined requirements or designs and asked to turn them into functional code.
- When implementing specific UI components, API endpoints, or utility functions from specs.
- When performing bug fixes or small enhancements on existing codebases.
- When speed of delivery and syntax correctness are the primary success criteria.

## When Not to Use

- When the task requires designing novel algorithms or complex data structures from scratch (use `programming`).
- When the task involves full product lifecycle: requirements gathering, deployment, or stakeholder communication (use `development`).
- For system architecture, cross-module design decisions, or strategic technical planning.

## Common Pitfalls

- **Scope Creep**: Implementing more than what was specified. Stick to the exact requirements.
- **Convention Drift**: Writing code that works but ignores project style, naming, or architectural patterns.
- **Over-Engineering**: Adding abstractions, patterns, or flexibility that was not requested.
- **Skipping Verification**: Delivering untested code. Always run project linters and relevant tests.

## Core Process

1. **Read the Spec Fully**: Understand the exact inputs, outputs, and behavior before writing any code.
2. **Identify Conventions**: Check neighboring files for style, naming, imports, and patterns to mimic.
3. **Implement the Exact Contract**: Write the minimal code that satisfies the spec. Do not add speculative features.
4. **Verify Syntax**: Ensure the code compiles/parses without errors.
5. **Run Tests**: Execute project-specific linters and existing tests to confirm no regressions.
6. **Delivery**: Present the implementation with a concise summary of what was done.

## Core Principles

- **Spec Fidelity**: Implement precisely what was asked, nothing more, nothing less.
- **Convention Alignment**: Match existing code style, imports, and architecture exactly.
- **Minimal Surface Area**: Write the smallest, most direct solution that satisfies the requirements.
- **Verification Gate**: Every delivered code block must pass project linting and relevant tests.

## What to Avoid

- **Speculative Generality**: Do not add configurability, abstraction, or "future-proofing" that was not requested.
- **Unexplained Deviations**: If the spec has an ambiguity, ask rather than guess.
- **Refactoring Adjacent Code**: Do not improve unrelated code even if it looks suboptimal.

## Related Skills

- **critical-thinking**:
  You MUST load this skill when specifications are ambiguous, contradictory, or incomplete and require deeper analysis before coding.
