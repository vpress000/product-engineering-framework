# Product Engineering Operating Framework (PEOF) — Charter

**Framework version:** 1.5.0  
**Release date:** 2026-11-07

## Mission

Provide a reusable, adaptable operating model for discovering, building, delivering, operating, modernizing, and continuously improving software products. Make product engineering systematic without imposing unnecessary bureaucracy.

## Applicability

PEOF supports greenfield products, existing products, modernization, engineering transformation, framework migration, and multi-product environments. It is suitable for solo developers and teams when tailored to product complexity, risk, and regulatory needs.

## Coverage

The framework covers product discovery and strategy, requirements, UX, architecture, implementation planning, feature grouping, engineering standards, quality, release, operations, governance, and continuous improvement. It also defines safe Claude Code setup, Agentic Engineering, Microsoft SkillOpt integration, and subscription-usage-efficient session practices.

## v1.5.0 decision: Claude subscription usage efficiency

PEOF v1.5 adds a dedicated discipline for managing work when Claude Code is used through a Claude subscription. It distinguishes account-level subscription usage limits from context-window limits and API/provider billing. It recognizes that usage across Claude product surfaces may be shared by the account and that starting a new session does not reset that shared allowance.

The framework therefore emphasizes bounded work packages, concise always-loaded instructions, selective context retrieval, proportionate model/effort selection, efficient tool output, deliberate subagent/parallelism use, repository-backed project memory, and explicit handoffs. It also requires small, approved budgets for model-backed SkillOpt experiments.

PEOF does not promise exact token savings or fixed prompt counts because plan metering and limits are dynamic and account-specific. The current Settings → Usage page and current official Anthropic documentation are authoritative for account limits. Usage credits and API billing require explicit account-owner approval.

## v1.4.0 decision: Microsoft SkillOpt integration

PEOF v1.4 uses Microsoft's SkillOpt repository as the supported external implementation for automated skill optimization where it is justified. The integration distinguishes:

- the SkillOpt research engine for benchmark-driven skill training/evaluation; and
- SkillOpt-Sleep, a separate preview workflow for usage-driven session harvesting, task mining, replay, consolidation, staging, and reviewed adoption.

The source checkout is kept separate from product source and pinned to an exact commit. The PEOF framework does not include or vendor Microsoft's code. Project-aware source-code evaluation requires a benchmark adapter/execution environment that exposes a controlled product snapshot and independently checks outcomes. A Sleep `--project` scope alone is not proof of repository access.

PEOF remains responsible for project/task context, evaluation split integrity, data classification, security, approval, asset versioning, adoption, monitoring, and rollback. SkillOpt supplies its documented execution/optimization mechanisms. SkillOpt-Sleep's preview status and changing package/source capabilities must be rechecked before use.

## Non-goals

- Mandating SkillOpt for products that do not need automated skill optimization.
- Treating a mock run, a single held-out gain, or an optimizer gate as proof of universal improvement.
- Automatically harvesting sessions, transmitting sensitive content, scheduling runs, or adopting skills without project approval.
- Replacing product engineering governance with an optimizer's defaults.
- Bundling the Microsoft SkillOpt repository into PEOF.
- Promising a fixed subscription allowance, exact token savings, or uninterrupted availability.
- Treating a new Claude Code session, `/clear`, or `/compact` as a reset of the account's shared subscription usage.

## Operating principles

1. Discover before configuring or migrating.
2. Separate verified facts, user-provided information, assumptions, and recommendations.
3. Preserve existing working practices unless a controlled change is approved.
4. Make requirements traceable to implementation and tests.
5. Group related features logically for collective planning, implementation, review, and testing.
6. Use least privilege and explicit approval for side effects.
7. Evaluate agents/skills against representative tasks and preserve uncontaminated test splits.
8. Stage optimization candidates and adopt only exact approved hashes.
9. Retain backups, receipts, and rollback capability.
10. Use focused sessions, persistent project state, and selective context retrieval to reduce waste without weakening quality.
11. Use subagents, parallelism, and SkillOpt runs only when expected benefits justify their added usage.
12. Continuously improve the framework without making it heavier than the product requires.

## Change authority

Changes to the shared framework require a recorded framework change proposal. Product-specific adaptations are governed by the product owner and must not silently become global standards. Adoption of optimized project skills follows the asset owner/approval policy in the Agentic Engineering discipline. Account billing and usage-credit settings remain under the account owner's control.
