# Persistent Project Memory and Session Handoff

## Purpose

Make a fresh Claude Code session productive without carrying the full conversation history or forcing a complete project rediscovery.

## 1. Durable project state belongs in the repository

Keep authoritative facts in maintained project documents, not only in chat history. The minimum viable set is:

- `CLAUDE.md`: concise, durable project instructions and links.
- `docs/engineering/DEVELOPMENT-STATUS.md`: current product/engineering status.
- `docs/engineering/IMPLEMENTATION-PLAN.md`: prioritized work packages and dependencies.
- `docs/engineering/SESSION-HANDOFF.md`: the precise next-session starting point.
- Existing requirements, architecture decisions, test strategy, and release records as the sources of truth.

Use equivalent existing files if the repository already has them. Do not create duplicate status files by default.

## 2. Keep `CLAUDE.md` small

`CLAUDE.md` should not become a transcript, full project manual, or copy of PEOF. Keep only the project summary, key source-of-truth links, essential commands, critical constraints, and task workflow. Put detailed workflows in on-demand skills and detailed standards in linked documents.

## 3. End-of-session handoff

Before ending a substantial session or clearing its context, update the handoff with:

- Current objective and scope.
- Completed work and evidence.
- Current Git branch and clean/dirty status.
- Files created/modified/deleted.
- Decisions made and source references.
- Tests/checks run and exact outcomes.
- Failures, unrun checks, risks, and blockers.
- Next action in priority order.
- Specific files/sections the next session should inspect.

Do not paste entire source files or conversation history into the handoff. Link to the source of truth.

## 4. Start-of-session recovery

A new session should:

1. Read root `CLAUDE.md`.
2. Read the current handoff and status file only if present and relevant.
3. Check branch and Git status.
4. Verify that referenced files and the stated next action still match the repository.
5. Read only the relevant requirements/architecture/code sections.
6. Summarize the confirmed starting point in a few lines and continue.

Do not rescan the entire repository unless the handoff is stale, the task requires wider discovery, or new evidence conflicts with it.

## 5. Handoff is not authorization

A handoff records state; it does not grant permission to deploy, migrate data, alter production infrastructure, expose secrets, or make other protected changes. Follow current project approval boundaries.

## 6. Suggested cadence

Update the handoff after a meaningful implementation package, before changing unrelated work, before a planned break, and whenever an interruption could make the next action ambiguous. Do not create a handoff after every minor edit if it adds more process than value.

## Related templates and skills

- [`../09-templates/35-session-handoff-template.md`](../09-templates/35-session-handoff-template.md)
- [`../09-templates/36-work-package-brief-template.md`](../09-templates/36-work-package-brief-template.md)
- [`../08-claude-code/starter-kit/skills/peof-session-handoff/SKILL.md`](../08-claude-code/starter-kit/skills/peof-session-handoff/SKILL.md)
