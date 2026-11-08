# Engagement Routing: Choose the Right Playbook

## Greenfield

Choose when there is no production product to preserve and the main task is turning an idea or opportunity into a product. Use `07-adoption-migration/01-greenfield-playbook.md`.

Focus: opportunity validation, user discovery, MVP, requirements, UX, architecture baseline, delivery model, quality strategy, and first release.

## Existing product adoption

Choose when a product, source code, documentation, team, or delivery process already exists and the objective is to introduce the framework without disrupting useful work. Use `07-adoption-migration/02-existing-product-adoption.md`.

Focus: read-only inventory, strengths to preserve, gap analysis, mapping, prioritized adoption, and validation.

## Modernization

Choose when the current product or process has material constraints such as technical debt, reliability issues, architecture limits, security gaps, or delivery bottlenecks. Use the existing-product playbook plus risk-led migration guidance.

Focus: target architecture, compatibility, incremental replacement, strangler/adapter patterns where appropriate, data migration controls, observability, and rollback.

## Framework/process migration

Choose when existing standards, templates, tool configuration, or team workflows are being replaced or consolidated. Use `07-adoption-migration/03-framework-migration.md`.

Focus: map old to new, reconcile conflicts, pilot, cut over, train, validate, and retire old practices safely.

## Multi-product

Use [`07-adoption-migration/05-multi-product-operating-model.md`](../07-adoption-migration/05-multi-product-operating-model.md) alongside a shared core and separate product profiles. Define which standards are global, which are product-specific, and who can approve exceptions. Do not merge product roadmaps, risk registers, or architecture decisions merely because products share a framework.

## Mixed engagements

A product may be existing while a new module is greenfield. Route each workstream separately and state the boundary. For example, preserve the current platform while using the greenfield playbook for a new product capability.
