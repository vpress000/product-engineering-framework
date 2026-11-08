# Existing Product Modernization Playbook

## Objective

Improve a live product's architecture, reliability, security, performance, developer experience, or delivery flow while protecting users and business continuity.

## Stage 1 — Define the modernization case

State the business problem, desired outcomes, affected users, non-goals, risk tolerance, constraints, sponsor, and decision authority. Separate symptoms from root-cause hypotheses.

**Outputs:** modernization brief, baseline measures, initial risk and dependency view.

## Stage 2 — Establish the as-is baseline

Inspect runtime behavior, architecture, code, data flows, dependencies, deployment, tests, support history, cost, and operational metrics with read-only access first. Record verified facts, user-stated information, inferences, and unknowns separately.

**Outputs:** current-state architecture, technical debt inventory, compatibility map, evidence and gaps.

## Stage 3 — Define target states and options

Describe the target capability at an appropriate level. Compare incremental refactoring, component extraction, platform replacement, vendor change, rehosting, rewrite, or no change. Evaluate total cost, delivery risk, reversibility, migration complexity, and operating burden.

**Outputs:** options analysis, target-state view, ADRs, migration principles.

## Stage 4 — Plan safe migration slices

Sequence work by dependency, risk reduction, user value, and ability to validate. Define compatibility boundaries, data migration, coexistence, feature flags, telemetry, rollback/forward recovery, and exit criteria for each slice.

**Outputs:** migration waves, implementation groups, test/validation plan, communications.

## Stage 5 — Pilot and prove

Choose a bounded slice. Validate performance, correctness, security, operational readiness, support impact, and team workflow. Compare results with the baseline and revise the plan.

**Outputs:** pilot evidence, updated estimates and risks, decision to scale/revise/stop.

## Stage 6 — Migrate incrementally

Deliver in small integrated increments. Maintain backward compatibility where required. Reconcile data and contracts, monitor both old and new paths, and retain a tested recovery option until confidence is sufficient.

**Outputs:** accepted migration slices, test evidence, updated architecture and runbooks.

## Stage 7 — Retire old components safely

Confirm no remaining consumers, jobs, integrations, data obligations, or support dependencies. Communicate end of support, archive required information, remove access safely, and shut down in a controlled order.

**Outputs:** decommission evidence, updated inventory, final risk disposition.

## Modernization guardrails

No rewrite by default. No destructive migration without explicit approval. Protect production data. Do not assume rollback is possible after irreversible data changes. Keep users informed when behavior, availability, contracts, or support are affected.
