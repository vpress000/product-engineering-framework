# PEOF Project Bootstrap Workflow

## Purpose

Provide one repeatable onboarding process for setting up the Claude Code environment and project-specific PEOF configuration in either a greenfield or existing repository.

This is the **PEOF Claude Bootstrap** layer. It operationalizes the framework; it is not a substitute for the product engineering lifecycle.

## Non-negotiable rules

- Start with read-only discovery.
- Write nothing until the user approves the exact plan.
- Verify current Claude Code documentation before writing settings keys, permission patterns, hook fields, skill/agent frontmatter, file locations, or commands.
- Never overwrite existing configuration. Propose a minimal diff or a side-by-side alternative.
- Do not install tools, plugins, MCP servers, integrations, or scheduled tasks unless explicitly selected.
- Do not invent workflows, services, or features.
- Ask only questions that repository evidence and existing configuration cannot answer.
- Separate user-level changes from project-level changes; user-level changes require separate approval.
- Treat secret, deployment, migration, infrastructure, production, and customer-data paths as protected until the owner confirms handling.
- Approval to assess is not approval to write; approval to write instructions is not approval to change application code.

## Stage 0 — Choose the project route

Route each workstream as one of:

- **Greenfield:** empty/new repository or no existing product assets.
- **Existing product:** code, product assets, users, or established workflows exist.
- **Modernization:** material architecture, reliability, security, process, or technical-debt changes are needed.
- **Framework migration:** an existing engineering standard or AI configuration is being replaced or consolidated.
- **Mixed/multi-product:** route each product or workstream independently.

Do not assume an empty directory means the product is fully greenfield; ask about existing designs, requirements, external services, and prior decisions.

## Stage 1 — Read-only inspection

Follow `05-environment-discovery-and-inventory.md`.

Inspect global Claude instructions/settings and user skills/agents only with permission. Inspect project configuration, repository manifests, CI, instructions, and tooling. Redact credentials. Do not run project commands with side effects.

For an existing product, inspect the codebase the way a project initializer would: manifests, README, CI, repository/monorepo layout, build/test/lint/format commands, and protected paths.

Summarize findings in 10 lines or fewer, marking each as found, unknown, user-confirmed, or not applicable.

## Stage 2 — Interview: core round

Ask no more than four questions in the first round. Use a structured question interface when available; use free text for commands and path lists.

Cover only unknowns that affect the setup:

1. **Project scope and stack:** for a new project, ask for the intended stack and commands or whether Claude should recommend them; for an existing project, confirm the detected stack and commands. Confirm project route and scope.
2. **Protected paths and forbidden actions:** confirm detected sensitive paths and anything that must never be auto-read, edited, or executed.
3. **Autonomy:** confirm the desired approval posture (review-first, limited automation, or a higher-autonomy mode) and explain material consequences.
4. **Integrations:** ask which external services Claude should access directly. Only services explicitly named by the user are eligible. Ask monorepo-specific follow-up only if a monorepo was detected.

Do not re-ask facts already established by repository evidence or the conversation.

## Stage 3 — Interview: optional-capability round

Ask one multi-select question covering only relevant optional capabilities:

- Repeatable project workflow (skill or subagent).
- Personal prompt library integration.
- Separate review before work is considered complete.
- Context/auto-compaction preferences.
- Saved plan files.
- Output style.
- Plugin for the stack or packaging the setup for reuse.
- CI integration.
- Scheduled or recurring task.
- Parallel work with Git worktrees.
- Agent teams (experimental; additional coordination and token cost).
- Browser/desktop integration, if relevant.
- Subscription usage-efficiency setup (bounded work packages, project handoff, concise instructions, and usage-aware SkillOpt budgets); this does not change billing or account settings.

Ask follow-ups only for selected options. For example, ask for threshold behavior only after verifying that a supported setting exists; ask for cadence/time zone for a schedule; ask which ignored files are safe to include in a worktree; ask which prompt-library items to scaffold.

## Stage 4 — Draft the product and environment configuration

Draft only what applies. Recommended components:

### Project instructions

- Keep root `CLAUDE.md` concise, ideally under 200 lines according to current documentation guidance.
- Include confirmed build/test/lint/format commands, project conventions not obvious from code, source-of-truth links, and repository etiquette the user confirmed.
- Move path-specific or topic-specific instructions to `.claude/rules/` with current supported path scoping.
- If `AGENTS.md` exists and is already the project's source of instructions, confirm current AGENTS.md loading behavior and determine whether Claude-specific additions are needed. Do not duplicate it mechanically.

### Settings and permissions

- Place each setting in the correct user, shared-project, project-local, or managed scope.
- Never write machine-specific absolute paths into shared project files.
- Add only confirmed routine commands to allow rules.
- Ask or deny for protected operations as agreed.
- Verify exact permission syntax, scope, precedence, and version support.
- Be explicit that deny rules and prompts do not guarantee secrets are unreachable through arbitrary scripts or other integrations.

### Hooks

- Add only selected deterministic hooks.
- Prefer narrow matchers, least privilege, explicit timeouts, and documented failure behavior.
- Use a portable runtime only after confirming it is installed and supported in the actual shell/OS.
- For Windows, check current Git Bash/PowerShell hook behavior and test on the target machine.
- Do not add notifications unless requested.

### Skills and agents

- Start with only the selected project workflows; do not install every PEOF example.
- Use skills for procedures and agents for bounded specialist roles.
- Give agents the smallest tool allowlist that works.
- Side-effecting skills such as deploy/release remain user-invoked.

### MCP and plugins

- Configure only named services/plugins.
- Choose local/user/project scope intentionally.
- Explain authentication steps and trust prompts.
- Keep credentials out of source control.

## Stage 5 — Present the approval plan and stop

Use [`../09-templates/20-claude-code-setup-and-approval-plan-template.md`](../09-templates/20-claude-code-setup-and-approval-plan-template.md).

Present:

1. Project files: path, create/modify/leave unchanged, purpose, and full content or diff for material settings/hooks/CI changes.
2. User-level changes: listed separately and requiring separate approval.
3. External services/plugins/MCP/CI/scheduled tasks and their scopes.
4. Manual actions: authentication, account permissions, app installation, CI secrets, marketplace trust, or other steps only the user can perform.
5. Known limitations: platform, permission, sandbox, version, cost, or tool constraints.
6. Rollback plan.

Then stop and wait. The user may approve all, some, request revisions, or decline. No write action occurs before explicit approval.

## Stage 6 — Write only approved items

- Apply only approved files and settings.
- Preserve existing content and use minimal diffs.
- Do not change product code, databases, deployment, or infrastructure unless explicitly included in the approval.
- Keep secrets, tokens, private data, and personal machine configuration out of shared files.
- Maintain a change manifest with created, updated, unchanged, and deferred items.

## Stage 7 — Self-check and hand off

Follow `08-setup-validation-and-handoff.md` and produce the validation report. Fix failures within the approved scope. If a fix requires new scope, stop and request approval.

## Stage 8 — Product engineering handoff

After the Claude Code environment is ready, return to the main PEOF lifecycle:

- Greenfield: create the product brief/profile and proceed into product discovery and MVP definition.
- Existing product: complete the current-state assessment, evidence map, and adoption plan.
- Modernization: establish baseline risks, target-state decisions, staged migration, and rollback criteria.
- Framework migration: map existing assets, resolve conflicts, pilot, and cut over incrementally.

Do not confuse a configured Claude Code environment with a product that is ready for development.

## Definition of done

Bootstrap is complete only when the approved setup is implemented, validations are reported honestly, manual steps are identified, rollback is documented, and the next product-engineering action is clear.


## Subscription usage efficiency (optional)

When the developer reports hitting Claude subscription limits, use [`../13-usage-efficiency/01-subscription-usage-model.md`](../13-usage-efficiency/01-subscription-usage-model.md) and its related playbooks. Clarify that a fresh session or `/clear` does not reset shared account usage. Do not change plans, enable usage credits, configure API billing, or alter auto-reload settings as part of project bootstrap. Those remain account-owner decisions.
