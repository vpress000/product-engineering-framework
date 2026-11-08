# Task and Session Strategy for Subscription Efficiency

## Purpose

Reduce avoidable subscription consumption while retaining reliable continuity across Claude Code sessions.

## 1. Use sessions as work units, not as permanent project memory

A Claude Code session should focus on one coherent task or implementation group. It should not become the permanent record of the product.

Keep durable knowledge in the repository: requirements, architecture decisions, implementation status, test evidence, and a concise session handoff. This lets the next session start clean without rediscovering the project.

## 2. Choose the right session action

| Situation | Recommended action | Reason |
|---|---|---|
| Start an unrelated task | Save handoff if needed, then `/clear` or start a new session | Removes irrelevant prior conversation context |
| Continue the same task, but context is getting large | Use `/compact` at a sensible checkpoint | Preserves a shorter continuation summary |
| Same task, small context, continuing now | Continue current session | Avoids unnecessary re-onboarding |
| Previous session ended and cache/history is stale | Start fresh and load only the handoff and relevant files | Avoids carrying old conversation baggage |
| Switch from discovery to implementation | Save decisions and task brief; start a focused implementation session when this creates a clear boundary | Keeps research noise out of implementation |
| Move between unrelated feature groups | Finish current group handoff; start a new session | Prevents unrelated feature context accumulating |

`/clear` does not reset subscription usage. It reduces irrelevant context in subsequent requests. A fresh session also does not create a fresh account allowance.

## 3. Recommended work-package cycle

1. **Prepare:** Read the current implementation plan and select one bounded work package.
2. **Brief:** State the outcome, scope, acceptance criteria, source-of-truth documents, likely files, and commands allowed.
3. **Inspect narrowly:** Identify the likely implementation path; expand discovery only when evidence requires it.
4. **Plan proportionately:** Use a short plan for routine work and a fuller plan for risky or cross-cutting work.
5. **Execute:** Implement the coherent group; avoid unrelated refactoring.
6. **Verify:** Run the smallest relevant tests first, then broader checks when justified.
7. **Record:** Update status, decisions, files changed, tests, risks, and outstanding work.
8. **Handoff:** Prepare a compact next-session handoff before ending or clearing the session.

## 4. Batch related work, but do not create giant prompts

Batch tasks when they share the same files, context, dependencies, and acceptance criteria. Split them when they have unrelated context, different risk, or independent ownership.

Good batch: implement a feature group that shares an API contract and can be collectively reviewed and tested.

Poor batch: ask for unrelated architecture research, a UI redesign, a deployment, and a documentation rewrite in one open-ended task.

## 5. Completion rule

A session is ready to close when:

- The work package status is accurate.
- Actual validation results are recorded.
- Known failures and unrun checks are explicit.
- Changes and decisions are recorded in durable files.
- The next action is unambiguous.
- The handoff is concise and points to source files instead of copying their contents.

## 6. Commands

Use `/clear` between unrelated tasks and `/compact` when continuing a long task. Check command availability and behavior against the installed Claude Code version. Do not treat any command as an account-usage reset.

## Related files

- [`07-persistent-project-memory-and-handoff.md`](07-persistent-project-memory-and-handoff.md)
- [`09-templates/35-session-handoff-template.md`](../09-templates/35-session-handoff-template.md)
- [`09-templates/36-work-package-brief-template.md`](../09-templates/36-work-package-brief-template.md)
