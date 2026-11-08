# Claude Code Environment Discovery and Inventory

## Purpose

Establish a read-only, evidence-based inventory of the developer environment and the target repository before proposing Claude Code configuration. This document complements product discovery; it does not replace the product profile or current-state assessment.

## Operating rules

1. Start read-only. Inventory is not permission to change settings, install tools, authenticate services, execute project scripts, or access production systems.
2. Ask permission before reading outside the target project, especially user-level configuration. If the user has explicitly requested a bootstrap and granted access, inspect only the relevant files and metadata.
3. Never print, copy, summarize, or place secret values in reports. Do not open `.env*`, private keys, tokens, credential stores, production secrets, or secret-bearing files. Record only that a protected path exists and how it must be handled.
4. Treat `~/.claude.json` as sensitive application state. Do not dump or manually edit it. MCP local-scope server information is stored there; inspect only through supported Claude Code status/configuration views and redact names or values where needed.
5. Redact credentials embedded in Git remote URLs, command output, environment variables, and configuration values.
6. Distinguish **found**, **unknown**, **user-confirmed**, and **not applicable**. Do not infer a missing configuration from a template.
7. Verify behavior against current official Claude Code documentation and the installed CLI version before writing configuration or invoking version-specific commands.

## A. Developer environment inventory

Capture only what is relevant to the requested setup:

| Area | Inspect | Record |
|---|---|---|
| Operating system | OS and version | Windows/macOS/Linux, native/WSL/container/remote |
| Shell | PowerShell, Git Bash, Bash, Zsh, other | Default shell and available alternatives |
| Terminal / IDE | Terminal host and editor integration | CLI, VS Code, JetBrains, Desktop, or other supported surface |
| Claude Code | Installed version and invocation surface | Version and whether the session is local, remote, or cloud |
| Runtime tools | `node`, package managers, language runtimes | Installed versions only; do not install anything |
| Source control | `git`, repository status, host | Git availability, clean/dirty state, GitHub/GitLab/other |
| Hosting CLI | `gh`, `glab`, or other | Check only when the repository host makes it relevant |
| Project tooling | Build, test, lint, format, type-check commands | Derive from manifests and CI; do not execute until approved and safe |
| Local constraints | Offline/network, proxy, execution policy, filesystem | Only material constraints relevant to configuration |

Do not assume the developer uses Windows, Git Bash, Node.js, GitHub, or a particular IDE. Record the actual environment and adapt.

## B. Global Claude Code inventory

With explicit permission, inspect the presence and relevant non-secret content of:

- `~/.claude/CLAUDE.md` — personal instructions.
- `~/.claude/settings.json` — user-level settings; redact sensitive values.
- `~/.claude/rules/` — user-level rules, if present.
- `~/.claude/skills/` — user-level skills, if present.
- `~/.claude/agents/` — user-level subagents, if present.
- User-level plugins/marketplaces or other Claude Code extensions, using supported status/configuration views.
- `~/.claude.json` — do not dump or manually edit; use supported views for MCP/global configuration and redact all sensitive data.

Do not copy global instructions or skills into a project automatically. Identify their purpose and reuse them only when appropriate and explicitly selected.

## C. Project-level configuration inventory

Inspect presence and relevant content of:

- `CLAUDE.md`, `.claude/CLAUDE.md`, and `CLAUDE.local.md`.
- `.claude/settings.json` and `.claude/settings.local.json`.
- `.claude/rules/`, `.claude/skills/`, `.claude/agents/`, `.claude/hooks/`, and project plugin configuration.
- `.mcp.json` and any other documented MCP configuration.
- `AGENTS.md` and nested `AGENTS.md` files. Claude Code currently documents AGENTS.md support; check the current loading rules and precedence rather than assuming all files are loaded in every context.
- `.cursor/rules/`, `.github/copilot-instructions.md`, and other AI-tool instructions.
- `.gitignore`, `.git/info/exclude`, and relevant worktree configuration.

For each instruction source, record path, scope, purpose, whether active/loaded, overlaps, and conflicts. Do not duplicate instructions without a reason.

## D. Repository and codebase inventory

For a non-empty project, inspect only enough to establish:

1. Repository root, layout, and whether it is a monorepo or multi-package workspace.
2. README and relevant architecture/product documentation.
3. Manifests and lockfiles (for example `package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, solution/project files, and Makefiles).
4. CI workflows and build scripts.
5. Git status and branch; inspect remotes only after redacting embedded credentials.
6. Existing test, lint, format, type-check, build, and deploy commands from authoritative files.
7. Sensitive and high-impact paths: `.env*`, secrets, certificates, database migrations, infrastructure-as-code, deployment scripts, generated assets, customer data, and production configuration.
8. Existing conventions, test coverage shape, and repository contribution instructions.

Do not execute build, migration, deployment, seed, or infrastructure commands during read-only discovery. Some test commands can mutate data or contact external services; classify and obtain approval before running them.

## E. Findings summary

Return a concise summary of no more than 10 lines before starting the interview. Each item must be marked `found`, `unknown`, `user-confirmed`, or `not applicable`. Include:

- Engagement route and project state.
- Product/repository identity and structure.
- Detected stack and package manager.
- Confirmed development commands or `unknown`.
- Claude Code and AI-instruction files found.
- Developer OS/shell and available relevant tools.
- Sensitive/protected paths identified (paths only, no contents).
- Existing services/integrations configured (redacted).
- High-risk unknowns or conflicts.
- Recommended next discovery decision.

## F. Inventory output

Use [`../09-templates/21-developer-environment-profile-template.md`](../09-templates/21-developer-environment-profile-template.md) for the developer environment profile and [`../09-templates/12-current-state-assessment-template.md`](../09-templates/12-current-state-assessment-template.md) for product/repository assessment. Keep the two profiles separate.

## Current documentation references

- [Claude Code memory and instruction files](https://code.claude.com/docs/en/memory)
- [Claude Code settings and scope](https://code.claude.com/docs/en/settings)
- [Claude Code MCP configuration and scopes](https://code.claude.com/docs/en/mcp)
- [Claude Code troubleshooting and diagnostics](https://code.claude.com/docs/en/troubleshooting)
