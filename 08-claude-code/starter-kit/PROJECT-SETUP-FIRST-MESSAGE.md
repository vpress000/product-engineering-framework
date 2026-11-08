# PEOF Project Setup — First Message for Claude Code

Use this as the first message in a fresh Claude Code session opened at the root of a new or existing project. Customize the developer-environment notes if you want, but do not assume a particular OS, shell, or IDE.

```text
Set up a Claude Code environment and PEOF project foundation tailored to this project. Do not generate boilerplate for capabilities I do not need. For anything unnecessary, producing nothing is the correct result.

Use the Product Engineering Operating Framework (PEOF) supplied in this repository or at the path I identify. Treat PEOF as an adaptable method, not permission to change this repository.

## Rules that apply throughout

- Start read-only. Write nothing, install nothing, and configure no external service until I approve a specific plan.
- Verify, do not recall: before writing any Claude Code setting, permission, frontmatter field, hook registration, MCP/plugin configuration, path, or command, verify it against the current official Claude Code documentation and the installed version/surface. If documentation contradicts a suggestion here, follow the current docs and explain the difference.
- Never overwrite an existing configuration file. If one exists, propose a minimal diff or merge that preserves unrelated content.
- Do not invent services, workflows, product requirements, or features I did not ask for.
- Ask only what repository evidence and my accessible global setup cannot answer.
- Keep user-level changes separate from project-level changes. They need separate approval.
- Do not expose or copy secrets, tokens, private keys, customer data, or credential-store contents into reports or generated files.
- Approval to inspect is not approval to modify. Approval to set up Claude Code is not approval to change application code, database data, production infrastructure, or deploy.

## 1. Gather context (read-only)

A. Developer/global environment, only with permission:
- Identify OS, version, shell, terminal, IDE, Claude Code version/surface, Git, Node.js and other relevant runtimes.
- Inspect the presence and relevant non-secret content of user instructions/settings and list user-level skills/agents.
- Treat ~/.claude.json as sensitive internal state: do not dump or edit it. Use supported views for MCP/global configuration and redact sensitive values.
- Identify user-level rules and optional prompt libraries, but do not copy them.

B. Project configuration:
- Inspect existing CLAUDE.md, .claude/ (settings, rules, skills, agents, hooks), .mcp.json, AGENTS.md, .cursor/rules, .github/copilot-instructions.md, .gitignore and related AI-tool instructions.
- Identify conflicts, overlaps, existing source-of-truth files and what must be preserved.

C. Repository:
- If non-empty, inspect repo/monorepo layout, README, manifests and lockfiles, CI configuration, Git status/host, build/test/lint/format/type-check commands, and relevant architecture docs.
- Derive commands from source files. Do not execute a command that may mutate data, access paid services, deploy, migrate, publish, or alter infrastructure during discovery.
- Identify sensitive/high-impact paths (.env*, secrets, credentials, migrations, infrastructure-as-code, deployment scripts, production config, customer data). Record paths only; do not open secret contents.

D. Summarize findings in 10 lines or fewer. Mark each item found, unknown, user-confirmed, or not applicable.

## 2. Interview in two rounds

Round 1 — core questions: ask no more than four questions, only for unresolved items. Use structured question UI where available; use plain text for paths and exact commands.
1. Project route/scope and stack: new project — ask for intended stack/commands or whether I want recommendations; existing project — confirm detected stack and safe commands.
2. Sensitive/protected paths and actions that must never be read, edited, or run automatically.
3. Autonomy preference: review-first, limited automation, or higher autonomy; explain consequences and limitations.
4. External services Claude should access directly. Include monorepo conventions only if a monorepo was found.

Round 2 — one multi-select question for optional capabilities:
- Repeatable project workflows (skills or subagents).
- Personal prompt library skills.
- Review step before non-trivial work counts as done.
- Context/auto-compaction preferences.
- Saved plan files.
- Output style.
- Plugin installation or packaging this setup as a plugin.
- CI integration.
- Scheduled/recurring task.
- Parallel sessions with Git worktrees.
- Agent teams (experimental, additional coordination/token cost).
- Browser/desktop integration, if relevant.

Ask follow-ups only for selected items. Do not guess unsupported settings or install anything by default.

## 3. Draft only what applies

- Project instructions: create or minimally merge a concise CLAUDE.md; move topic/path-specific standards to .claude/rules/ where useful. If AGENTS.md exists, verify current loading behavior and avoid duplicate instructions.
- Settings/permissions: select the correct user/shared-project/project-local/managed scope. Include only confirmed routine commands. Ask/deny sensitive or high-impact operations as agreed. Explain precedence, sharing, and limits.
- Hooks: create only selected deterministic hooks. Review scripts; they execute with my user permissions. Use the actual platform/shell and verify event schema, timeout, failure behavior, and safe test cases.
- Skills/agents: create only selected workflows/roles. Skills are for procedures; subagents are for bounded tasks. Use the smallest tool allowlist. Side-effecting workflows remain user-invoked.
- MCP/plugins: configure only services or plugins I explicitly selected. Explain scope, permissions, source/trust, and authentication. Never commit credentials.
- Optional CI, worktrees, scheduled tasks, agent teams, output styles, or plans: configure only if selected and supported in my installed version/surface.

## 4. Plan and wait for approval

Use the PEOF setup approval-plan template. Present:
1. Every project file: path, create/modify/leave unchanged, purpose, and full proposed content/diff for settings, hooks, and CI files.
2. User-level changes separately, with their own approval.
3. External services, MCP, plugins, CI, schedules, and worktrees, including scopes and permissions.
4. Manual steps I must perform (authentication, CI secrets, marketplace trust, app approval, etc.).
5. Known limitations, version/platform constraints, risks, and rollback steps.

Then stop. I may approve all, only selected items, request changes, or decline. Do not write before approval.

## 5. Write, self-check, and hand off

- Write only the approved items. Do not modify application code or project assets unless explicitly included.
- Parse every JSON file; validate frontmatter, links, file paths, and script syntax.
- Test each new hook with safe positive and negative sample input. Do not use real secrets to test blocked paths.
- Run only confirmed project checks that are safe and approved; report skipped checks with reasons.
- Inspect the final diff for unrelated or unapproved changes.
- Confirm current settings/skills/agents/hooks/MCP status using documented diagnostics for this version.
- Report pass/fail/not-run, evidence, files created/changed, user-level vs project-level changes, manual steps, rollback, commit-vs-local recommendations, and next PEOF product-engineering step.

Begin with read-only discovery. Do not ask me to repeat information already available in the repository or prior messages.
```
```

## Customization notes

- The prompt intentionally does not hardcode a personal prompt-library path, operating system, shell, team size, or preferred autonomy mode. Add those only when they are genuinely stable preferences.
- The prompt is a workflow aid, not an enforcement boundary. Use current Claude Code permissions, hooks, and operating-system controls where enforcement is required.
- If the installed Claude Code `/init` workflow provides a suitable interactive initialization path, compare it with this PEOF process before choosing. Do not run an initializer that writes files without reviewing its proposal and approval behavior.
