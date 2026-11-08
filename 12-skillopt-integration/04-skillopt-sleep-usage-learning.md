# SkillOpt-Sleep: Usage-Driven Learning Workflow

## Purpose and status

Use SkillOpt-Sleep, where justified, to learn from recurring work recorded in supported coding-agent sessions and stage proposed memory/skill updates for review. Microsoft documents SkillOpt-Sleep as a **preview** deployment-time companion. Its interfaces, defaults, and backend support may change; validate the exact checked-out revision before every rollout or scheduled use.

SkillOpt-Sleep is distinct from the SkillOpt research engine. Microsoft's documentation states that the Sleep package has no runtime dependency on the research `skillopt/` package. Treat it as a separate workflow with its own config, state, backend, and data boundary.

## Documented cycle

```text
Harvest local sessions (read-only)
  → mine recurring task records
  → replay tasks using selected backend
  → reflect and propose bounded memory/skill edits
  → gate candidate on held-out tasks
  → stage reports and candidate artifacts
  → human review and explicit adoption
```

A normal `run` stages a proposal; it does not mean the project skill has been updated. A rejected proposal should remain rejected and its report should be inspected for useful failure evidence. A real-backend `dry-run` is not necessarily cost-free: it can still perform provider calls; it suppresses staging, not all model work.

## Distinguish source from backend

Transcript source and replay backend are independent selections. The source determines which local session history is harvested. The backend determines how mining, replay, judging, and reflection model calls are executed. `auto` source precedence is not equivalent to selecting every supported source. Verify the current CLI reference and select the intended source explicitly where scope matters.

## Important project-scope distinction

`--project PATH` scopes project transcript selection, target/state/staging paths as documented by the checked-out version. It does **not by itself guarantee that the replay model can read the repository, run the project's tests, use MCP tools, or perform end-to-end code changes**. Repository access and tool execution depend on the selected backend and its isolation model. For true repository-level benchmark evaluation, prefer the research engine with a project adapter or another explicitly validated repository execution harness.

Always provide an explicit `--target-skill-path` for the intended project skill. Do not assume the default target is a skill inside the current project. Confirm that the target file is the product skill, not the SkillOpt plugin's own workflow skill. The current source config also labels `replay_mode` as a report field and notes that fresh-worktree replay is not implemented in Sleep; do not mistake a setting label, project scope, or staging path for isolated repository execution.

## Recommended first-run sequence

1. Read the current official Sleep overview, safety notes, CLI reference, and backend-specific documentation for the pinned commit.
2. Confirm source paths and transcript scope. Start with one project and the narrowest scope.
3. Run `status` (read-only) and inspect the current configuration.
4. Run `harvest` or `dry-run` with the `mock` backend and small limits to inspect session/task counts. A mock run is a plumbing check, not proof of model quality.
5. Review harvested task records; remove secrets, customer data, proprietary details not approved for transmission, irrelevant sessions, and duplicate/contaminated tasks.
6. If using a real backend, use the reviewable task-file workflow supported by the checked-out version and explicitly mark the tasks reviewed. Check the provider's retention and data-processing terms.
7. Run a small real-backend cycle with a clearly identified target skill, bounded session/task limits, and a budget.
8. Inspect report, diagnostics, staged diff, baseline, candidate, task-level gate results, and all skipped/failed tasks.
9. Adopt only a specifically reviewed skill or memory proposal after approval and backup verification.

## Claude backend isolation

The current Sleep documentation describes a Claude replay guard that uses `--bare` when `ANTHROPIC_API_KEY` is set; without that API key it uses `--safe-mode` only if the installed Claude CLI advertises the option, otherwise replay is refused. Safe mode excludes user-level Claude instructions/skills/plugins/hooks/MCP customizations while preserving normal authentication/model selection, and admin policy still applies. This is not an OS sandbox. Review the selected isolation mode in the run diagnostics and do not assume your normal project instructions are loaded during replay. Recheck this behavior against the pinned SkillOpt and Claude Code versions.

## Multi-skill fan-out

Use multi-skill fan-out only after single-skill evaluation works reliably. It can create independent proposals/gates for explicitly hinted skills, but adds work and increases provider calls/token use. Missing, ambiguous, unreadable, unsafe, or colliding skills must be skipped with a reason. Review and adopt an explicit subset; an aggregate report must never authorize all skills by implication.

## Scheduling

Do not schedule a nightly run during initial adoption. First complete several manual cycles, assess data quality and cost, then propose a schedule with an owner, time zone, source, target, backend, budget, retention, failure notification, and disable/unschedule procedure. Confirm the scheduler persists all required flags; the SkillOpt docs note that some source/backend/model/path options may need to be placed in its config file instead of being assumed to persist in the scheduled entry.

## No auto-adoption by default

Keep `--auto-adopt` off. A held-out gain is evidence for the current task set/model/configuration; it is not a promise of general improvement. Human review remains required by PEOF for all shared, product-critical, or high-impact skills.

## Sources

- [SkillOpt-Sleep overview](https://github.com/microsoft/SkillOpt/blob/main/docs/sleep/README.md)
- [Claude Code SkillOpt-Sleep integration](https://github.com/microsoft/SkillOpt/tree/main/plugins/claude-code)
- [CLI reference](https://github.com/microsoft/SkillOpt/blob/main/docs/reference/cli.md)
