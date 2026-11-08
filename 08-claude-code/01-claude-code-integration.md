# Claude Code Integration Guide

## Purpose

Use Claude Code to help apply the framework consistently while keeping project decisions, security, quality, and approval under appropriate human control.

## Integration principles

- Treat the framework as guidance and context, not authorization to change files or production systems.
- Keep universal framework documents separate from product-specific project instructions.
- Put only durable, high-value project context in the root `CLAUDE.md`.
- Use modular rules for scoped standards, skills for repeatable workflows, agents for bounded specialist tasks, and hooks for deterministic automation only when appropriate.
- Avoid duplicated or contradictory instructions.
- Require review and verification of AI-generated changes.
- Never expose secrets, sensitive customer data, or restricted material in prompts or generated artifacts.

## Recommended separation

**Framework library:** reusable standards, playbooks, and templates.

**Product profile:** product purpose, users, scope, architecture, technology, constraints, decision owners, and approved tailoring.

**Repository instructions:** concise instructions Claude needs while working in that repository, including links to relevant project documentation and quality commands.

**Skills:** repeatable workflows such as requirements review, architecture assessment, feature grouping, test planning, and release validation.

**Agents:** specialist roles with narrow responsibilities and clear inputs/outputs; use them only when delegation improves quality or separation of concerns.

## PEOF Claude Bootstrap

Use the separate bootstrap workflow whenever Claude Code environment setup or repository onboarding is requested:

- `05-environment-discovery-and-inventory.md`
- `06-permissions-and-configuration-management.md`
- `07-optional-capabilities-and-integrations.md`
- `08-setup-validation-and-handoff.md`
- `09-project-bootstrap-workflow.md`
- `10-cross-platform-environment-guidance.md`
- `11-official-documentation-reference.md`

The ready-to-paste first message is in `starter-kit/PROJECT-SETUP-FIRST-MESSAGE.md`; the reusable workflow skill is in `starter-kit/skills/peof-project-bootstrap/SKILL.md`.

## Safe operating sequence

1. Read the product profile and the relevant framework pages.
2. Confirm task intent and scope.
3. Inspect the repository and identify relevant source-of-truth files.
4. Summarize findings and unknowns.
5. Propose a plan and identify files/systems to change.
6. Obtain approval where required by the project or user.
7. Make small, reviewable changes.
8. Run relevant tests and checks; report exact results and limitations.
9. Summarize changed files, decisions, risks, and follow-up work.

## Agentic engineering lifecycle

Claude Code assets are governed by the platform-independent discipline in `11-agentic-engineering/`. Skills, agents, prompt assets, and evaluation suites are versioned engineering assets, not disposable generated text. Use the lifecycle, design, evaluation, controlled evolution, adoption, rollback, and observability standards before sharing material assets across a project or team.

PEOF v1.4 supports Microsoft SkillOpt as its external skill-optimization implementation. Keep the SkillOpt source checkout separate from the product repository, pin its exact commit, and select the research engine, SkillOpt-Sleep, or both explicitly. Sleep is a preview and backend isolation varies. Use the PEOF integration guides under [`12-skillopt-integration/`](../12-skillopt-integration/01-integration-architecture.md); do not assume project scope means repository access, and do not adopt candidates without human approval.

## Existing repositories

Start read-only. Inventory existing `CLAUDE.md`, `.claude/` files, scripts, tests, local conventions, and reusable agentic assets. Reconcile before adding new instructions. Do not overwrite existing Claude configuration blindly. Record existing skills/agents, owners, versions where known, dependencies, permissions, usage, and evaluation evidence before deciding to retain, improve, consolidate, replace, archive, or retire them.

## Current documentation check

Claude Code capabilities and configuration syntax can change. Before generating executable configuration, consult current official Anthropic Claude Code documentation for supported `CLAUDE.md`, rules, skills, agents, hooks, permissions, and settings behavior. Do not invent frontmatter fields or assume an example remains current.

## Human approval boundaries

Require explicit authorization before destructive operations, bulk migrations, changing access controls, handling production secrets/data, deploying, modifying production infrastructure, accepting security/privacy risk, or changing significant architecture/product scope.

## Quality controls for AI-assisted changes

- Verify generated code against the actual codebase and requirements.
- Run relevant tests, static checks, and security checks.
- Inspect diffs for unrelated or unintended changes.
- Check dependency/license implications where relevant.
- Do not claim a check passed unless it was executed and the result was observed.
- Record assumptions and unresolved questions.


## Configuration scope and preservation

Keep user instructions/settings, shared project settings, project-local settings, managed policies, and MCP configuration separate. Inspect existing files before proposing changes. A user-level change requires separate approval because it may affect other projects. A local MCP server scope is not the same as project-local settings; consult the current MCP documentation. Never expose `~/.claude.json` or credential values.

Use current official documentation for the actual settings precedence and supported fields. Do not assume project settings can set user-only or managed keys, and do not assume every setting applies in local, cloud, or IDE surfaces identically.


## Subscription usage efficiency

When Claude Code is used through a Claude subscription, follow the dedicated [`13-usage-efficiency/`](../13-usage-efficiency/01-subscription-usage-model.md) discipline. Distinguish plan usage limits from the context window: `/clear` and fresh sessions remove irrelevant conversation history but do not reset account-level usage. Claude app, Desktop, and Code usage may share the plan allowance. Monitor the current account's Settings → Usage page; do not infer quota from prompt counts or API `/cost` output.

Use focused work packages, concise durable instructions, selective file retrieval, appropriate model/effort, bounded tool output, and deliberate delegation. Preserve continuity in repository-backed status and handoff files so fresh sessions do not need broad rediscovery. Avoid unnecessary agent teams and SkillOpt loops because model-backed parallel work can consume additional shared allowance. Never enable usage credits or API billing without explicit account-owner approval.
