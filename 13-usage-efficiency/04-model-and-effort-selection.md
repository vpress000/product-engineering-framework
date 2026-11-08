# Model and Effort Selection for Subscription Efficiency

## Purpose

Match model capability and reasoning effort to task complexity, risk, and ambiguity.

## 1. Select before the work begins

At the start of a work package:

1. Check which models are currently available to the signed-in account using the supported model picker/`/model` command.
2. Select a model appropriate to the work.
3. Select a suitable effort level if the model exposes one.
4. Avoid changing model or effort repeatedly mid-session unless the task changes materially or quality requires it.

Exact model names, availability, and effort controls change. The installed `/model` experience and current official docs are authoritative.

## 2. Practical routing matrix

| Task category | Starting choice | Escalate when |
|---|---|---|
| Mechanical edits, renames, simple explanations, formatting | Most efficient available model; low effort where supported | The requested change reveals hidden dependencies or ambiguity |
| Routine feature implementation, tests, known bug fixes | Efficient general coding model; low/medium effort | Multiple modules, unclear behavior, or non-obvious failure appears |
| Cross-cutting refactor, difficult debugging, architecture decision | Strong reasoning model; medium/high effort appropriate to risk | Evidence shows more analysis is necessary |
| Security-sensitive or high-impact design review | Strong reasoning model and explicit review criteria | Use independent review where the additional usage is justified |
| Large research or exploration task | Scope the research first; consider a read-only subagent only if it will avoid flooding the main context | Multiple independent areas need parallel inspection |

This is a routing policy, not a fixed model-name mandate. Anthropic's current Claude Code usage guidance describes Sonnet as suitable for most coding, Opus for harder reasoning, and Haiku for quick mechanical work where available; verify the current account's model menu.

## 3. Avoid unnecessary high-effort usage

- Do not use the most expensive/highest-effort option by default for every task.
- Do not lower effort on safety-critical, ambiguous, or architecture-changing work merely to save quota.
- Ask for a concise plan before an expensive multi-step task.
- Use a smaller first pass for diagnosis; escalate after identifying the difficult part.
- Avoid repeating high-effort analysis when the decision and evidence are already documented.

## 4. Model switching and cache behavior

Changing models or effort mid-session can cause the prompt cache to be rebuilt. Set the expected model and effort at the beginning when practical. If a task legitimately needs a stronger model, change it and proceed; correctness and safety take precedence over cache preservation.

## 5. No false precision

Do not promise that a model/effort selection will consume an exact number of subscription messages or a specific percentage of the allowance. Plan metering is dynamic and account-specific.

## Official references

- [Models, usage, and limits in Claude Code](https://support.claude.com/en/articles/14552983-models-usage-and-limits-in-claude-code)
- [Usage limit best practices](https://support.claude.com/en/articles/9797557-usage-limit-best-practices)
