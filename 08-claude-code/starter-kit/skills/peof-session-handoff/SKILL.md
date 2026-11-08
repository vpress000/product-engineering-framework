---
name: peof-session-handoff
description: Create or validate a concise repository-backed session handoff before a Claude Code task is cleared, closed, or transferred to a fresh session. Use when the user asks to save progress, prepare continuation, or hand off work.
---

# PEOF Session Handoff

## Purpose
Create a reliable continuation record without copying long conversation history or source files.

## Workflow
1. Inspect the current Git branch and working-tree status.
2. Identify the current work package and compare chat claims with actual repository files/diffs.
3. Review validation already run; do not claim tests passed unless evidence is present.
4. Reuse existing status/handoff files when they exist. Avoid creating duplicates.
5. Update the project's agreed handoff file using `09-templates/35-session-handoff-template.md` as guidance, adapting paths to the repository.
6. Record completed, partial, blocked, and planned work separately.
7. Link to source files, requirements, ADRs, and test evidence rather than pasting their contents.
8. Exclude credentials, secrets, private customer data, and raw session transcripts.
9. Report the exact handoff path and a short next-session opening instruction.

## Safety
- Do not commit, push, deploy, migrate, delete, or discard work unless separately authorized.
- A handoff does not grant approval for future side effects.
- If repository state is ambiguous, record the uncertainty instead of guessing.

## Output
Return the handoff path, Git status summary, validation status, and next action. Keep the response concise.
