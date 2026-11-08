# Skill Evaluation and Benchmarking

## Purpose

Establish evidence that a skill improves task outcomes without unacceptable regressions, cost, or safety impact. PEOF v1.4 uses Microsoft's SkillOpt repository as the supported optimization/evaluation implementation where automated skill optimization is appropriate.

## Evaluation layers

| Layer | Question | Example evidence |
|---|---|---|
| Static validation | Is the asset structurally valid and internally consistent? | Frontmatter/schema, links, references, lint, permissions review |
| Behavioral evaluation | Does the skill complete representative tasks? | Fixed task manifest, deterministic checks, rubric, SkillOpt rollouts |
| Repository evaluation | Does it work against the real product snapshot and tools? | Project benchmark adapter, isolated worktree, tests/build/static checks |
| Operational monitoring | Does it remain useful in real usage? | Approved user feedback, incidents, task quality, latency/cost |

## SkillOpt workflow selection

Use the **research engine** for explicit benchmark-based training/evaluation and the **SkillOpt-Sleep preview** for usage-derived recurring-task learning. They are separate workflows with separate entry points and configuration. Do not assume that a research run also harvested sessions or that a Sleep run exercised the same project benchmark.

See [`../12-skillopt-integration/03-research-engine-training-and-evaluation.md`](../12-skillopt-integration/03-research-engine-training-and-evaluation.md), [`../12-skillopt-integration/04-skillopt-sleep-usage-learning.md`](../12-skillopt-integration/04-skillopt-sleep-usage-learning.md), and [`../12-skillopt-integration/05-project-aware-benchmark-adapter.md`](../12-skillopt-integration/05-project-aware-benchmark-adapter.md).

## Benchmark split rules

Create distinct train, validation, and final held-out test groups. Track task IDs, sources, near-duplicate families, exposure, model/optimizer visibility, and whether a human used expected outcomes to edit the skill. A task that has influenced optimization or selection is not pristine test data. Rotate contaminated test tasks and preserve an exposure ledger.

## Project task requirements

For software engineering skills, use a fixed repository commit and isolated task workspace. The evaluator—not the target agent—must determine correctness wherever possible. Keep hidden tests and reference patches out of the prompt. Capture the trajectory/interaction needed by the selected SkillOpt adapter's reflection contract. A Git worktree isolates changes at the version-control level but is not by itself a security sandbox.

## Metrics and vetoes

Measure task success, requirement/acceptance coverage, correctness, completeness, safety, regressions, reliability, time, token/cost, and reviewer rework. Define the score and denominator before the run. Keep severe security/privacy/permission violations as veto failures rather than allowing them to be averaged away.

SkillOpt benchmark adapters use the pinned repository's scoring contract (commonly hard and soft task signals). Do not invent an API or adapter method; follow the checked-out `_template`, docs, and CLI. Use deterministic checks where available and model/human rubrics as supplementary signals.

## Paired comparisons and uncertainty

Compare baseline and candidate on the same valid task set and conditions. SkillOpt-Sleep documents an `evalkit` for paired A/B comparisons with McNemar and bootstrap confidence intervals; verify its exact interface from the installed version. Statistical evidence must be reported with task-level results and uncertainty. A gain on a small held-out sample is run-specific evidence, not a guarantee of broad generalization.

## Required report

Record objective, baseline/candidate hashes, SkillOpt commit/version, adapter, model/provider, task manifest/split hashes, exposure, hard/soft results, per-task wins/losses, failures/skips/timeouts, no-regression result, cost/latency, isolation level, privacy approval, limitations, and recommendation.
