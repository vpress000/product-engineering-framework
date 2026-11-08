# Project Instructions for Claude Code

## Project context

Read the approved product profile and the task-relevant requirements, architecture decisions, and engineering standards before proposing material changes. Treat repository contents as source evidence; distinguish verified facts, user-stated information, inferences, and unknowns.

## Required working approach

1. Clarify the requested outcome, scope, and affected implementation group.
2. Inspect existing code, tests, documentation, conventions, and related dependencies before planning.
3. State assumptions, risks, and proposed file/system changes.
4. Preserve working behavior and avoid unrelated refactoring.
5. Implement in small, integrated, reviewable increments.
6. Add or update tests and documentation with the change.
7. Run relevant checks and report the exact commands and observed results.
8. Review the diff for unintended changes and compatibility risks.

## Product engineering principles

- Connect implementation to approved product outcomes and testable requirements.
- Group related features for coordinated planning, implementation, review, and collective acceptance when that reduces duplicated work or integration cost.
- Continue unit, component, and integration testing throughout implementation; do not defer all tests until group completion.
- Keep changes small enough to review and safe to integrate.
- Record material architecture and product decisions in the project's source of truth.
- Consider security, privacy, accessibility, performance, reliability, observability, and support where relevant.

## Safety and approval boundaries

- Do not expose secrets, credentials, personal data, or restricted information.
- Do not delete, overwrite, bulk-migrate, deploy, change production data, or modify infrastructure without explicit authorization.
- Do not accept security, privacy, legal, or production risk on behalf of an authorized owner.
- Ask when requirements conflict, access is unclear, or a change is difficult to reverse.

## Project-specific source of truth

- Product profile: [path]
- Requirements / backlog: [path]
- Architecture / ADRs: [path]
- Design: [path]
- Test strategy: [path]
- Operations / runbooks: [path]
- Build and test commands: [verified commands]

## Completion report

Report the outcome, files changed, requirements addressed, tests/checks actually run and results, limitations, risks, and decisions needing human approval.


## Efficient session behavior

- Keep this file concise; put repeatable workflows in on-demand skills and detailed standards in linked project documents.
- Load only the PEOF disciplines relevant to the current task; do not read the entire framework at session start.
- Use the current work-package brief and session handoff to avoid rediscovering project state.
- Prefer targeted file/symbol inspection and concise command output; do not dump large logs or generated directories into context.
- Choose an appropriate available model and effort for the task. Avoid unnecessary model/effort changes mid-session.
- Use subagents and parallel execution only when isolation, breadth, or independence justifies extra usage.
- Save durable progress to project documentation before clearing or ending a substantial session.
- `/clear` starts a clean conversation; it does not reset the account's shared subscription allowance.
