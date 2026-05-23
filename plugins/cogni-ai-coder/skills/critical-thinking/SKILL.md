---
name: critical-thinking
description: >-
  Engage deep analytical reasoning, follow behavioral guidelines, deconstruct assumptions, apply Socratic questioning,
  and perform adversarial red-teaming to solve complex problems and validate architectural plans.
  You MUST load this skill when facing challenges that require critical thinking,
  especially when writing, reviewing, or refactoring code to avoid overcomplication.
license: MIT
---
# critical-thinking

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

A cognitive framework for deep analytical reasoning.

## When to Use

- When confronted with an ambiguous, contradictory, or complex problem that defies immediate technical fixes.
- Before embarking on a massive, repository-wide architectural refactoring.
- When an automated test or build fails silently and standard debugging yields no obvious root cause.

## When Not to Use

- For trivial syntax errors or obvious spelling mistakes.
- When the user explicitly requests immediate, uncritical execution of a basic command without review.
- If a problem is already solved and simply requires writing documentation.

## Common Pitfalls

- **Paralysis by Analysis**: Spending so much time red-teaming and generating alternative hypotheses that no actual code gets written or debugged.
- **Ignoring Empirical Data**: Relying purely on abstract logical models while ignoring the actual tracebacks or logs presented in the current environment.
- **Over-Modeling**: Writing a 500-line MiniZinc model for a problem that can be solved with a simple unit test.

## Core Process

1. **Analyze**: Review the task, issue, or error to understand the requirements.
2. **Deconstruct & Frame**: Separate the final goal (Conclusion) from the underlying logic (Premises).
3. **Surface Hidden Dependencies**: Identify what must be true for the current logic to hold (assumptions, state, concurrency). **State your assumptions explicitly. If uncertain, ask.**
4. **Generate Hypotheses**: Explicitly list alternative explanations or missing context before acting. **If multiple interpretations exist, present them—don't pick silently.**
5. **Push for Simplicity**: **If a simpler approach exists, say so. Push back when warranted.**
6. **Clarification Protocol**: **If something is unclear, stop. Name what's confusing. Ask.**
7. **Transform Tasks into Verifiable Goals**: Reframe ambiguity into provable outcomes:
   - "Add validation" → "Write tests for invalid inputs, then make them pass"
   - "Fix the bug" → "Write a test that reproduces it, then make it pass"
   - "Refactor X" → "Ensure tests pass before and after"
8. **Root Cause Isolation**: When troubleshooting, split the problem into smaller, reproducible steps and use version history (`git blame`/`git log`) or execution logs to narrow down the fault.
9. **Adversarial Red-Teaming**: Aggressively attempt to break your proposed plan. Identify the exact line or condition most likely to fail.
10. **Constraint Formulation (MiniZinc)**: When applicable, formally model the problem's constraints by writing dry-code definitions in MiniZinc to expose hidden dependencies and restrictions.
11. **Verify Systemically**: Evaluate the decision against immediate needs, technical debt accrual, and long-term maintainability. **Emit a post-verification trace**: a short written summary in the current response that lists the checks performed, the evidence observed, and the final verification result.
12. **Persist & Close**: After verification, record the outcome, an **assumptions ledger** (a bullet list of assumptions made, which were verified, and which remain open), and any new invariants in the skill's persistent memory/store if one is available; otherwise include them in the current response. Then emit a final **Hard Checkpoint**: a concise closing summary of decision, evidence, remaining risks, and next step.

## Core Principles

- **Active Disconfirmation**: Do not seek evidence that confirms your theory; design experiments that would prove your favorite hypothesis wrong.
- **Burden of Proof Calibration**: Align evidence requirements with risk. High-risk changes demand formal-level proof; low-risk changes require empirical checks.
- **Constraint-Aware Design**: Explicitly map and adhere to project-specific constraints (architectural, performance, security).
- **Fact-Based Reasoning**: Base every decision on empirically gathered facts from the codebase rather than assumptions.
- **Formal Constraint Mapping**: Use MiniZinc snippets as a dry-code exercise to rigorously define problem boundaries, resources, and requirements.
- **Goal-Driven Execution**: Define success criteria. Loop until verified. Transform tasks into verifiable goals. Strong success criteria let you loop independently.
- **Information Gain Optimization**: Prioritize actions that maximize information about the system's state over actions that merely "try to fix it."
- **Internal Tension Scan**: Search for self-contradictions within the plan (e.g., claiming a system is "high-performance" while introducing O(n²) complexity in a critical path).
- **Keep Changes Atomic and Focused**: Make one logical change per PR or commit. Avoid mixing refactors, formatting, and behavior changes unless they are inseparable.
- **Simplicity First**: Minimum code that solves the problem. Nothing speculative.
- **Socratic Depth**: Apply a minimum "3-Why" drill-down for any anomaly. Move from the immediate symptom to the behavioral anomaly, to the foundational flaw.
- **Surgical Changes**: Touch only what you must. Clean up only your own mess.
- **The Steelman Protocol**: Before critiquing a plan, articulate it in its strongest possible form. If you cannot Steelman it, you are not ready to reject it.
- **Think Before Coding**: Don't assume. Don't hide confusion. Surface tradeoffs.
- **Use Judgment**: For trivial tasks, use judgment.

## Diagnostics and Usage Patterns

- **MiniZinc Dry-Code**:
  Write MiniZinc `.mzn` snippets to formally declare the parameters, decision variables, and constraints of the problem space, even if you do not execute the solver immediately.

## Self-Improvement Workflow

When encountering a new error or issue:

1. **Document the problem**
   - What command was run?
   - What was the error or unexpected behavior?
   - What was the intended outcome?
   - Have you loaded the right skills to overcome this issue?
2. **Isolate the cause**
   - Identify the smallest reproducible scenario.
   - Separate observed facts from assumptions.
   - Determine whether the issue is in logic, data, environment, or expectations.
3. **Form and test a hypothesis**
   - State the most likely root cause.
   - Make the smallest possible change to test that hypothesis.
   - Prefer one variable at a time so results stay interpretable.
4. **Verify the fix**
   - Confirm the original issue is resolved.
   - Check for regressions or broken adjacent behavior.
   - Ensure the result matches the intended outcome, not just the absence of the error.
5. **Record the learning**
   - Note the root cause, the successful fix, and any misleading signals.
   - Capture which skills, diagnostics, or heuristics were most useful.
   - Reuse the lesson in future debugging and code review.

## What to Avoid

- **Adjacent Polishing**: Don't "improve" adjacent code, comments, or formatting.
- **Confirmation Bias**: Over-weighting evidence that supports an initial guess while ignoring contradictory anomalies.
- **Feature Creep**: No features beyond what was asked.
- **Impossible Scenario Guarding**: No error handling for impossible scenarios.
- **The Sunk Cost Fallacy**: Persisting with a failing approach or refactor just because effort was already invested.
- **Over-Abstraction**: No abstractions for single-use code.
- **Proactive Refactoring**: Don't refactor things that aren't broken.
- **Shallow Fixes**: Patching symptoms instead of addressing the architectural or structural root causes.
- **Speculative Generality**: No "flexibility" or "configurability" that wasn't requested.
- **Unauthorized Deletion**: Don't remove pre-existing dead code unless asked.

## Limitations

- This skill provides a cognitive framework but does not execute external tooling; it relies on the agent to apply these principles internally during planning, execution, and review phases.
