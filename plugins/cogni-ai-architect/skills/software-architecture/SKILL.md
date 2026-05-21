---
name: software-architecture
description: 'Expert-level workflow for software architecture design, covering styles (Monolith, Layered, Microservices, Event-Driven), SOLID principles, design patterns, quality attributes, and architectural decision records.'
license: MIT
---

# Software Architecture

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## When to Use

- When tasked with designing the high-level structure of a new software system.
- When determining the architectural style (e.g., Monolith, Microservices, Event-Driven) for an application.
- When addressing quality attributes such as scalability, maintainability, reliability, and performance.
- When applying SOLID principles and other foundational design principles (DRY, KISS, YAGNI, Law of Demeter).
- When defining or evaluating architectural trade-offs and creating Architecture Decision Records (ADRs).

## When Not to Use

- When implementing low-level coding tasks that do not involve structural or architectural decisions (use the `coding` skill instead).
- When debugging simple logic errors or writing unit tests (use the `programming` or `tdd` skill instead).
- When strictly writing documentation without making architectural choices (use `docs-writer` instead).

## Core Principles

- **Separation of Concerns**: Divide software based on distinct responsibilities to ensure modularity and loose coupling.
- **Trade-offs**: Understand that no architecture can optimize all quality attributes simultaneously. Improving one often degrades another.
- **Why over How**: Focus on the reasoning behind architectural decisions rather than just the implementation details.
- **Fitness Functions**: Use automated checks to ensure the architecture continues to meet its defined quality attributes over time.
- **Last Responsible Moment**: Delay architectural decisions until there is enough information to justify and validate them, avoiding analysis paralysis.

## Step-by-Step Workflows

### 1. Analyze Requirements and Constraints

- Identify the functional requirements of the proposed system.
- Extract and prioritize architectural characteristics (quality attributes/non-functional requirements) such as availability, fault tolerance, testability, and security.
- Identify business constraints, such as budget, time-to-market, or team size.

### 2. Determine Architectural Style

- Evaluate different architectural styles based on the prioritized quality attributes:
  - **Monolithic Architecture**: Suitable for small teams, rapid initial development, and simpler deployments, but limited in independent scalability.
  - **Layered (n-tier) Architecture**: Enforces separation of concerns (presentation, business, persistence, database), but can introduce latency and complexity.
  - **Microservices Architecture**: Enables independent deployment, scaling, and technology diversity, but introduces distributed complexity, data consistency challenges, and operational overhead.
  - **Event-Driven Architecture**: Decouples components for high scalability and real-time responsiveness, using publish-subscribe or event sourcing patterns.

### 3. Apply Design Principles

- **SOLID Principles**:
  - *Single Responsibility Principle (SRP)*: A class should have only one reason to change.
  - *Open-Closed Principle (OCP)*: Open for extension, closed for modification.
  - *Liskov Substitution Principle (LSP)*: Subtypes must be substitutable for their base types.
  - *Interface Segregation Principle (ISP)*: Favor many small, client-specific interfaces.
  - *Dependency Inversion Principle (DIP)*: Depend on abstractions, not concrete details.
- **Foundational Principles**: Apply DRY (Don't Repeat Yourself), KISS (Keep It Simple, Stupid), YAGNI (You Aren't Gonna Need It), and the Law of Demeter to minimize complexity and coupling.

### 4. Select Design Patterns

- **Creational Patterns**: Use patterns like Singleton, Factory Method, Abstract Factory, Builder, or Prototype to handle object instantiation flexibly.
- **Structural Patterns**: Apply patterns to compose classes and objects into larger structures while keeping them flexible and efficient.
- **Behavioral Patterns**: Define clear communication and assignment of responsibilities between objects.

### 5. Document Architectural Decisions

- Provide both technical and business justifications for architectural choices.
- Record decisions in an Architecture Decision Record (ADR), capturing the context, problem, considered alternatives, the selected decision, and its consequences.
- Ensure the decision rationale is easily accessible to all stakeholders to prevent repeated discussions.

## Common Pitfalls

- **Premature Decomposition**: Breaking a system into microservices too early before domain boundaries are clear, leading to high operational overhead and tight coupling. Start with a modular monolith if unsure.
- **Ignoring Trade-offs**: Selecting an architecture without acknowledging the negative impact on other quality attributes (e.g., choosing microservices for a small app without accounting for distributed complexity).
- **Over-Abstraction**: Applying design patterns or principles (like DRY) excessively, resulting in rigid, hard-to-understand code.
- **Analysis Paralysis**: Delaying decisions for too long out of fear of making the wrong choice. Make decisions at the last responsible moment, and adapt based on feedback.
- **Undocumented Decisions**: Failing to record architectural decisions and their rationales, leading to lost knowledge and recurring debates.

## What to Avoid

- Do not use email or informal channels as the primary record for architectural decisions. Always maintain a centralized ADR repository.
- Avoid tight coupling between high-level policy and low-level details. Always depend on abstractions.
- Avoid introducing intermediate layers that perform minimal processing without adding significant value in layered architectures.

## Related Skills

- **development**:
  Load this skill when handling the full-cycle software development workflow from requirements to deployment.
- **programming**:
  Load this skill when solving technical problems with code, algorithm design, and code craftsmanship.
- **critical-thinking**:
  Load this skill when deconstructing assumptions and performing adversarial red-teaming to validate architectural plans.
