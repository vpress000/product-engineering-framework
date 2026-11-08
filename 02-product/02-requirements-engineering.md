# Requirements Engineering

## Purpose

Translate product intent into a shared, testable understanding of what the system must do and the quality it must provide.

## Requirement types

- **Business/outcome requirements:** why the product or change exists.
- **User and stakeholder needs:** tasks, goals, constraints, and pain points.
- **Functional requirements:** observable system behavior.
- **Non-functional requirements (NFRs):** performance, reliability, security, privacy, accessibility, usability, compatibility, maintainability, and other quality attributes.
- **Constraints:** mandated technologies, integrations, policies, budgets, or operating conditions.
- **Transition requirements:** data migration, training, coexistence, cutover, and decommissioning needs.

## Quality criteria

A requirement should be clear, singular where practical, necessary, feasible, unambiguous, verifiable, traceable, and prioritized. Avoid implementation detail unless it is a genuine constraint or design decision.

## Requirements workflow

1. Identify stakeholder and user sources.
2. Capture needs and context.
3. Resolve terminology and scope boundaries.
4. Define functional behavior and exceptions.
5. Identify relevant NFRs with measurable targets where possible.
6. Define acceptance criteria and examples.
7. Prioritize and identify dependencies.
8. Review feasibility, risks, and testability.
9. Baseline the agreed scope for the next delivery increment.
10. Manage changes through impact analysis and approval.

## Acceptance criteria

Use observable outcomes. Examples include Given/When/Then scenarios, examples, state transitions, validation rules, permission boundaries, and failure behavior. Cover normal, edge, error, and security-relevant cases proportionate to risk.

## Traceability

For material requirements, maintain links:

`Product outcome → Requirement/story → Design/decision → Implementation item → Test/validation evidence → Release`

Traceability can live in an issue tracker or repository. Do not duplicate the same source of truth across documents.

## Change control

For a proposed change, identify the reason, affected requirements, users, architecture, estimates, dependencies, tests, release, cost, and risks. The product owner decides scope priority; technical and risk owners assess their respective impacts.

## SRS and PRD usage

A PRD explains user/business problem, outcomes, scope, and product behavior. An SRS provides a more structured, detailed, testable system requirement baseline. Use both only when their distinct purposes justify the overhead. Keep them linked and avoid copying content that will drift.
