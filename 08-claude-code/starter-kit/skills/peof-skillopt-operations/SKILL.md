---
name: peof-skillopt-operations
description: Use when setting up, inspecting, running, evaluating, reviewing, upgrading, or adopting Microsoft SkillOpt or SkillOpt-Sleep for a PEOF-managed project. Do not use to modify live skills without explicit approval.
---

# PEOF SkillOpt Operations

## Mission

Operate the project's approved Microsoft SkillOpt integration under PEOF governance. The SkillOpt source checkout and exact version must be identified before running commands.

## Required sequence

1. Read `12-skillopt-integration/01-integration-architecture.md` and the relevant workflow guide.
2. Inspect the integration profile, project profile, developer environment profile, SkillOpt remote/commit, current CLI `--help`, and current working-tree state.
3. Determine whether the request concerns the research engine, SkillOpt-Sleep, or both. Never conflate their configurations or assume they share runtime dependencies.
4. Verify the target skill path explicitly. For Sleep, do not assume `--project` selects the intended skill; use the documented `--target-skill-path` option when applicable.
5. Check source/backend separation, repository access, isolation level, privacy classification, provider, cost budget, and task split/exposure.
6. For a first run, use a mock/dry-run path to inspect flow. A mock result is not a quality result. Before real provider calls, inspect and approve transcript-derived tasks.
7. For repository-level coding tasks, use the approved project benchmark adapter and a disposable worktree. Do not assume Sleep's project scope means the model can read or modify repository files.
8. Run only documented commands supported by the pinned checkout. Do not invent flags or silently replace a failed command with manual edits.
9. Keep all candidate files in staging. Review baseline/candidate diffs, task-level results, report, diagnostics, hash, and failures.
10. Never use auto-adoption unless the user explicitly approves that exact mode. PEOF default is manual adoption only.
11. Before adoption, verify the live baseline still matches, create a backup, obtain approval for exact paths, write a receipt, and run post-adoption checks.
12. Report actual results, limitations, cost, provider/data boundary, and rollback location.

## Hard stop conditions

Stop if the SkillOpt commit is unknown, current CLI syntax is unverified, project/target scope is ambiguous, a sensitive transcript may be transmitted without review, backend isolation is unknown, task splits are contaminated, a live file changed unexpectedly, the gate is disabled without approval, or staging/adoption hashes do not match.

## Output contract

Return a concise run summary with: workflow, project, skill, source/backend, SkillOpt commit/version, isolation, task counts, baseline/candidate scores, gate outcome, errors/skips, cost/tokens where available, staging path, approval state, and rollback reference.


## Subscription usage guardrail

Before a model-backed research or Sleep run, prepare a small run budget using `09-templates/38-skillopt-run-budget-template.md`. Start with local static checks and deterministic/mock validation, then a small approved real-model pilot. Cap tasks, candidate versions, iterations, and concurrent workers. Do not assume a new Claude Code session resets the shared subscription allowance. Do not enable usage credits or API billing without explicit account-owner approval.
