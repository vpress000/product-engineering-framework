# SkillOpt Project Operations Runbook

## Purpose

Provide a conservative, repeatable runbook for onboarding and operating SkillOpt against one product.

## Prerequisites

- Completed product profile and developer environment profile.
- Approved target skill and owner.
- Pinned SkillOpt source checkout and clean/recorded working tree.
- Confirmed Python/CLI/plugin versions.
- Selected workflow: research engine, Sleep, or both.
- Approved model/provider and data classification.
- Baseline skill hash and reviewable evaluation tasks.
- Project-specific adapter if repository execution is required.
- Isolated temporary workspace and safe test commands.
- Defined budget, retention, and rollback plan.

## Pilot sequence

### A. Verify source checkout

```bash
git -C <SKILLOPT_PATH> status --short
git -C <SKILLOPT_PATH> rev-parse HEAD
python -m skillopt_sleep --help
python <SKILLOPT_PATH>/scripts/train.py --help
python <SKILLOPT_PATH>/scripts/eval_only.py --help
```

Run commands from the appropriate Python environment and verify their paths. The exact module and entry-point availability depends on the installed source revision.

### B. Prove non-provider plumbing

```bash
skillopt-sleep status --project <PRODUCT_PATH>
skillopt-sleep dry-run --project <PRODUCT_PATH> --source claude --backend mock
```

Use the current CLI's `--help` to confirm syntax. The mock backend is useful for control-flow testing, not model-quality evidence.

### C. Inspect source-derived tasks

Harvest or dry-run the intended project/source. Review counts, task quality, duplicates, attribution, privacy, and relevance. If using a real backend, use the documented reviewed-task-file workflow where available. Explicitly name the target skill path.

### D. Small real-backend pilot

Use one low-risk skill, a small number of sessions/tasks, a low cost budget, and a provider approved for the content. Review the CLI output and diagnostics to confirm the actual isolation mode. Do not schedule the run yet.

### E. Repository benchmark pilot

For code-writing or repository-aware tasks, use the project benchmark adapter with a clean pinned snapshot and disposable worktree. Prove reset, shell allowlist, test execution, hidden checks, trajectory persistence, score calculation, and cleanup before training.

### F. Review and adoption

Inspect staged proposal, baseline/candidate diff, reports, per-task results, split exposure, provider/backend, cost, and all skipped/failing tasks. Use the adoption template. Adopt only the explicitly approved path(s), verify backup and hashes, run smoke checks, and document rollback target.

## Routine commands

The SkillOpt-Sleep documentation currently describes actions such as `status`, `dry-run`, `harvest`, `run`, `adopt`, `schedule`, `unschedule`, and `evalkit`. Use `--help` from the pinned checkout to confirm exact syntax and flags. Do not paste an old command from this file if the installed version reports a different interface.

## Scheduling gate

Scheduling is disabled until all of the following are true:

- at least three successful manual cycles have been reviewed;
- harvested tasks are relevant and clean;
- backend isolation and provider handling are verified;
- configured source, backend, model, project, and target paths persist in the scheduler environment;
- task, token/cost, and retention budgets are approved;
- failed schedule runs are observable;
- a documented disable/unschedule process has been tested.

Auto-adoption remains disabled.

## Stop and escalation conditions

Stop the run if it discovers unexpected projects/sessions, accesses unauthorized files, encounters a credential, sends unreviewed sensitive content externally, changes live files, uses an unexpected backend/isolation mode, exceeds budget controls, leaves a worktree behind, or cannot produce a trustworthy report.

## Handoff report

Record the run ID, action, project, skill target, SkillOpt commit, CLI version, source/backend, model/provider identifier, isolation level, task counts, manifest hash, costs, output/staging path, gate result, skipped failures, approval, and next action.
