# Usage Efficiency Review and Operations

## Purpose

Turn subscription usage observations into practical improvements without optimizing for quota at the expense of correctness, security, or maintainability.

## 1. When to review

Review after repeated early limit exhaustion, a large SkillOpt run, a major increase in multi-agent use, a new Claude Code configuration, or a sustained change in product workload.

## 2. Review questions

- Which work types consumed the most account capacity?
- Were sessions focused on one coherent work package?
- Did Claude repeatedly rediscover known facts?
- Was `CLAUDE.md` bloated or duplicated with other documents?
- Were large files, logs, or tool results added unnecessarily?
- Were model and effort choices proportionate?
- Did subagents or agent teams provide enough benefit to justify extra use?
- Did SkillOpt runs have explicit task/iteration/concurrency limits?
- Was project memory sufficient to start fresh sessions efficiently?
- Was Claude usage shared with other product surfaces during the same period?

## 3. Improvement actions

Prioritize changes with the highest expected savings and lowest quality risk:

1. Fix vague task briefs and repeated clarification loops.
2. Shorten always-loaded instructions and move workflows into on-demand skills.
3. Add or improve session handoffs.
4. Narrow repository discovery and command outputs.
5. Adjust model/effort routing.
6. Reduce unnecessary agent/subagent concurrency.
7. Add caps and small pilots to SkillOpt/benchmark runs.
8. Reassess MCP/tools that are loaded but rarely used.

## 4. What not to optimize away

Do not skip security reviews, required regression tests, data protection, acceptance criteria, or human approval merely to conserve usage. Reduce waste by targeting scope and evidence, not by lowering the quality bar.

## 5. Success measures

Use qualitative and operational measures:

- Fewer repeated discovery steps.
- More work packages completed per available usage period.
- Fewer unnecessary retries and broad scans.
- Shorter, more useful session handoffs.
- Lower frequency of premature limit exhaustion for comparable work.
- Stable or improved test quality, defect rate, and acceptance outcomes.

Do not claim causal savings unless comparable work periods and task complexity are considered. Account limits may change independently of developer behavior.

## 6. Change control

Update project instructions, skills, agents, or automation only after review. Preserve a before/after example where practical and roll back changes that reduce task quality or reliability.
