# Changelog

All notable changes to PEOF are recorded here. Dates use ISO 8601.

## 1.5.0 — 2026-11-07

### Added
- Dedicated `13-usage-efficiency/` discipline focused on Claude subscription usage limits and work efficiency, not only context-window management.
- Explicit distinction between subscription usage limits, context/length limits, and API/provider billing.
- Guidance on shared usage across Claude surfaces, plan-specific reset behavior, account usage monitoring, and authentication-route checks.
- Bounded task/session strategy, prompt/context hygiene, model/effort routing, tool-output/MCP efficiency, and subagent/parallelism cost controls.
- Repository-backed project memory and a repeatable session handoff/recovery workflow.
- Usage-aware SkillOpt and agentic workload budgeting, including small pilots, one-skill-at-a-time defaults, and caps on tasks, iterations, and concurrency.
- Four templates: session handoff, work-package brief, usage-efficiency review, and SkillOpt run budget/approval.
- Two Claude Code skills: `peof-session-handoff` and `peof-usage-efficient-development`.

### Changed
- Updated Claude Code integration and starter instructions to keep always-loaded context concise and load PEOF documents selectively.
- Updated SkillOpt cost guidance to treat model-backed experiments as consumers of subscription allowance where subscription authentication is used.
- Updated framework charter and package documentation with explicit no-reset and no-automatic-billing principles.

### Important operating notes
- Starting a new session or using `/clear` does not reset shared account subscription usage. It only creates a cleaner conversation context.
- Anthropic plan limits and usage factors can change; use the current account Settings → Usage page and current official Help Center docs.
- PEOF does not promise a fixed prompt count or exact quota savings. Subscription metering is dynamic and may be shared across Claude web, Desktop, and Code.
- Usage credits/API billing are separate paid consumption paths and must not be enabled automatically.

## 1.4.0 — 2026-11-07

### Added
- First-class Microsoft SkillOpt integration as an external, separately pinned source checkout.
- Dedicated `12-skillopt-integration/` discipline covering architecture, source checkout/version pinning, research engine, SkillOpt-Sleep, project-aware benchmark adapters, backend/isolation boundaries, data governance/cost, staged adoption/multi-skill governance, operations, upgrades, and pilot acceptance.
- Six SkillOpt-specific templates: integration profile, research experiment plan, Sleep run approval, project benchmark task, improvement proposal, and run/adoption receipt.
- Claude Code starter skill `peof-skillopt-operations` for governed SkillOpt operations.
- Explicit distinction between SkillOpt research engine and SkillOpt-Sleep; source-derived limits around project scope, backend isolation, preview status, and package/source differences.

### Changed
- Updated Agentic Engineering lifecycle, evaluation, usage feedback, controlled evolution, adoption/rollback, and observability to use SkillOpt where appropriate.
- Updated Claude Code integration to treat SkillOpt as a supported external implementation rather than optional reference-only material.
- Updated README, charter, package inventory, and review report.

### Governance and compatibility notes
- SkillOpt source code is not bundled in this PEOF archive; the integration guide clones it separately and records the exact commit.
- The research engine and SkillOpt-Sleep are separate workflows and must not be conflated.
- SkillOpt-Sleep remains documented by Microsoft as a preview; current source and package capabilities must be checked at install/upgrade time.
- PEOF keeps auto-adoption disabled by default and requires human approval for publication of shared/product-critical skills.
- A project-specific benchmark adapter is required for credible end-to-end repository evaluation; `--project` in Sleep does not alone prove replay access to source files or tools.

## 1.3.0 — 2026-11-07
- Added the Agentic Engineering discipline, evaluation/benchmarking, usage feedback, controlled skill evolution, versioning/adoption/rollback, observability, and Microsoft SkillOpt reference notes.
- Added six reusable agent/skill templates and extended Claude Code, quality, governance, and adoption documentation.

## 1.2.0 — 2026-11-07
- Expanded Claude Code project bootstrap, environment discovery, permissions, optional integrations, approval, validation, and cross-platform guidance.

## 1.1.0 — 2026-11-07
- Added current-state assessment, product profile, dependency matrix, modernization, data governance, multi-product, and operations coverage.

## 1.0.0 — 2026-11-07
- Initial product engineering framework package.
