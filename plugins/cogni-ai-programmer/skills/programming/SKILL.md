---
name: programming
description: >-
  Expert workflow for solving technical problems with code — designing algorithms,
  data structures, and reliable solutions with a focus on correctness, efficiency,
  and maintainability. You MUST load this skill when designing and implementing
  algorithmic solutions or building robust modules and subsystems.
license: MIT
---
# programming

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

A methodical approach to building robust, correct, and efficient code solutions. Focuses on problem decomposition, algorithm design, edge case handling, and code craftsmanship.

## When to Use

- When designing and implementing algorithms, data structures, or complex logic.
- When building modules, features, or subsystems that require careful design.
- When optimizing existing code for performance, correctness, or maintainability.
- When debugging complex issues that require deep logical analysis.

## When Not to Use

- For simple implementation of well-defined specs without algorithmic complexity (use `coding`).
- For full product lifecycle tasks involving deployment, monitoring, or stakeholder management (use `development`).
- For one-off scripts or exploratory data transformations.

## Common Pitfalls

- **Premature Optimization**: Optimizing before measuring, leading to complex code without proven benefit.
- **Edge Case Blindness**: Implementing the happy path but missing null inputs, boundary values, or error states.
- **Over-Abstraction**: Introducing interfaces and patterns that obscure the core logic.
- **Incomplete Verification**: Assuming correctness without comprehensive test coverage.

## Core Process

1. **Understand the Problem**: Deconstruct the requirements. Identify inputs, outputs, constraints, and edge cases.
2. **Design the Solution**: Choose appropriate algorithms and data structures. Consider time/space complexity trade-offs.
3. **Plan the Structure**: Define module boundaries, interfaces, and data flow before writing code.
4. **Implement with Precision**: Write clean, well-typed code that handles all identified paths.
5. **Test Thoroughly**: Cover happy path, edge cases, error conditions, and performance boundaries.
6. **Review & Refactor**: Scrutinize for correctness, efficiency, and maintainability. Refactor without changing behavior.

## Core Principles

- **Correctness First**: The solution must produce the right answer for all valid inputs.
- **Edge Case Awareness**: Actively enumerate and handle boundary conditions, empty states, and error inputs.
- **Complexity Transparency**: Be explicit about time and space complexity of chosen approaches.
- **Clean Code**: Write readable, well-structured code that communicates intent clearly.
- **Test-Driven Confidence**: Every logical path should be verified by a test.

## What to Avoid

- **Guess-Driven Optimization**: Optimizing without profiling data or benchmarks.
- **Silent Failures**: Swallowing exceptions or returning incorrect results without signaling errors.
- **Copy-Paste Logic**: Duplicating logic instead of extracting reusable functions or modules.
- **Untestable Coupling**: Hard-coding dependencies that make isolated testing impossible.

## Related Skills

- **python** (or language-specific skills):
  You MUST load the relevant language skill for idiomatic syntax, type hints, and framework conventions.
