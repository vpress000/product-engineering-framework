# Usage Monitoring and Workload Planning

## Purpose

Help developers understand and plan around the subscription allowance without pretending to predict an exact token or message budget.

## 1. Monitor the account-level source of truth

Use Claude **Settings → Usage** to review the current session allowance and weekly usage/reset information available for the account. Claude Code warnings are useful signals but do not replace the account dashboard.

Do not rely on a per-message token counter or API `/cost` output to estimate subscription quota unless current official documentation explicitly says it applies to the active billing route.

## 2. Record patterns, not secrets

A lightweight usage review may record:

- Date/work block.
- Plan category (optional; user supplied only).
- Work type (research, implementation, debugging, tests, documentation, SkillOpt).
- Model and effort used.
- Approximate task duration and completion outcome.
- Whether a warning/limit was reached.
- Likely cause: long context, large files, repeated scans, model/effort, multi-agent work, heavy tool loops, or use across other Claude surfaces.

Do not collect account identifiers, billing data, screenshots containing personal information, or credentials into the product repository.

## 3. Plan the work block

Before an intensive session:

1. Check current and weekly usage.
2. Choose the highest-value work package that fits the expected availability.
3. Set an appropriate model and effort at session start.
4. Avoid unrelated work and unnecessary agent fan-out.
5. Define a stopping point and produce a handoff if work must continue later.

When usage is low, prioritize planning, local deterministic checks, small edits, and tasks that do not require broad model-based exploration. Do not misrepresent local scripts as substitutes for required reasoning or verification.

## 4. Diagnose unexpectedly high usage

Review in this order:

1. Is the same account being used in Claude chat, Desktop, and Claude Code? These may share an allowance.
2. Is the active billing route a subscription or an API/provider key?
3. Did the session accumulate many files, tool outputs, and unrelated tasks?
4. Was a high-quota model or high effort used for routine work?
5. Were subagents, agent teams, SkillOpt loops, or repeated benchmark runs launched?
6. Were tools, web research, artifacts, or multi-step tasks used extensively?
7. Did the work include repeated retries caused by vague scope or insufficient acceptance criteria?

## 5. Do not bypass or misstate limits

- Starting a new session does not reset shared plan usage.
- Changing accounts, credentials, or billing route is not a usage optimization technique and can change billing.
- Do not enable usage credits, API billing, auto-reload, or a different paid tier without a deliberate account-owner decision.
- Plan limits and features can change; check the current Help Center and account Usage page.

## Official references

- [Usage and length limits](https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work)
- [Usage limit best practices](https://support.claude.com/en/articles/9797557-usage-limit-best-practices)
- [Manage usage credits for paid Claude plans](https://support.claude.com/en/articles/12429409-manage-usage-credits-for-paid-claude-plans)
