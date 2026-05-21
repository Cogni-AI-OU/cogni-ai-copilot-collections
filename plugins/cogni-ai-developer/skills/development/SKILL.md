---
name: development
description: >-
  Workflow and guidelines for full-cycle software development, feature implementation,
  and architecture-compliant execution. You MUST load this skill when building features
  or acting as an autonomous developer.
license: MIT
---
# development

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

A workflow and set of guidelines for robust, end-to-end feature development.

## When to Use

- When developing new features or building software components.
- When tasked with translating a user requirement into a fully functional implementation.
- When you need to ensure code aligns with architectural patterns.

## When Not to Use

- For simple one-line bug fixes that do not require full-cycle development context.
- When just formatting or linting code.
- When generating documentation without code changes.

## Core Process

1. **Understand Requirements**: Analyze user request, identify core functionality, and constraints.
2. **Context Gathering**: Map out existing architectural patterns, dependencies, and impacted modules.
3. **Architecture Alignment**: Ensure the planned implementation seamlessly fits the existing structure.
4. **Implementation Strategy**: Break down the feature into small, logical increments.
5. **Execution**: Write clean, idiomatic, and maintainable code for each increment.
6. **Integration**: Integrate newly developed code with existing systems safely.
7. **Verification Check**: Ensure all tests, linters, and quality gates pass.

## Core Principles

- **End-to-End Ownership**: Deliver functional, verifiable features.
- **Incremental Progress**: Build and verify in small steps.
- **Maintainability First**: Write code that is easy to read, test, and adapt.
- **Architectural Harmony**: Mimic existing patterns instead of inventing new ones unless explicitly required.

## What to Avoid

- **Scope Creep**: Implementing more than what was asked.
- **Pattern Invention**: Ignoring existing architectural conventions in favor of personal preference.
- **Skipping Verification**: Committing or delivering code without running local builds and tests.
