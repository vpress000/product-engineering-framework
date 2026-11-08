# Controlled Skill Evolution

## Purpose

Improve skills through small, evidence-based edits while keeping the approved version stable until a candidate passes the required gates and receives approval.

## Accepted change types

- Add a missing instruction or decision rule.
- Modify an ambiguous or ineffective instruction.
- Remove a demonstrably redundant or harmful instruction.
- Consolidate duplicated guidance.

## SkillOpt as the optimization engine

PEOF v1.4 uses Microsoft's SkillOpt repository for automated optimization where appropriate. Its research engine applies trajectory-driven reflection and bounded text edits under a validation gate. SkillOpt-Sleep (preview) applies a usage-driven harvest/mine/replay/consolidate cycle and stages validated proposals. These workflows are distinct. The chosen engine, exact commit/version, model/backend, task set, and adapter must be recorded.

## Controlled procedure

1. Preserve the live baseline and content hash.
2. Define the failure hypothesis and target behavior.
3. Freeze a train/validation/test task manifest and exposure ledger.
4. Generate a candidate through SkillOpt or a documented manual workflow.
5. Limit edits to the agreed scope; protect metadata, safety, permissions, and owner-maintained blocks.
6. Validate format, links, instructions, scope, tool permissions, and security boundaries.
7. Evaluate baseline and candidate using the same validation conditions.
8. Reject candidates that fail the gate, violate a safety veto, or lack sufficient evidence.
9. Use held-out test data only after candidate selection is complete; do not feed results back into the same optimization loop.
10. Stage the exact candidate and report for human review.
11. Adopt only after explicit approval and backup/hash verification.
12. Reevaluate if the model, provider, backend, adapter, project architecture, or relevant tool permissions change.

## No-regression policy

For high-impact skills, require both an aggregate improvement/threshold and no regressions on critical tasks. If the optimizer's default gate does not enforce per-task no-regression, use the relevant supported setting or an external PEOF veto check; verify exact config names and defaults for the pinned version. Do not claim PEOF's policy is enabled merely because SkillOpt is installed.

## Rejected candidate handling

Keep the report and rationale, but do not promote rejected content. A candidate may be revised and re-run only with a new run ID and preserved history. Do not reuse contaminated test tasks as pristine evidence.

## Human review is mandatory

The reviewer sees exact diff, task IDs, scores, failures, split exposure, run provenance, provider, permissions, cost, data boundary, compatibility impact, and rollback path. Automated adoption is disabled by PEOF policy unless separately risk-assessed and explicitly approved for a narrow scope.

## Related guidance

- [SkillOpt research engine](../12-skillopt-integration/03-research-engine-training-and-evaluation.md)
- [SkillOpt-Sleep](../12-skillopt-integration/04-skillopt-sleep-usage-learning.md)
- [Staging and adoption](../12-skillopt-integration/08-staging-adoption-and-multi-skill-governance.md)
