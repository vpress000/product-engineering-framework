---
name: peof-feature-grouping
description: Decompose a product backlog or requirements set into coherent feature implementation groups using dependencies, shared functionality, complexity, risk, and collective validation. Use when preparing implementation packages or a feature-group matrix.
---

# Feature Grouping Workflow

1. Identify the source-of-truth backlog, SRS, PRD, and technical context.
2. Inventory candidate features and stable identifiers.
3. Map user outcomes, shared journeys, data, APIs, components, dependencies, and acceptance evidence.
4. Assess complexity, uncertainty, risk, integration coupling, and deployment constraints.
5. Form logical groups where coordinated work reduces repeated design, setup, implementation, or integration effort.
6. Keep unrelated work separate and identify safe parallel work.
7. Define group boundaries, included/excluded features, predecessor groups, owner, outcome, shared assets, acceptance criteria, test strategy, and rollout/rollback notes.
8. Create a feature inventory and dependency matrix plus one group plan per package.
9. Flag quick wins, critical path, unknowns, and decisions requiring approval.

## Quality rules
- A group is a planning and validation unit, not a reason to create a giant branch or pull request.
- Run unit/component/integration checks continuously; perform collective group acceptance and relevant regression at the group boundary.
- Never invent dependencies or feature IDs. Mark uncertain relationships for confirmation.
- Do not reorder approved scope without identifying the trade-off and decision owner.

## Output
Provide a short summary table with group ID, name, included feature IDs, rationale, dependencies, complexity/risk, and validation boundary, followed by key assumptions and recommended sequence.
