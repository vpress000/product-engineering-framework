# SkillOpt and Agentic Workload Budgeting

## Purpose

Prevent the Agentic Engineering and Microsoft SkillOpt workflows from unexpectedly consuming a large share of the developer's Claude subscription allowance.

## 1. Treat model-backed evaluation as a usage-intensive workload

A SkillOpt optimization cycle can involve multiple candidate generations, task executions, model calls, replays, and evaluations. A research engine experiment or SkillOpt-Sleep run can therefore consume meaningful account capacity, even if the SkillOpt source repository is installed locally.

Local installation does not make model-backed execution free. Mock backends can validate wiring and schemas but do not prove real-model skill quality.

## 2. Required pre-run budget brief

Before a model-backed experiment, define:

- Objective and skill under test.
- Baseline skill version/hash.
- Candidate generation approach.
- Task manifest and dataset split.
- Backend and model configuration.
- Maximum task count for the pilot.
- Maximum candidate/optimization iterations.
- Maximum parallel workers.
- Whether repository build/test commands may run.
- Expected provider/subscription usage risk.
- Stop conditions and human approval point.

The limits are operational guardrails, not guarantees of a precise subscription quota amount.

## 3. Quota-conscious experiment sequence

1. Run static lint/schema/frontmatter checks locally.
2. Validate adapter and environment behavior with deterministic or mock tests.
3. Run a very small model-backed pilot on one low-risk skill.
4. Review quality, failure cases, and observed usage before expanding.
5. Increase task count or iterations only when results justify it.
6. Keep validation and held-out task sets separate from optimizer exposure.
7. Stop when the candidate fails a critical quality/safety criterion or improvement evidence is inconclusive.

## 4. One skill at a time by default

Do not run multi-skill fan-out, broad nightly loops, or continuous optimization by default. Optimize one skill at a time until the execution cost, repeatability, and evaluation value are understood.

## 5. Avoid unnecessary parallelism

Limit concurrent model-backed evaluations. More workers may shorten elapsed time but can use the shared account allowance faster. Select concurrency based on demonstrated benefit and available capacity, not because a tool exposes a parallel option.

## 6. Approval and stop conditions

Require human approval before:

- Starting a real-model experiment with non-trivial expected usage.
- Enabling scheduled or recurring model-backed runs.
- Increasing iteration, dataset, or worker limits.
- Sending session-derived or product data to an external provider.
- Adopting a candidate skill into the active project.

Never automatically enable paid usage credits or API billing to finish an experiment.

## Related documents

- [`../12-skillopt-integration/03-research-engine-training-and-evaluation.md`](../12-skillopt-integration/03-research-engine-training-and-evaluation.md)
- [`../12-skillopt-integration/04-skillopt-sleep-usage-learning.md`](../12-skillopt-integration/04-skillopt-sleep-usage-learning.md)
- [`../12-skillopt-integration/07-data-governance-security-and-cost.md`](../12-skillopt-integration/07-data-governance-security-and-cost.md)
- [`../09-templates/38-skillopt-run-budget-template.md`](../09-templates/38-skillopt-run-budget-template.md)
