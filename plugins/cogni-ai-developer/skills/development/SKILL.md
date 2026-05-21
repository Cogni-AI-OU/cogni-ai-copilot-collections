---
name: development
description: >-
  Workflow and guidelines for full-cycle software development — from requirements
  gathering and system design through deployment, monitoring, and iteration.
  Focuses on building and shipping working software that delivers user and business value.
  You MUST load this skill when building features or acting as an autonomous developer
  responsible for end-to-end product delivery.
license: MIT
---
# development

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

A comprehensive workflow for delivering complete, usable software that solves real needs. Covers the entire product lifecycle: understanding user needs, designing solutions, building, deploying, monitoring, and iterating.

## When to Use

- When developing end-to-end features that span multiple layers (frontend, backend, data).
- When responsible for the full lifecycle: requirements → design → build → deploy → maintain.
- When shipping software that must deliver user or business value, not just correct code.
- When coordinating across technical and product concerns to make architectural trade-offs.

## When Not to Use

- For implementing well-defined, isolated specs without system design concerns (use `coding`).
- For algorithmic or data-structure focused tasks without product context (use `programming`).
- For tasks that are purely about writing tests (use `tdd`) or debugging.

## Common Pitfalls

- **Skipping Requirements Clarity**: Building the wrong feature because user needs were not validated.
- **Ignoring Operations**: Delivering code that works locally but fails in production due to missing monitoring, logging, or deployment considerations.
- **Stakeholder Silence**: Making technical decisions in isolation that conflict with product priorities or timelines.
- **Rollout Neglect**: Shipping without a rollback plan, feature flags, or incremental rollout strategy.

## Core Process

1. **Understand Requirements**: Analyze the user or business need. Clarify scope, priorities, and success criteria with stakeholders.
2. **Architecture & Design**: Choose technical approaches considering scalability, maintainability, and fit with existing systems.
3. **Implementation Strategy**: Break down the feature into small, independently shippable increments.
4. **Build & Integrate**: Write clean, production-grade code. Integrate with existing systems safely.
5. **Testing & Quality**: Ensure comprehensive test coverage, CI/CD pipeline validation, and security review.
6. **Deployment & Release**: Handle rollout, feature flags, and monitoring setup. Plan for rollback if needed.
7. **Post-Release Iteration**: Monitor production metrics, gather feedback, and plan follow-up improvements.

## Core Principles

- **End-to-End Ownership**: Take responsibility from idea to production and beyond.
- **Product-First Thinking**: Understand *why* a feature exists and how it creates value for users.
- **Incremental Delivery**: Ship small, verifiable increments rather than large batches.
- **Operational Awareness**: Design for observability, deployability, and recoverability from day one.
- **Stakeholder Communication**: Keep relevant parties informed about progress, trade-offs, and risks.

## What to Avoid

- **Requirements Bypass**: Implementing without validating understanding of the user need.
- **Rollout Neglect**: Shipping without rollback planning, feature flags, or gradual exposure.
- **Operational Blindness**: Delivering code without logging, metrics, or error handling for production.
- **Scope Creep**: Adding unrequested features that delay delivery of the core value.
- **Pattern Invention**: Ignoring existing architectural conventions in favor of personal preference.

## Related Skills

- **tdd**:
  You MUST load this skill when practice Test-Driven Development for reliability and regression prevention.
