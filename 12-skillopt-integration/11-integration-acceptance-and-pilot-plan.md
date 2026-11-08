# SkillOpt Integration Acceptance and Pilot Plan

## Purpose

Define the minimum proof required before PEOF declares the SkillOpt integration ready for a product.

## Pilot scope

Select one product, one low-risk skill, one task family, one approved provider/backend, and a small number of tasks. Record why this is the best pilot. Do not pilot every agent or skill at once.

## Acceptance gates

| Gate | Required evidence | Fail condition |
|---|---|---|
| Source provenance | Remote, commit/tag, clean/dirty state, CLI/package versions | Revision or source is unknown |
| Installation | Python environment and required CLI/plugin commands work | Wrong environment or missing dependency |
| Scope | Correct product and explicit skill target selected | Project/target ambiguous or wrong path |
| Privacy | Source reviewed, transcript tasks sanitized, provider approved | Sensitive data may be transmitted without authorization |
| Isolation | Documented capability probe and disposable workspace | Access broader than approved or isolation unknown |
| Baseline | Fixed skill hash, fixed task manifest, split/exposure ledger | No valid baseline or contaminated holdout |
| Reproducibility | Same config/model/snapshot can be rerun or differences recorded | Key run conditions unknown |
| Scoring | Independent checks, valid hard/soft scores, trajectory artifacts | Model self-score only or missing/invalid results |
| Candidate gate | Validation result and task-level regressions reviewed | Gate bypassed or evidence incomplete |
| Staging | Candidate separate from live file; hash/diff present | Live file changed before approval |
| Adoption | Explicit approval, backup, receipt, post-check | Approval/path/hash mismatch or rollback absent |
| Operations | Cost, retention, schedule/disable decisions recorded | Budget or data lifecycle unclear |

## Minimum pilot report

Include:

- objective and target skill;
- product snapshot and adapter version;
- SkillOpt commit and workflow (research or Sleep);
- source/backend/model/provider and isolation level;
- task manifest, split IDs, exposure status;
- baseline and candidate results;
- hard/soft task scores, task-level changes, uncertainty;
- failures, skips, timeouts, and evaluator issues;
- tokens/cost, duration, and any budget overrun;
- privacy/security review and staging path;
- recommendation: reject, revise, repeat, or approve for adoption.

## What passing means

Passing means this specific integration configuration completed the defined pilot checks. It does not prove SkillOpt will improve every skill, support all projects, or remain compatible with future versions. Limit the approval to the exact skill, benchmark, backend, project snapshot, SkillOpt commit, and adoption target tested.
