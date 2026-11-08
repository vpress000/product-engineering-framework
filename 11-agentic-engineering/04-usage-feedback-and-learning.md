# Usage Feedback and Learning

## Purpose

Convert recurring, approved agent-use evidence into reviewable improvements without turning raw session capture into uncontrolled surveillance or automatic prompt rewriting.

## Sources of evidence

- Explicit user feedback and corrections.
- Reviewed defect/incident patterns.
- Repeated failed or incomplete task outcomes.
- Approved coding-agent session summaries or harvested session-derived tasks.
- Evaluation reports and regression analysis.

Usage data should be collected only when there is a defined improvement question and approved data boundary.

## SkillOpt-Sleep integration

Microsoft SkillOpt-Sleep is the supported reference implementation for usage-driven session harvesting, recurring-task mining, replay, bounded consolidation, held-out validation, staging, and review. Microsoft documents it as a preview. Use the pinned source checkout and current docs; do not assume a moving `main` feature is present in an installed package.

The documented cycle is harvest → mine → replay → reflect/consolidate → held-out gate → stage → human adoption. Harvesting is local/read-only, but real backends may send truncated transcript excerpts and derived tasks to selected providers. Review/redact task records before real-provider replay. The `mock` backend makes no provider calls but does not prove model quality.

## Required workflow

1. Define the recurring problem and target skill.
2. Approve which local session sources and project scopes may be read.
3. Inspect harvest counts and filter irrelevant/automated sessions.
4. Review, minimize, and redact derived tasks.
5. Freeze the baseline skill and evaluation/split manifest.
6. Run a small controlled replay through an approved backend.
7. Review the proposed bounded edits and task-level gate results.
8. Stage candidate only; do not modify live skills.
9. Obtain explicit approval and adopt through PEOF versioning/rollback controls.
10. Monitor whether the change improves actual use and whether new regressions appear.

## Repository context warning

The Sleep `--project` parameter does not guarantee repository-aware replay. Source selection, replay backend, file/tool access, and workdir are separate. For genuine codebase tasks, use a tested project benchmark adapter or execution harness. Do not describe a textual replay as an end-to-end code evaluation.

## Feedback and consent

Define who may contribute feedback, what is collected, whether user/session content is stored, how long it is retained, whether a provider receives it, and how deletion requests are handled. Never infer consent from the fact that a transcript exists locally.

## Learning limits

Recurring patterns are hypotheses, not proof that an instruction is correct or that the same task should always be automated. Keep low-frequency but high-severity edge cases in a separate safety suite. Do not optimize away human review or user-specific intent.
