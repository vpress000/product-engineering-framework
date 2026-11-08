# Claude Code Skills and Agent Design

## Choose the simplest mechanism

- **Project instructions:** durable context and rules that apply broadly.
- **Scoped rules:** standards that apply only to certain paths or file types.
- **Skills:** repeatable procedures with clear inputs, steps, and outputs.
- **Agents:** bounded specialist tasks that benefit from independent context or focused analysis.
- **Hooks:** deterministic actions tied to tool/lifecycle events, only when reliable and safe.

Verify current supported syntax and behavior in official Claude Code documentation before implementation.

## Skill specification

Each skill should define:

- Name and purpose.
- When to use / when not to use.
- Required inputs and source-of-truth locations.
- Step-by-step workflow.
- Safety and approval boundaries.
- Expected outputs.
- Validation checklist.
- Escalation conditions.

Good candidates include product discovery, requirements review, SRS quality review, architecture assessment, feature grouping, implementation planning, test planning, code review, migration assessment, and release readiness.

## Agent specification

Each agent should define:

- Narrow role and objective.
- Explicit responsibilities and non-responsibilities.
- Required context and inputs.
- Analysis method.
- Output format.
- Tools/permissions required, minimized to the task.
- Human approval and escalation conditions.
- Validation expectations.

Potential roles include Product Analyst, Requirements Engineer, Software Architect, Implementation Planner, QA Engineer, Security Reviewer, Code Reviewer, and Release Engineer. Do not create all of them by default; select based on real workflow needs.

## Lifecycle, evaluation, and change control

Do not treat a skill or agent as complete when its Markdown file has been authored. Material reusable assets follow the lifecycle in [`../11-agentic-engineering/01-agent-and-skill-lifecycle.md`](../11-agentic-engineering/01-agent-and-skill-lifecycle.md): specify, design, build, baseline, evaluate, approve, publish, monitor, improve, and retire.

Use the design standards in [`../11-agentic-engineering/02-agent-and-skill-design-standards.md`](../11-agentic-engineering/02-agent-and-skill-design-standards.md). Define observable success criteria and evaluate behavior using [`../11-agentic-engineering/03-skill-evaluation-and-benchmarking.md`](../11-agentic-engineering/03-skill-evaluation-and-benchmarking.md). Usage-derived learning is optional and must follow the privacy and review controls in [`../11-agentic-engineering/04-usage-feedback-and-learning.md`](../11-agentic-engineering/04-usage-feedback-and-learning.md).

Any optimization proposal must be bounded, staged, evaluated, and approved before adoption. See [`../11-agentic-engineering/05-controlled-skill-evolution.md`](../11-agentic-engineering/05-controlled-skill-evolution.md) and [`../11-agentic-engineering/06-skill-versioning-adoption-and-rollback.md`](../11-agentic-engineering/06-skill-versioning-adoption-and-rollback.md).

## Avoid

- Agents with overlapping authority and no clear handoff.
- Skills that merely restate the same long instructions.
- Hooks that perform destructive actions without safeguards.
- Autonomous production changes or default automatic skill adoption.
- Treating agent output as verified evidence without checking it.
- Claiming a skill is improved based only on anecdotal success or a single run.
- Reusing optimization tasks as pristine held-out evaluation evidence.
