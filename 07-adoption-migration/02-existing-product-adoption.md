# Existing Product Adoption Playbook

## Objective

Introduce PEOF into an operating product while preserving valuable work and minimizing disruption.

## Phase 1 — Permission and read-only baseline

Confirm scope, repository/system access, protected areas, stakeholders, active releases, and approval authority. Begin with read-only inspection.

**Outputs:** scope agreement, asset inventory, product profile draft, evidence log.

## Phase 2 — Current-state assessment

Review product strategy, requirements, design, architecture, code practices, testing, security, CI/CD, operations, governance, and team workflow. Compare documentation with actual behavior where possible.

**Outputs:** maturity assessment, strengths to preserve, risks, gaps, conflicting artifacts, unknowns.

## Phase 3 — Target-state design

Select the minimum useful framework components. Define decision rights, lifecycle gates, required artifacts, quality controls, Claude Code configuration (if wanted), and product-specific rules.

**Outputs:** target operating model, artifact mapping, adoption backlog, migration plan.

## Phase 4 — Pilot

Pilot with one low-to-moderate-risk feature group or workflow. Avoid using a production-critical change as the first experiment unless necessary and properly controlled.

**Outputs:** pilot plan, feedback, measured friction, revised templates and workflow.

## Phase 5 — Incremental adoption

Prioritize high-value gaps. Adopt practices in coherent packages (for example, requirements traceability plus acceptance testing, or release checklist plus rollback validation). Preserve existing effective practices until replacements are proven.

**Outputs:** adopted practices, updated documentation, training/enablement, change log.

## Phase 6 — Validate and stabilize

Check adoption, traceability, quality, team friction, and whether the new process is actually being used. Remove redundant artifacts and process steps.

**Outputs:** validation report, updated maturity baseline, unresolved risks, stabilization actions.

## Existing agentic assets

As part of the read-only inventory, identify existing skills, agents/subagents, reusable prompts, hooks, evaluation sets, and optimizer tooling. Record canonical paths, owners where known, versions/hashes, permissions, dependencies, data access, active usage, test evidence, and known limitations. Classify each asset as retain, improve, consolidate, replace, archive, or retire. Do not assume that a skill is safe or effective merely because it is already in use. Establish a baseline and representative evaluation before making behavior-changing updates.

When migrating assets, preserve the prior version and provenance. Avoid changing multiple unrelated skills in one unreviewable batch. Pilot the lifecycle and evaluation process with a low-risk asset first.

## Existing-product safeguards

- No rewrite by default.
- No bulk rename, deletion, or reorganization without explicit approval.
- Keep the current production workflow working during transition.
- Maintain backward compatibility where required.
- Identify source-of-truth documents before consolidating.
- Preserve history for important decisions.
- Do not migrate stale or contradicted content without reconciliation.
- Treat customer data and production credentials as sensitive.
