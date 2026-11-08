# Microsoft SkillOpt: Reference and Implementation Notes

## Purpose and status

This file preserves the v1.3 research notes and points to the first-class integration added in PEOF v1.4. Microsoft SkillOpt is now PEOF's recommended external implementation for automated skill optimization when the use case justifies it. It remains a separate repository and runtime; PEOF does not vendor its source code.

**Documentation checked:** 2026-11-07, against Microsoft's public repository and documentation. Recheck before installing or running because repository `main`, package releases, CLI options, and backend behavior can change.

## What SkillOpt provides

1. **Research engine:** text-space optimization of natural-language skill documents through target rollouts, trajectory/reflection, bounded edits, selection, and validation-gated updates; supports explicit benchmark/task environments.
2. **SkillOpt-Sleep (preview):** a separate usage-driven companion that can harvest supported coding-agent sessions, mine recurring task records, replay through a selected backend, consolidate bounded skill/memory edits, stage reports/proposals, and require explicit adoption by default.

The workflows are complementary but distinct. Microsoft's docs state Sleep has no runtime dependency on the paper/research `skillopt/` package. Do not assume shared configuration or identical guarantees.

## PEOF decision

Use SkillOpt as an external tool checkout beside the product, pinned to an exact commit/release and recorded in the PEOF SkillOpt Integration Profile. Prefer the source checkout when PEOF needs repo plugins, benchmark configs, materializers, adapters, or features documented on `main` but not yet in the published wheel. Do not use a moving `main` without recording its resolved commit.

For repository-aware evaluation, use the research engine with a project-specific environment adapter and isolated task worktrees, or another backend whose actual repository access has been validated. SkillOpt-Sleep's `--project` is a scope setting for collection/targets/state/staging; it is not proof that the replay backend can read or execute the project's source. Backend isolation varies.

## Key cautions retained from v1.3

- SkillOpt-Sleep is a preview; interfaces and defaults can change.
- Published package and `main` feature sets can differ.
- Real backends may send transcript-derived prompts/tasks to providers; outbound content is not guaranteed secret-free.
- Evidence logs can contain prompt/reply text and should be treated as sensitive.
- Mock is a plumbing check, not model-quality evidence.
- Token budgets may not be hard spend caps; verify backend accounting and provider-side controls.
- Multi-skill fan-out increases work/cost and requires individual review/adoption.
- A validation gain is run-specific evidence, not a guarantee of generalization.

## Detailed integration

See [`../12-skillopt-integration/01-integration-architecture.md`](../12-skillopt-integration/01-integration-architecture.md) and the remaining `12-skillopt-integration/` guides for source installation, research engine, Sleep, project benchmark adapters, backend isolation, privacy, adoption, operations, and upgrades.

## Official references

- [Microsoft SkillOpt documentation](https://microsoft.github.io/SkillOpt/docs/)
- [GitHub repository](https://github.com/microsoft/SkillOpt)
- [Installation](https://github.com/microsoft/SkillOpt/blob/main/docs/guide/installation.md)
- [Research benchmark guide](https://github.com/microsoft/SkillOpt/blob/main/docs/guide/new-benchmark.md)
- [SkillOpt-Sleep overview](https://github.com/microsoft/SkillOpt/blob/main/docs/sleep/README.md)
- [SkillOpt CLI reference](https://github.com/microsoft/SkillOpt/blob/main/docs/reference/cli.md)
- [Claude Code plugin](https://github.com/microsoft/SkillOpt/tree/main/plugins/claude-code)
