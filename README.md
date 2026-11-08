# Product Engineering Operating Framework (PEOF)

**A reusable, discovery-led operating system for building, operating, improving, and modernizing software products.**

**Current framework version:** 1.5.0 — see [`CHANGELOG.md`](CHANGELOG.md) for release history.

## What this framework is

PEOF connects product strategy, discovery, requirements, user experience, architecture, implementation, quality engineering, release, production operations, and continuous improvement. It supports greenfield products, existing products, modernization, framework migration, and multiple products with tailored profiles.

It also provides Claude Code bootstrap, Agentic Engineering governance, Microsoft SkillOpt integration, and now a usage-efficiency discipline for developers working within Claude subscription limits.

## Critical operating rule: discover before configuring

Do not install, migrate, generate project-specific files, or change a working product based only on this framework. Begin with [`01-discovery/01-discovery-protocol.md`](01-discovery/01-discovery-protocol.md). Establish the engagement type, inspect available evidence, ask only relevant questions, document unknowns, and present a recommended configuration and adoption/migration plan. Obtain explicit approval before making changes to an existing project.

## Start here

1. Read [`FRAMEWORK_CHARTER.md`](FRAMEWORK_CHARTER.md) and [`00-operating-model/01-principles.md`](00-operating-model/01-principles.md).
2. Follow [`01-discovery/01-discovery-protocol.md`](01-discovery/01-discovery-protocol.md).
3. Select the appropriate path using [`01-discovery/04-engagement-routing.md`](01-discovery/04-engagement-routing.md).
4. Assess current maturity and create a product-specific profile.
5. Present findings, target state, risks, dependencies, and phased plan for approval.
6. Use the relevant greenfield, existing-product, modernization, or migration playbook.
7. Select only the templates needed from `09-templates/`.
8. If Claude Code setup is requested, follow `08-claude-code/09-project-bootstrap-workflow.md` and obtain approval before writing.
9. If agentic assets are used, follow `11-agentic-engineering/`.
10. If automated skill optimization is useful, follow `12-skillopt-integration/01-integration-architecture.md` and the selected workflow. Pin SkillOpt, verify its current capabilities, and keep candidate skills staged until approval.
11. If using Claude through a subscription and usage limits are a concern, follow `13-usage-efficiency/01-subscription-usage-model.md` and the session strategy. The starter skills `peof-session-handoff` and `peof-usage-efficient-development` operationalize the workflow. Keep durable project state in repository files so new sessions can start cleanly.

## Package map

| Folder | Purpose |
|---|---|
| `00-operating-model/` | Principles, lifecycle, roles, decision rights, tailoring |
| `01-discovery/` | Discovery, question bank, maturity assessment, engagement routing |
| `02-product/` | Product strategy, requirements, roadmap, launch, lifecycle |
| `03-design-architecture/` | UX, architecture, technical design, security, privacy, data governance |
| `04-delivery/` | Feature grouping, implementation planning, engineering standards, technical debt |
| `05-quality/` | Testing strategy, quality gates, readiness criteria |
| `06-release-operations/` | CI/CD, release, production operations, incidents, reliability |
| `07-adoption-migration/` | Greenfield, existing-product adoption, modernization, migration, multi-product |
| `08-claude-code/` | Claude Code bootstrap, environment inventory, permissions, integrations, validation, starter kit |
| `09-templates/` | Product, engineering, operations, migration, agentic, SkillOpt, and usage-efficiency templates |
| `10-governance/` | Metrics, risk, decisions, framework change management |
| `11-agentic-engineering/` | Agent/skill lifecycle, design, evaluation, usage learning, controlled evolution, versioning, observability |
| `12-skillopt-integration/` | Microsoft SkillOpt source integration, research engine, Sleep, project adapters, backend isolation, privacy, adoption, operations |
| `13-usage-efficiency/` | Subscription usage model, task/session strategy, context hygiene, model/effort choice, tools, delegation, handoff, monitoring, SkillOpt workload budgets |

## What's new in v1.5.0

Version 1.5.0 adds a dedicated Claude subscription usage-efficiency discipline. It distinguishes subscription usage limits from context-window limits and API/provider billing; explains that new sessions and `/clear` do not reset shared account usage; and provides practical controls for bounded work packages, model/effort selection, selective context retrieval, concise tool output, deliberate subagent use, durable project memory, and session handoffs. It also adds usage-aware budget controls for model-backed SkillOpt experiments.

**Important:** PEOF cannot guarantee a fixed number of prompts or exact quota savings. Anthropic's usage allowances and metering can vary by account, plan, model, effort, feature, and time. The current Settings → Usage page and current official documentation are authoritative. Do not enable usage credits or API billing without explicit account-owner approval.

## What's new in v1.4.0

Version 1.4.0 integrates the Microsoft SkillOpt repository as PEOF's supported external skill-optimization implementation. It separates the research engine from SkillOpt-Sleep, documents source-checkout installation and exact commit pinning, adds project-aware benchmark adapter requirements, and defines explicit backend/isolation boundaries. The SkillOpt source code is not bundled in this PEOF ZIP.

## Research engine vs. SkillOpt-Sleep

- **Research engine:** optimize and evaluate skills against explicit task/benchmark environments. Use a custom project adapter and isolated task workspaces for true repository-level coding tasks.
- **SkillOpt-Sleep:** learn from supported local coding-agent sessions, replay recurring tasks through a selected backend, and stage candidate memory/skill updates. Its `--project` scope does not by itself guarantee repository file/tool access. Backend behavior varies.

Do not conflate the two workflows or assume Sleep is a repository-aware coding benchmark. See the integration folder for detailed controls.

## Usage efficiency: important distinctions

- `/clear` removes chat history for a clean task context; it does not reset a shared subscription allowance.
- `/compact` summarizes the current session; it does not reset subscription usage.
- A new Claude Code session can reduce repeated irrelevant context but still uses the same account-level allowance.
- Claude web, Desktop, and Code can share usage limits depending on plan/account configuration.
- Use `Settings → Usage` to monitor account limits. Do not infer subscription quota from API `/cost` output.
- SkillOpt and multi-agent evaluation can consume additional model usage; pilot with small, approved batches.

## Operating principles

- The framework adapts to each product; it does not force every product into the same process.
- Universal standards remain separate from product-specific configuration.
- Existing projects are assessed and migrated incrementally; working files are preserved unless explicitly approved for change.
- Skills and agents are versioned assets, not automatically trusted outputs.
- Evaluation is evidence, not a guarantee. Maintain clean task splits and report uncertainty.
- Candidate skills are staged; human approval is required before adoption by default.
- Session harvesting, external transmission, scheduling, multi-skill fan-out, and usage credits are opt-in and require data/cost review.
- Optimize usage by reducing waste, not by skipping required engineering quality and safety controls.

## Profiles and versioning

Maintain separate Product Profile, Developer Environment Profile, and SkillOpt Integration Profile. Version product-specific adaptations independently from the shared framework. See [`09-templates/11-product-profile-template.md`](09-templates/11-product-profile-template.md), [`09-templates/21-developer-environment-profile-template.md`](09-templates/21-developer-environment-profile-template.md), and [`09-templates/29-skillopt-integration-profile-template.md`](09-templates/29-skillopt-integration-profile-template.md).
