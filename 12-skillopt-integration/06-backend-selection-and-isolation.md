# Backend Selection and Isolation Boundaries

## Purpose

Prevent PEOF users from assuming that every SkillOpt backend has the same tool access, repository visibility, isolation, or validation capability.

## General rule

Choose the backend based on the task and required execution contract. Verify the current backend documentation and run a safe capability probe on the pinned SkillOpt revision. Never infer repository access from a backend name or from `--project` alone.

## Research engine vs. Sleep

The research engine has optimizer and target roles configured separately. Chat backends are not equivalent to execution harnesses. Some execution backends are target-only or require environment-specific rollout adapters. In the current docs reviewed for this release, `claude_chat` invokes the Claude Code CLI in print mode; it is not a direct Anthropic API client. Claude Code execution harnesses are a different route for agentic target rollouts. Verify current role support and adapter requirements in the pinned configuration reference.

SkillOpt-Sleep has a separate backend set. The current CLI reference lists mock, Claude, Codex, Copilot, Cursor, Pi, OpenCode, handoff, and Azure/OpenAI-compatible routes, but support and isolation vary by revision.

## Capability matrix (must be re-verified)

| Mode/backend family | Model/provider calls | Project file/tool access | PEOF treatment |
|---|---:|---|---|
| Sleep `mock` | No | No real execution evidence | Safe plumbing check only; not quality evidence |
| Sleep `handoff` | Engine makes no provider calls | Human/model answer is supplied out of band; validate context isolation | Use for manual, reviewed operation; protect held-out context |
| Sleep `claude` / CLI backends | Yes | Depends on backend invocation and working directory; current Claude Sleep docs describe `--bare` or a capability-probed `--safe-mode` guard | Inspect diagnostics and actual filesystem/tool behavior in a disposable workspace; safe mode is not an OS sandbox and may omit user-level Claude skills/plugins/hooks/MCP |
| Sleep Cursor ordinary replay (current docs) | Yes | Read-only Ask mode in an empty temporary workspace; project files denied; tool-aware replay currently disabled | Textual guidance evaluation only; not repository end-to-end evaluation |
| Sleep Pi/OpenCode/Codex/Copilot | Usually yes for real backend | Backend-specific controls; inspect current docs | Validate actual tool/MCP/config isolation before project tasks |
| Research chat backend | Yes | Usually conversation input; tools/context depend on adapter/config | Use for text-centric skill tasks unless adapter proves more |
| Research `claude_code_exec` / `codex_exec` / other exec target | Yes | Agentic execution where supported, controlled by benchmark rollout/adapter | Preferred starting point for repo-aware benchmark work after isolation is proven; target-role support and adapter requirements vary by SkillOpt revision |

This is a guide, not a substitute for the current README, CLI reference, backend docs, source code, or diagnostic output. Capability changes can land on `main` before a package release.

## Known Sleep limitation in the reviewed source

The reviewed `skillopt_sleep` source configuration labels `replay_mode` as a report label and explicitly notes that fresh-worktree replay is not implemented. Therefore, do not claim that Sleep itself creates a new isolated code worktree for each replay. For code-editing evaluations, implement the project-aware worktree lifecycle in the research benchmark adapter or an independent runner. The current Cursor Sleep backend also documents ordinary replay in an empty temporary workspace with project files denied and tool-aware replay disabled; that is text-guidance evaluation, not repository end-to-end evaluation.

## Required capability probe

Before a real run, record evidence for:

- process executable and exact version;
- working directory and filesystem roots visible;
- read/write access to a harmless sentinel file;
- whether project `CLAUDE.md`, skills, hooks, plugins, MCP, or user configuration are loaded or excluded;
- shell command execution and allowed command policy;
- network access and external services;
- git write access and worktree boundary;
- whether commands can access environment variables or credentials;
- whether tool outputs and file content are transmitted to the provider;
- cleanup/reset behavior.

Do not use a real secret as a probe. Use synthetic sentinel content and a temporary repository. For Claude Sleep, inspect the diagnostics field that reports the selected isolation mode; for other backends, inspect their backend-specific diagnostics and current source/docs.

## Isolation levels

Classify every run:

- **L0 — Text-only:** only prompt/task text is available; no project files or tools.
- **L1 — Read-only project:** approved repository files are visible; writes and commands are disabled.
- **L2 — Disposable workspace:** write-capable work in a fresh worktree/container with controlled commands and no production secrets.
- **L3 — External side-effect environment:** network/service/deploy/data effects may occur; requires a separate threat model and explicit approval. Not allowed for routine skill optimization.

Record the level in every evaluation report. If behavior is unknown, classify as unknown and do not use for write-capable or sensitive work.

## Project-scope warning for Sleep

Sleep's `--project` option scopes project session collection, targets/state/staging as documented. It is not proof that the selected replay backend can inspect the project's source, run its tests, or use project tools. The current Cursor docs explicitly say ordinary replay cannot inspect project files and tool-aware replay is disabled. Use the project benchmark adapter for end-to-end repository evaluation.

## Fail closed

Stop if the backend unexpectedly loads user plugins/MCP, sees credentials, has broader filesystem access than expected, escapes the worktree, cannot reset state, or its isolation mode cannot be diagnosed.
