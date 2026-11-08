# Subagent and Parallelism Cost Control

## Purpose

Use delegation only when it improves quality, isolation, or throughput enough to justify its additional model usage.

## 1. Subagents are not free quota multipliers

Subagents have separate contexts and can reduce noise in the primary conversation. They also consume additional model usage. Agent teams and broad parallel work can be more expensive because multiple sessions/models are active. Do not assume delegation reduces total subscription usage.

## 2. Use a subagent when

- Research spans many files and a concise synthesized report will avoid loading all raw evidence into the main conversation.
- Two or more tasks are genuinely independent and can run in parallel.
- A fresh, independent review materially reduces bias or risk.
- A specialist can work within a tightly bounded scope and return a short, structured result.

## 3. Avoid delegation when

- The task is small or mechanical.
- Work is sequential and each stage depends on the previous full output.
- Multiple agents would edit the same files.
- The main task context is already small and clear.
- Agent coordination overhead exceeds the expected benefit.
- The user has not approved the use of parallel agents for sensitive or high-cost work.

## 4. Default limits

For quota-conscious solo development:

- Start with the main agent only.
- Use one read-only research subagent only when repository discovery is substantial.
- Add a second reviewer only for high-impact changes or when a clean independent review is worth the usage.
- Avoid agent teams for routine feature work.
- Avoid broad fan-out prompts such as "inspect everything" or "improve all skills".

These are PEOF defaults, not technical limits imposed by Claude Code. Tailor them to the account, task, and risk.

## 5. Delegation contract

Every subagent task should state:

- One objective and bounded scope.
- Read/write permissions.
- Files or directories in scope.
- Questions to answer.
- Exact output format and maximum useful length.
- Whether it may execute commands.
- Prohibited side effects.

The parent session should request a synthesized result, not a transcript of every search and thought. Avoid having multiple agents repeat the same inspection.

## Official reference

- [How and when to use subagents in Claude Code](https://claude.com/resources/articles/subagents-in-claude-code)
