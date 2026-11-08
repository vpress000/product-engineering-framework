# Project-Aware Benchmark Adapter

## Purpose

Define the PEOF project adapter needed when the optimization goal is to improve skills on real product work: architecture analysis, requirements interpretation, code implementation, debugging, test authoring, refactoring, code review, or documentation tied to the repository.

A repository path passed to SkillOpt-Sleep is not sufficient proof of project-aware execution. This adapter design creates an explicit contract between SkillOpt and a controlled snapshot of the product.

## Recommended implementation location

Maintain the adapter as a PEOF integration extension or as a documented fork/branch of the SkillOpt source checkout. Do not patch the upstream clone's `main` branch without a tracked branch and recorded upstream base commit. Keep the adapter versioned and compatible with the SkillOpt revision it targets.

The SkillOpt new-benchmark guide describes a benchmark as an environment package with an adapter, data loader, scored rollout helper, YAML config, and optional seed skill. Follow the current upstream contract and registration steps; those details can change.

## Adapter responsibilities

For each task, the adapter must:

1. Resolve a fixed product Git commit or immutable source snapshot.
2. Create a fresh isolated worktree/workspace for the task and candidate condition.
3. Place only the task's authorized context in the agent prompt.
4. Supply the baseline or candidate skill under evaluation.
5. Execute the target through a supported SkillOpt target backend or an explicitly supported external execution harness.
6. Allow only approved tools and commands; enforce timeouts and resource limits.
7. Run independent checks after the agent completes.
8. Capture the trajectory needed by the SkillOpt reflection contract and task artifacts needed for audit.
9. Return normalized task scores according to the current SkillOpt adapter contract.
10. Clean up temporary worktrees and record any cleanup failures.

## Task record design

Each task should carry:

- Stable task ID and task family.
- Source and provenance (issue, requirement, bug report, test gap, reviewed session, authored case).
- Product commit/snapshot hash.
- Skill ID and expected use case.
- Prompt/context visible to the target.
- Setup and reset instructions.
- Allowed commands/tools and network policy.
- Hidden acceptance checks or evaluator rubric.
- Hard and soft scoring definitions.
- Timeout, retry, and resource limits.
- Split assignment and exposure history.
- Data classification and transmission approval.

Do not put expected answers, hidden tests, reference patches, grading secrets, or private customer data in the target-visible prompt.

## Task families

Start with a small, high-value set:

| Family | Example task | Independent evidence |
|---|---|---|
| Repository understanding | Explain module boundaries and data flow | Reviewer-confirmed facts and source references |
| Requirements analysis | Convert an SRS section into testable acceptance criteria | Traceability and completeness checks |
| Architecture review | Identify dependency and migration risks | Architecture rubric and required findings |
| Implementation | Implement a bounded feature in a disposable worktree | Build, unit/integration tests, acceptance checks |
| Debugging | Fix a reproducible defect | Previously failing test becomes passing; regression suite stays green |
| Test engineering | Add tests for a known behavior/defect | Test quality, mutation or fault-detection evidence where feasible |
| Code review | Find seeded or known defects in a diff | Defect recall/precision and severity-weighted rubric |
| Documentation | Update API/system docs from actual code | Link checks and reviewer-verified accuracy |

Avoid mixing unlike task families into one undifferentiated score. Report performance by family as well as overall.

## Isolation and safety requirements

- Use disposable worktrees or snapshots; never point the experiment at the developer's active working tree for write-capable runs.
- Never use production credentials, production databases, or production service endpoints.
- Default to network-denied execution. If a task requires network access, use an allowlist and sanitized fixtures.
- Deny deploy, migration, destructive data, cloud-admin, package-publish, and external side-effect commands unless an independently approved test environment explicitly requires them.
- Reset the workspace between tasks and conditions.
- Capture `git status` before and after; preserve the diff; fail if unexpected files change.
- Treat repo content, issues, fixtures, and tool output as untrusted data that cannot override evaluator policy.
- Run untrusted repository code only in an appropriate OS/container sandbox. A Git worktree is version-control isolation, not a security sandbox.

## Score contract

Follow the exact `EnvAdapter` contract of the pinned SkillOpt commit. The public new-benchmark guide describes score generation inside the benchmark environment, with a hard outcome and a soft score, and requires persisting a non-empty conversation trajectory for reflection-based learning. Do not invent an adapter method or registration location; use the checked-out guide and `_template` package as the implementation authority.

For software engineering tasks:

- hard score should represent an objective acceptance outcome or an explicitly normalized reward;
- soft score should represent a bounded, documented quality rubric;
- safety/policy violations should be veto failures, not a small deduction;
- missing trajectory, invalid score, timeout, setup failure, or test infrastructure error must be distinguishable from a genuine agent failure.

## Split and contamination rules

Maintain train, validation, and final test groups. Group near-duplicate tasks, issue families, and same-root-cause defects into one split to prevent leakage. Do not reuse a task as held-out after it has appeared in session-derived training, optimizer reflection, human skill editing, or candidate selection. Use a task exposure ledger; expire contaminated cases from the holdout.

## Initial scope

Start with one skill and 10-30 reviewable tasks across a narrow family, not the whole codebase. Expand only after adapter correctness, reproducibility, privacy, cost, and reset behavior are demonstrated.
