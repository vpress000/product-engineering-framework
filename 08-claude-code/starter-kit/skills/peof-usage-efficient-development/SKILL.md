---
name: peof-usage-efficient-development
description: Plan and execute a bounded Claude Code work package while reducing avoidable subscription usage through focused context, selective reads, suitable model/effort, concise outputs, and justified delegation. Use for implementation, debugging, testing, or documentation work when usage efficiency matters.
---

# PEOF Usage-Efficient Development

## Before work
1. Read the concise project instructions and current session handoff/status if present.
2. Verify the task, scope, acceptance criteria, and relevant source-of-truth paths.
3. Select a coherent work package; batch related work but exclude unrelated tasks.
4. Use the model/effort already selected for this task unless a material change is justified. Do not assume a particular model is available.
5. Decide whether subagents are genuinely useful. Default to the main session for small or sequential work.

## During work
1. Search and read narrowly. Avoid full-repository scans when targeted evidence is sufficient.
2. Refer to files/symbols by path and inspect relevant portions; avoid repeated full-file attachments.
3. Keep command output concise without hiding failures.
4. Run the smallest relevant validation first, then the agreed broader checks.
5. Do not repeat unchanged tests or investigations without a reason.
6. Do not launch broad parallel work, agent teams, or SkillOpt loops unless the expected benefit and scope justify their extra usage.
7. Never lower security, test, or acceptance standards merely to conserve usage.

## Finish
1. Report changed files and acceptance criteria.
2. Report exact checks run and results, plus checks not run and why.
3. Update durable project status and the session handoff when the work package is complete or being paused.
4. Suggest `/clear` only when moving to an unrelated task; suggest `/compact` only when continuing the same long task. State clearly that neither resets the subscription allowance.

## Output discipline
Prefer a concise summary, evidence, and next action. Do not provide unnecessary full-file dumps or a transcript of tool activity.
