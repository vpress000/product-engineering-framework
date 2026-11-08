# Optional Claude Code Capabilities and Integrations

## Purpose

Provide a selective capability menu for a project bootstrap. These features are opt-in; do not install, configure, or enable them merely because they appear in this catalogue.

## Selection rule

Ask one multi-select question after core discovery. Explain each option briefly. Ask follow-up questions only for options selected. If the user selects none, create none.

## Optional capability catalogue

| Capability | When it helps | Follow-up needed | Default stance |
|---|---|---|---|
| Repeatable project workflow | A multi-step process is reused | Skill or subagent? Trigger/invocation preference? Inputs and outputs? | Create only workflows requested or clearly agreed |
| Personal prompt library | Existing prompts should become reusable skills | Path, access permission, list of prompts, which to scaffold | Read/list first; user selects items; never bulk-copy by default |
| Review before completion | Non-trivial work needs a separate review | Built-in review workflow or read-only reviewer agent? Which work qualifies? | Use an explicit workflow, not a hook on every edit |
| Context/auto-compaction preferences | Long sessions need context management | Desired behavior and available current settings | Verify current feature and settings; do not invent a threshold key |
| Saved plan files | Plans need to persist across sessions | Directory, naming, git-tracking preference | Create only if requested; confirm ignored/committed behavior |
| Output style | User wants a stable response format | Existing supported style or custom style? | Use a currently supported option only |
| Plugin | A packaged capability is useful | Exact plugin/marketplace, trust review, install scope, permissions | Inspect and explain before installation |
| MCP service | Claude needs access to an external service | Exact service, functions needed, scope, authentication, data accessed | Only services explicitly named by the user |
| CI integration | Automated review or workflow in CI is useful | GitHub/GitLab/other, events, permissions, secret storage, cost | Least privilege; no secrets in repo; user approves workflow changes |
| Scheduled/recurring task | A repeated check or task has clear value | Cadence, time zone, execution environment, data access, notification target | Verify the available surface and whether the machine must remain online |
| Git worktrees | Parallel sessions need isolated working copies | Git availability, base branch, ignored files needed, cleanup policy | Use only when isolation is useful; avoid copying secrets |
| Agent teams | Multiple Claude sessions need shared task coordination | Why subagents/worktrees are insufficient; cost and limitations | Experimental/opt-in only; never enable by default |
| Browser or desktop integration | A task needs interactive app/browser context | Exact app/site, permissions, data access, surface | Explicit opt-in, least scope, user handles authentication when prompted |
| Skill evaluation and optimization | Shared skills need repeatable behavioral evaluation or bounded improvement | Asset scope, baseline, evaluation tasks/splits, model/provider, budget, data boundary, approval owner | Start with manual evaluation; optimize only when a checkable signal and valid task set exist |
| Usage-driven skill learning | Recurring work or agent failures should inform improvements | Approved session sources, date range, redaction/review, provider, retention, cadence, budget | Opt-in only; no background harvesting or external transmission by default |
| Multi-skill staging/adoption | Several skills need independent proposals and selective promotion | Canonical paths, per-skill baselines, selection, lock/backup/recovery behavior | Each skill needs separate evidence; explicit subset approval; fail closed on ambiguity |

## Follow-up rules by capability

### Skills and subagents

- Prefer a skill for reusable procedural workflows.
- Prefer a subagent for a bounded specialist role that benefits from an isolated context or restricted tools.
- Start with no more than three project skills unless the user asks for more.
- Keep subagent tool permissions to the smallest documented allowlist that works.
- Keep side-effecting workflows such as deploy, publish, release, and data migration user-invoked only.

### Prompt libraries

- Read the specified prompt library only after the user identifies its path and grants access.
- List available prompts and summarize purpose without copying private or irrelevant material.
- Ask which prompts to convert.
- Check whether an equivalent global skill already exists before creating another.

### Review workflow

- Use a documented review command only if available in the installed version/surface.
- Otherwise propose a read-only reviewer agent or explicit checklist.
- Review should compare the diff to requirements, tests, security/privacy expectations, and project conventions.
- Do not use a per-edit hook to invoke a language model for every small change unless there is a demonstrated need and cost/latency has been accepted.

### Hooks

- Add hooks only for deterministic, repeatable checks or guardrails.
- Each hook requires purpose, event, matcher, command, expected input/output, timeout, failure behavior, and test cases.
- Review the script itself; hooks execute with the user's permissions.
- Test one allowed case and one blocked case where relevant.
- Do not install notifications unless specifically requested.

### MCP servers

- Ask which named service(s) are required and which tools/actions Claude needs.
- Explain local, project, and user scopes using current docs; local scope is documented as the default for `claude mcp add` and is stored in Claude's local application state.
- Use project scope only when the team intentionally wants a shared project configuration.
- Never commit credentials. Do not reveal tokens or inspect raw credential stores.
- Verify authentication separately after configuration and record who owns the connection.

### Plugins

- Distinguish a Claude Code plugin from an IDE extension, MCP server, or standalone skill.
- Identify the exact marketplace/plugin and inspect its components, permissions, sources, and trust implications.
- Provide installation commands and scope as a proposal; install only after approval.
- Prefer a standalone skill or MCP server when that is all the use case needs.

### CI integration

- Identify the repository host and current CI conventions first.
- Propose narrowly scoped workflow permissions and only the events needed.
- Store credentials in the CI platform's secret manager, not source control or prompt files.
- Include cost, concurrency, review, and failure behavior.
- Test with a safe branch or dry-run where supported.

### Scheduled tasks

- Decide whether the task needs local files, browser/app access, or must run while the developer's machine is off.
- Select a supported native scheduler, desktop feature, CI workflow, or external cloud routine only after verifying current capabilities and access policies.
- Define cadence, time zone, expiration, retry behavior, output destination, data scope, and cancellation method.
- Never create a recurring task without explicit user authorization.

### Worktrees

- Confirm this is a Git repository and inspect the working tree before creating one.
- Identify ignored files required to run the project; include only explicitly approved, non-secret items. If the current worktree workflow supports `.worktreeinclude`, propose it only for the named files and verify the exact syntax.
- Explain branch creation, shared settings behavior, conflict risk, cleanup, and how to retain changes.
- Never copy `.env` or credentials into a worktree automatically.

### Agent teams

- Current official documentation describes agent teams as experimental and disabled by default. Recheck before use.
- Compare with subagents and worktrees first.
- Explain token usage, coordination overhead, known limitations, permissions, and file-conflict risks.
- Enable only when explicitly selected and supported by the installed version.

### Skill optimization and usage learning

- Distinguish benchmark-driven skill optimization from usage-driven session learning; do not assume one tool or package provides both in the same way.
- Confirm the installed version, release channel, dependencies, supported agent/session sources, model backends, and integration method.
- Start with a small, non-sensitive benchmark and a mock/no-network or handoff mode where the tool supports it. Verify actual network behavior rather than assuming a mode is isolated.
- Establish a baseline, fixed task manifest, split/exposure ledger, acceptance gate, and cost ceiling before optimization.
- Treat session harvesting as an explicit data-processing activity. Review and redact derived tasks before sending them to a provider; automated secret redaction is not a guarantee.
- Keep candidate files in staging. Require a pinned live baseline, candidate hash, per-skill evaluation, backup, receipt, and explicit adoption choice.
- Do not enable automatic adoption, scheduled harvesting, or multi-skill fan-out by default.
- See `../11-agentic-engineering/` for lifecycle, evaluation, privacy, evolution, and rollback requirements.

## Output

Produce an optional-capability selection record with: selected item, rationale, scope, dependencies, risks, proposed files/settings, approval status, validation method, and items deliberately not enabled.

## Official references

- [Skills](https://code.claude.com/docs/en/skills)
- [Subagents](https://code.claude.com/docs/en/sub-agents)
- [Hooks](https://code.claude.com/docs/en/hooks)
- [MCP](https://code.claude.com/docs/en/mcp)
- [Plugins](https://code.claude.com/docs/en/plugins)
- [Worktrees](https://code.claude.com/docs/en/worktrees)
- [Agent teams](https://code.claude.com/docs/en/agent-teams)
- [Claude Code Desktop and scheduled tasks](https://code.claude.com/docs/en/desktop)
