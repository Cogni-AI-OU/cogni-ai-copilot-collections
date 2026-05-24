---
name: docs-review
description: >-
  Enforce documentation quality, completeness, and mutual consistency across
  architecture files, ADRs, runbooks, READMEs, and code-level documentation.
  You MUST load this skill when asked to review or check consistency of documentation (such as *.md/*.mmd files).
license: MIT
---

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

# Docs Review

Guidance for reviewing core architecture, documentation, and constraint files for mutual consistency and accuracy. Use this skill when checking repository documentation.

## WHEN TO USE

- Auditing core architecture files (`*.mmd`, `*.mzn`) for consistency.
- Reviewing documentation (`**/AGENTS.md`, `**/README.md`) for outdated or contradictory references.
- Verifying that architectural decisions, operational procedures, and complex code blocks are accurately documented.

## WHEN NOT TO USE

- Writing completely new documentation from scratch (use `docs-writer` instead).
- Performing deep code execution or logic validation (use `testing` or `code-review` instead).
- Applying purely formatting or linting fixes.

## Common Pitfalls

- **Overzealous Editing**: Modifying architectural constraint files (`CONSTRAINTS.mzn`) arbitrarily without understanding the global impact, leading to runtime failures.
- **Surface-Level Checks**: Verifying that a markdown file exists without actually reading its content to ensure it accurately reflects the current codebase.
- **Ignoring Dependency Context**: Updating a README file while neglecting the corresponding `AGENTS.md` or ADR, creating localized inconsistency.

## Core Process

1. **Analyze Relationships**:
   Cross-reference the relationships, definitions, rules, and configurations defined across these files.
2. **Identify Inconsistencies**:
   Look for contradictions, outdated references, missing updates, or structural mismatches between files.
3. **Verify Up-to-Date Status**:
   Check if any of the documentation lags behind the current state of the repository.
4. **Conditional Edits**:
   **CRITICAL INSTRUCTION:** ONLY apply changes to these files if actual inconsistencies, contradictions,
   or outdated information are found. If all files are mutually consistent and up-to-date,
   do not make any edits—simply report back that the files are in order.

## Architectural Decision Records (ADRs) Verification

**Verify:** Every significant decision has an ADR (typically stored in `docs/decisions/`).

## Code-Level Documentation Verification

**Verify:** Every non-obvious code block has a "why" comment.
**Verify:** Code-level comments don't state the obvious.

## Runbooks Verification

**Verify:** Every on-call alert has a linked runbook (typically stored in `docs/runbooks/`).

## README Currency Verification

**Verify:** README reflects current state (not v1 state).
**Verify:** Setup instructions work on a fresh machine.
**Verify:** Architecture diagrams are up to date.

## Subdirectory Agents (`AGENTS.md`) Verification

**Verify:** Subdirectories with specific functionality have local `AGENTS.md` context files.
**Verify:** Local `AGENTS.md` aligns with the global repository invariants.

## Verification Checklist

- [ ] ADRs written for significant architectural decisions
- [ ] Non-obvious code blocks have "why" comments
- [ ] Every production alert has a linked runbook
- [ ] README is current and setup instructions work
- [ ] Subdirectories with specific functionality have local `AGENTS.md` context files

## Related Skills

- **critical-thinking**:
  You MUST load this skill when deconstructing complex documentation and identifying structural contradictions.
- **docs-writer**: Guidance for writing and maintaining documentation.
  You MUST load this skill when asked to write, document, or generate new documentation.
