# Permissions and Configuration Management

## Purpose

Define how Claude Code configuration is reviewed, scoped, approved, and validated. Use this document whenever PEOF is introduced into a repository or an existing Claude Code setup is changed.

## 1. Separate configuration scopes

Do not put every preference into the project. Choose the narrowest appropriate scope and confirm current behavior in the official documentation.

| Scope | Common location | Intended use | Change approval |
|---|---|---|---|
| User instructions | `~/.claude/CLAUDE.md`, `~/.claude/rules/` | Personal instructions used across projects | Separate user-level approval |
| User settings | `~/.claude/settings.json` | Personal defaults and permission preferences | Separate user-level approval |
| Project instructions | `CLAUDE.md`, `.claude/CLAUDE.md`, scoped rules | Shared product/repository conventions | Project owner approval |
| Shared project settings | `.claude/settings.json` | Team-shared settings, permissions, hooks, plugins where supported | Project owner approval; review before commit |
| Project-local settings | `.claude/settings.local.json` | Machine-specific settings for one project | User approval; ensure it stays uncommitted |
| Project-local instructions | `CLAUDE.local.md` | Personal per-project guidance | User approval; ensure it stays uncommitted |
| Managed policy | Organization-managed paths/sources | Organization-wide policy | Organization administrator only |
| MCP configuration | Local/user/project scopes, including `.mcp.json` for project configuration | Tool/service connections | Explicit service-specific approval |

Important distinctions:

- The current settings documentation distinguishes user, shared project, project-local, and managed settings.
- MCP local scope is different from project-local settings. Current documentation states that local-scope MCP server configuration is stored in `~/.claude.json`; do not manually edit or expose that file.
- A project `.mcp.json` may be shared with the repository. Review it for secrets and environment-variable handling before committing.
- A project setting is not guaranteed to apply to every surface, cloud session, or untrusted folder. Verify actual behavior for the target execution surface.

## 2. Permission model

Use the current documented permission system, including `allow`, `ask`, and `deny` rules, permission modes, and sandboxing where supported.

Recommended starting posture:

- Keep human confirmation for file writes and commands until the exact project workflow is understood.
- Allow only confirmed, routine, low-risk checks that are safe and repeatable.
- Ask before operations with external effects, elevated privileges, data mutation, destructive behavior, deployment, release, or infrastructure changes.
- Deny access to explicitly protected paths where the current permission system supports the intended control.
- Do not enable broad bypass modes as a convenience. Any more autonomous mode requires an informed, explicit choice and a documented risk review.

Do not invent permission keys, mode names, patterns, or precedence. Verify syntax against the installed Claude Code version and current official documentation before creating settings.

## 3. Permission layers are not a complete security boundary

Treat configuration as defense in depth, not as a guarantee that secrets cannot be reached.

- A Read/Edit deny rule may not block indirect access through shell commands, scripts, tools, or another integration.
- Shell permissions and file permissions are evaluated differently; inspect the documented behavior for the selected shell and tool.
- Hooks run commands with the user's operating-system permissions. A faulty hook can access or alter files available to that user. A narrowly scoped protected-path hook can be an additional backstop to permission rules, but it is not a complete security boundary.
- MCP servers, plugins, agents, and external integrations introduce additional capabilities and trust boundaries.
- Do not place secrets in `CLAUDE.md`, skills, agent prompts, logs, test fixtures, plans, or generated reports.
- Avoid reading the contents of credential files during discovery. If a file must be handled, ask the user to perform the credential-specific step outside the generated report.

For sensitive paths, record the path and required handling, not the contents. If a project needs stronger isolation, assess OS-level controls, repository permissions, dedicated environments, secret managers, and the current Claude Code sandbox capabilities rather than relying only on prompt instructions.

## 4. Protect sensitive and high-impact paths

Identify and classify paths such as:

- `.env*`, API keys, tokens, private keys, certificates, and credential stores.
- Production configuration and customer/user data.
- Database migrations, destructive seeds, and schema reset scripts.
- Infrastructure-as-code and cloud account configuration.
- Deployment, release, publishing, and package-signing scripts.
- Billing, payment, identity, authorization, and security-critical code.
- Generated files, lockfiles, and files owned by other tools where direct editing is unsafe.

For each path, choose one or more controls: do not read, do not write, ask before access, use a safe redacted view, or exclude from automation. Confirm the exact policy with the owner.

## 5. Autonomy and approval preferences

Ask the developer to choose a working posture, then map it to current supported Claude Code settings only after verification:

1. **Review-first:** ask before meaningful writes and commands; suitable as the default during onboarding.
2. **Limited automation:** allow approved routine checks and low-risk edits while preserving prompts for sensitive operations.
3. **Higher autonomy:** permit a broader workflow only after the user reviews the exact permission and sandbox implications.

Do not silently translate a preference such as “auto-accept edits” into a broad permission mode. Explain what the selected mode can do and where its limits apply. Project files cannot necessarily set every user-level or managed setting.

## 6. Change-control requirements

Before writing any configuration:

1. Inventory the existing file and its scope.
2. Check whether a higher-precedence or managed setting controls the same behavior.
3. Propose a minimal diff; preserve unrelated existing entries and formatting where practical.
4. Show user-level changes separately from project changes.
5. Explain effects on teammates, cloud sessions, worktrees, CI, and local machines where applicable.
6. Identify secrets, credentials, and machine-specific values that must not be committed.
7. Obtain explicit approval for the exact changes.
8. Write only the approved items and validate them.

Never overwrite an existing `CLAUDE.md`, settings file, `.mcp.json`, hook, skill, or agent. If the file exists, propose a merge or minimal diff.

## 7. Validation and recovery

- Parse every JSON file with a real JSON parser; strict JSON does not allow comments or trailing commas.
- Confirm the configuration is loaded using the current supported status/diagnostic commands.
- Check for rejected settings, permission conflicts, and managed settings that override the proposal.
- Exercise new hooks with safe positive and negative test cases before relying on them.
- Confirm that normal operations still work and protected operations are blocked or require confirmation as intended.
- Inspect the diff and restore from a known backup if validation fails.
- Report checks as `passed`, `failed`, `not run`, or `not applicable`; never claim unexecuted checks passed.

## Official references

- [Settings files, scope, and precedence](https://code.claude.com/docs/en/settings)
- [Permission rules and sandboxing](https://code.claude.com/docs/en/permissions)
- [Hooks and their security considerations](https://code.claude.com/docs/en/hooks)
- [MCP server scopes](https://code.claude.com/docs/en/mcp)
- [Project instructions and AGENTS.md](https://code.claude.com/docs/en/memory)
