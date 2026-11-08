# Claude Subscription Usage Model

## Purpose

Explain and govern efficient use of Claude Code when the developer is using a Claude subscription (rather than metered API billing). This discipline focuses on **subscription usage limits**, not only the context-window size.

## 1. Distinguish the two limits

| Limit | What it controls | What helps |
|---|---|---|
| Subscription usage limit | How much Claude activity is available over the plan's applicable time periods | Choose efficient models/effort, reduce unnecessary work, plan tasks, monitor Settings > Usage |
| Context/length limit | How much information can be active in one conversation | Keep sessions focused, use `/clear` between tasks, use `/compact` when continuing the same task, retrieve only relevant files |

A full context window and an exhausted subscription allowance are not the same problem. Context management can improve both, but clearing a conversation does **not** reset the subscription allowance.

## 2. Subscription usage is shared

Anthropic's current consumer-plan guidance says usage across Claude surfaces such as claude.ai, Claude Code, and Claude Desktop counts toward shared account limits. Paid-plan limits can include a five-hour session allowance and a weekly allowance; exact behavior differs by plan and can change. Some plans have additional model-specific or feature-specific limits.

Do not assume a new terminal, new Claude Code session, new project, or `/clear` gives a fresh subscription allowance. These actions create a cleaner working context; they do not reset shared account usage.

Use **Settings → Usage** as the account-level source of truth for current and weekly usage and reset timing. Do not infer remaining allowance from message count, token count, context-window percentage, or a `/cost` command intended for API-key billing.

## 3. Confirm the billing route

Claude Code can authenticate through a Claude subscription or through an API/provider credential. Check the active login route before diagnosing usage:

- Confirm the intended Claude account is selected.
- Check whether an `ANTHROPIC_API_KEY` environment variable or other provider configuration is overriding subscription authentication.
- Never print, copy, commit, or share credential values while checking configuration.
- If the session uses an API key, usage is metered/billed differently from subscription quota. Keep subscription and API billing diagnostics separate.

Do not change authentication or enable paid usage credits without the account owner's explicit decision. Usage credits are pay-as-you-go and can create charges beyond the subscription fee.

## 4. Factors that affect consumption

Anthropic identifies factors including message length, attachment size, current conversation length, tool use, model choice, effort level, artifact use, and multi-step work such as code execution and browsing. In Claude Code, the complete conversation, project instructions, files read, and tool results can all contribute to later turns.

Practical consequence: the goal is not merely fewer messages. The goal is to reduce unnecessary model work, repeated discovery, redundant context, excessive output, and avoidable retries while still completing the task correctly.

## 5. Account-specific configuration

At onboarding, record only the information needed for advice:

- Plan category as stated by the user (do not guess).
- Billing route: subscription, API key/provider, or organization-managed.
- Whether Claude app usage is also heavy during the same reset period.
- Primary Claude Code model and effort level used for routine work.
- Whether usage credits are enabled (yes/no/unknown; do not expose billing details).
- Current reset information only when the user chooses to provide it.

Do not hardcode plan allowances, model names, reset hours, or usage-credit rules into project instructions. Verify current plan documentation and the user's Settings → Usage page when needed.

## 6. Operational policy

1. Check the usage dashboard before a planned intensive work block and when warnings appear.
2. Prefer a focused task brief and a bounded implementation group.
3. Select an appropriate model and effort level before work begins.
4. Avoid unnecessary tool output, broad repository scans, repeated full-file reads, and unrelated follow-up work.
5. Use subagents, agent teams, SkillOpt, and multi-step automation only when their benefit justifies their additional usage.
6. Save durable project state before starting a fresh session.
7. Do not promise that a workflow will fit within a fixed number of prompts or a precise quota amount; subscription metering is dynamic.

## Official references

- [Usage and length limits](https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work)
- [Claude Code usage limits for subscription plans](https://support.claude.com/en/articles/11145838-use-claude-code-with-your-pro-max-or-ultra-plan)
- [Usage limit best practices](https://support.claude.com/en/articles/9797557-usage-limit-best-practices)
- [Models, usage, and limits in Claude Code](https://support.claude.com/en/articles/14552983-models-usage-and-limits-in-claude-code)
