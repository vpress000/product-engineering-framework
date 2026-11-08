# SkillOpt Research Engine: Training and Evaluation Workflow

## Purpose

Use the SkillOpt research engine for reproducible, task-based optimization of reusable skill documents. This is the preferred route when PEOF needs controlled benchmarks, explicit task splits, repeatable rollouts, and a measurable comparison between skill versions.

## Core loop

The documented research-engine pattern is:

```text
Task rollout by target agent
  → trajectory capture
  → optimizer reflection / edit proposal
  → bounded edit selection and application
  → validation gate
  → repeat across configured epochs
  → evaluate the selected skill on the appropriate held-out split
```

The skill document is the optimized artifact; the model weights are not trained by this process. The optimizer role and target role are configured separately and may use different backends.

## When to use the research engine

Use it when:

- a skill has a stable, repeated job that can be evaluated with explicit tasks;
- success criteria can be expressed through deterministic checks, structured scoring, or a documented rubric;
- a representative task set can be split without leaking solutions;
- baseline and candidate versions can be tested under the same conditions;
- the team can record model/provider, config, source revision, seed, and environment.

Do not optimize a skill solely because it exists. First establish a real recurring problem and decide whether improvement is worth its cost and maintenance.

## Benchmark/task-set governance

Create distinct, versioned data splits:

- **Train:** may be used repeatedly for skill refinement.
- **Validation:** may be used for candidate selection and gate decisions.
- **Test / held-out:** is reserved for final measurement and must not be used to author, tune, or select the candidate.

Maintain an exposure ledger by task ID, source, split, run, and whether the target or optimizer saw the task or expected outcome. A task ceases to be pristine test data once exposed to a model, optimizer, human author, or skill-editing decision.

For project tasks, use fixed repository snapshots and no hidden test leakage. Keep expected fixes, test assertions, judge rubrics, and reference outputs outside the prompt where possible. Use an independent evaluator.

## Scoring

SkillOpt's benchmark adapter contract distinguishes hard and soft scores. Follow the checked-out repository's current contract. In the documented pattern, hard is a binary or suitably normalized task outcome, while soft is a bounded quality signal. Score the task in the environment adapter; do not rely only on a model judge when deterministic checks are available.

For software tasks, separate at least:

- correctness: tests and observable behavior;
- completeness: required acceptance criteria;
- safety: forbidden changes/actions and security checks;
- maintainability: static checks and reviewer rubric;
- efficiency: runtime, token usage, and human rework where available.

Do not collapse severe safety failures into a compensable average score. Define veto conditions that fail the candidate regardless of other scores.

## Reproducible execution

For each experiment, freeze and record:

- SkillOpt exact commit and package/CLI versions;
- task manifest, data snapshot, and split hashes;
- baseline skill content hash;
- target model/provider/deployment and optimizer model/provider;
- backend role selection and relevant configuration;
- task adapter revision and product commit;
- random seeds, retry/timeouts, environment variables by name (not secret values);
- token/cost budget, observed usage, duration, and run artifacts.

The SkillOpt docs show training and standalone evaluation entry points. Use the checked-out repository's CLI help and config reference rather than copying stale command flags. A source checkout may contain newer backends or adapters than the published package.

## Evaluation and statistics

Use a separate evaluation run against the selected skill and held-out split. For paired A/B comparisons, keep tasks and conditions fixed. SkillOpt-Sleep's `evalkit` is a separate Sleep utility documented to compare two conditions using McNemar and bootstrap confidence intervals; do not confuse it with the research engine's own evaluation CLI. Use the tool appropriate to the workflow and verify its exact interface from `--help`.

Report effect size, uncertainty, task-level wins/losses, failures, and practical significance. A statistically significant difference does not establish safety, representativeness, or performance on tasks outside the benchmark.

## Project-specific benchmark requirement

Built-in SkillOpt benchmarks do not automatically represent a particular product. If the goal is to improve implementation, debugging, repository analysis, or test-authoring skills for a product, create or maintain a project-specific benchmark adapter. See [`05-project-aware-benchmark-adapter.md`](05-project-aware-benchmark-adapter.md).

## Output and approval

Keep SkillOpt's experiment outputs outside production skill locations. Review `best_skill.md` or the candidate skill, run history, configuration, task-level artifacts, and evaluation report. Copy the exact candidate into PEOF staging only after verifying its hash and provenance. Adoption follows [`../11-agentic-engineering/06-skill-versioning-adoption-and-rollback.md`](../11-agentic-engineering/06-skill-versioning-adoption-and-rollback.md).

## Stop conditions

Stop and report rather than promote if task splits are contaminated, scoring is not reproducible, the optimizer/target config is ambiguous, a backend silently fails, evaluation tasks are missing, the baseline changed, or cost/privacy controls are insufficient.

## Sources

- [SkillOpt overview and workflow](https://microsoft.github.io/SkillOpt/docs/)
- [First experiment and backend guide](https://microsoft.github.io/SkillOpt/docs/guideline.html)
- [New benchmark guide](https://github.com/microsoft/SkillOpt/blob/main/docs/guide/new-benchmark.md)
- [CLI reference](https://github.com/microsoft/SkillOpt/blob/main/docs/reference/cli.md)
