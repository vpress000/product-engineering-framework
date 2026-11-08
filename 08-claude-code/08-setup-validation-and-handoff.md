# Claude Code Setup Validation and Handoff

## Purpose

Define the post-setup verification required before a Claude Code environment or project bootstrap is declared complete.

## Validation principles

- Validate only what was approved and actually created or changed.
- Prefer read-only and deterministic checks.
- Do not run a test, hook, build, migration, deployment, or CI workflow if it may mutate data or contact an external service without approval.
- Never claim success for an unexecuted check.
- Capture concise evidence and redact secrets, user data, and credentials.

## 1. File and diff checks

- Confirm each created/modified path matches the approved plan.
- Confirm no unapproved files changed.
- Confirm existing content was preserved or the approved diff was applied.
- Check `.gitignore` / global exclude behavior for local settings and personal files.
- Check that project-shared files do not contain machine-specific absolute paths or credentials.
- Check that all expected skills contain `SKILL.md` and all agent definitions use currently supported frontmatter.
- Check CLAUDE.md files, rules, nested instruction files, and imports for duplication or contradiction.
- Keep CLAUDE.md concise; current documentation recommends under 200 lines per file as a target, not a hard universal limit.

## 2. Syntax checks

- Parse every JSON file with a standard JSON parser. JSON files must not contain comments or trailing commas.
- Validate YAML frontmatter and required fields against current Claude Code docs.
- Validate relative links and references to files/directories.
- Confirm script syntax using the relevant runtime/parser where safe.
- Do not run arbitrary project scripts simply to prove they parse.

## 3. Hook tests

For every hook created:

1. Review the exact script and the command that launches it.
2. Confirm it has an explicit timeout and appropriate failure behavior.
3. Supply safe sample input matching the documented event payload.
4. Test a normal/allowed case.
5. Test a blocked/denied case for guard hooks.
6. Confirm exit code and output behavior match the documented hook event semantics.
7. Test on the actual operating system and shell used by the developer.
8. Confirm it does not read secrets, call external services, or mutate unrelated files.

Do not assume a hook behaves identically in Git Bash, PowerShell, macOS, Linux, containers, and remote sessions. Check the current hooks documentation, especially Windows failure behavior.

## 4. Settings and permission checks

- Confirm settings JSON parses.
- Confirm the actual settings sources loaded using current diagnostics.
- Check whether managed settings, command-line flags, environment variables, or higher-precedence files change the result.
- Verify the intended permission behavior using safe test cases.
- Confirm sensitive-path protections are not represented as stronger security guarantees than they provide.
- Check normal development commands remain usable.
- Do not test a deny rule by reading a real secret. Use a harmless test path or a dummy fixture.

## 5. Skill, agent, MCP, and plugin checks

- Skills: confirm the selected skill is discoverable and invocation instructions are clear.
- Agents: confirm the selected agent appears and has only the approved tools/capabilities.
- MCP: verify status and authentication using supported views; do not print tokens or sensitive server configuration.
- Plugins: confirm the selected plugin and version/source; review enabled components and permissions.
- Worktrees: if configured, confirm isolation and that no sensitive ignored files were copied.
- Agent teams: validate only if explicitly enabled; document experimental status and observed limits.

## 6. Agentic asset validation

When skills, agents, or prompt assets are created or changed, validate them under [`../11-agentic-engineering/03-skill-evaluation-and-benchmarking.md`](../11-agentic-engineering/03-skill-evaluation-and-benchmarking.md):

- Confirm a baseline and candidate version/hash are recorded.
- Confirm evaluation tasks are representative, approved, and split/exposure status is known.
- Run static checks and the predeclared behavioral checks.
- Compare baseline and candidate on the same task manifest and equivalent environment.
- Report failure cases, uncertainty, cost/latency, safety behavior, and limitations.
- Confirm that no candidate directly changed live assets during evaluation.
- Confirm human approval, backup, and rollback plan before publication.
- For multi-skill proposals, verify each skill independently and adopt only explicitly selected skills.

Do not certify an asset if the validation set is contaminated, critical results are missing, or the evaluator failed in a way that invalidates the outcome.

## 7. Project check commands

Run only the relevant commands discovered and approved during discovery. Typical checks include formatting, lint, type checking, unit tests, integration tests, and build. Do not run commands that may:

- Drop/reset databases or modify test/production data.
- Deploy, publish, release, or alter infrastructure.
- Access paid or production external APIs.
- Send messages, create external resources, or trigger billing.

Where a command is unsafe or cannot be run, report `not run` with the reason and identify a safe alternative.

## 8. Diagnostics and handoff

Use only commands documented for the installed version and the selected surface. Depending on the configuration, current documentation may support status, hooks, MCP, permissions, context, doctor, or prompt-audit diagnostics. Verify command availability rather than copying a static list from an old prompt.

The handoff must include:

- Files created, changed, preserved, and intentionally not changed.
- Settings scopes changed (user, project-shared, project-local, managed request, MCP scope).
- Checks run and actual pass/fail/not-run results.
- Commands and concise evidence for failures.
- Permissions granted, denied, or left for confirmation.
- MCP/plugin/CI/scheduled integrations configured, if any.
- Manual steps still required (authentication, marketplace trust, app approval, secrets, CI secrets).
- Known platform/version limitations.
- What should be committed versus kept local.
- How to undo the approved changes.
- Outstanding human decisions.

Use [`../09-templates/22-setup-validation-report-template.md`](../09-templates/22-setup-validation-report-template.md).

## Official references

- [Settings and diagnostics](https://code.claude.com/docs/en/settings)
- [Hooks reference and Windows behavior](https://code.claude.com/docs/en/hooks)
- [Troubleshooting](https://code.claude.com/docs/en/troubleshooting)
- [Memory and instruction-file audit](https://code.claude.com/docs/en/memory)


## Subscription usage settings are out of project scope

If usage efficiency is part of the setup, validate only project-local artifacts such as concise instructions, work-package templates, and session handoff workflows. Do not change subscription tier, usage credits, API billing, payment method, auto-reload, or spend limits. Those changes occur outside the repository and require a separate, explicit account-owner decision. For operational guidance, see [`../13-usage-efficiency/`](../13-usage-efficiency/01-subscription-usage-model.md).
