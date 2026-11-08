# PEOF v1.4.0 Review and Validation Report

**Release:** 1.4.0  
**Review date:** 2026-11-07  
**Basis:** Existing PEOF v1.3.0 ZIP plus current public Microsoft SkillOpt repository and documentation reviewed on 2026-11-07.

## Executive summary

PEOF v1.4.0 upgrades the earlier SkillOpt reference-only treatment into a practical external integration. It uses the Microsoft SkillOpt repository as the supported optimization implementation while preserving PEOF's own product engineering, discovery, Claude Code bootstrap, privacy, approval, evaluation, and rollback governance.

The integration distinguishes the research engine from SkillOpt-Sleep. It establishes a source-checkout and commit-pinning approach, includes project-aware benchmark adapter requirements, documents backend-specific isolation boundaries, and provides operations, adoption, cost, privacy, and upgrade controls.

## Key findings applied

| Finding | v1.4.0 action |
|---|---|
| Research engine and Sleep are separate workflows | Separate integration docs and runbooks |
| Sleep is a preview | Explicit warning and compatibility checks |
| PyPI and repository `main` feature sets differ | Recommend pinned source checkout for repo/plugin/adapter features; verify current release each time |
| `--project` is not a guarantee of repository/tool access | Added explicit scope warning and backend matrix |
| Real Sleep backends can transmit transcript-derived prompts/tasks | Added data governance, reviewed-task, provider, and retention controls |
| Mock is not proof of model quality | Added first-run and evidence restrictions |
| Research codebase tasks require a task environment/adapter | Added project-aware benchmark adapter design |
| Multi-skill fan-out adds work and requires independent review | Added per-skill gates and explicit subset adoption |
| Backend/tool isolation varies | Added isolation levels and mandatory capability probe |
| Optimization candidate must not change live skill directly | Added staging, hash verification, approval, receipt, and rollback process |

## Files added

- 11 new documents under `12-skillopt-integration/`.
- 6 reusable templates under `09-templates/` (29–34).
- 1 Claude Code starter skill under `08-claude-code/starter-kit/skills/peof-skillopt-operations/`.

Total added: 18 Markdown files. Existing v1.3 files are preserved; selected root and agentic-engineering files are updated. The v1.3 review report is retained as `REVIEW-REPORT-V1.3.md`.

## Important architecture choices

1. SkillOpt is a separate source checkout, not copied into each product repository or embedded in the PEOF ZIP.
2. PEOF owns the policy and governance; SkillOpt owns its documented execution/optimization mechanics; a project adapter owns controlled access and scoring for product tasks.
3. Research-engine benchmarking is the primary path for controlled project-code evaluation. Sleep is a complementary preview workflow for usage-derived task learning; it must not be represented as repository-aware unless the selected backend proves that behavior.
4. Real sessions and project data require classification, review/redaction, provider approval, retention, and cost controls.
5. Auto-adoption is off by default. Each candidate requires explicit review, baseline/hash verification, backup, receipt, and post-adoption checks.

## Validation performed

- Extracted v1.3 archive and preserved its 99 Markdown files.
- Added 18 Markdown files and updated root/Agentic Engineering/Claude integration documents.
- Generated a complete package inventory from actual files.
- Checked internal relative Markdown links (including anchors where statically resolvable).
- Checked ZIP integrity and exact archive file list.
- Confirmed the new integration guides contain source-repo URLs and distinguish source-derived behavior from PEOF policy.

## Limitations — what was not tested

This is a documentation/package release. No SkillOpt repository was installed, no model/provider credentials were used, no SkillOpt train/eval/Sleep cycle was executed, no project benchmark adapter was implemented against a real product, no Claude Code plugin was installed, and no security isolation audit was performed. Therefore, this report does not claim live runtime compatibility or actual skill-performance improvement.

## Upgrade steps for a real project

1. Run PEOF discovery and approve a project-specific SkillOpt Integration Profile.
2. Clone SkillOpt separately, inspect current official docs and source, install in an isolated Python environment, and pin the resolved commit.
3. Start with mock/low-risk Sleep review or a small research benchmark; do not begin with nightly automation.
4. If repository tasks are required, implement and test the project benchmark adapter in a disposable worktree/container.
5. Review all data/provider/cost boundaries before a real backend.
6. Stage, evaluate, review, approve, adopt, and retain rollback evidence.

## Official source references

- [Microsoft SkillOpt repository](https://github.com/microsoft/SkillOpt)
- [Official documentation](https://microsoft.github.io/SkillOpt/docs/)
- [Installation guide](https://github.com/microsoft/SkillOpt/blob/main/docs/guide/installation.md)
- [Research benchmark guide](https://github.com/microsoft/SkillOpt/blob/main/docs/guide/new-benchmark.md)
- [SkillOpt-Sleep overview](https://github.com/microsoft/SkillOpt/blob/main/docs/sleep/README.md)
- [Multi-skill staging](https://github.com/microsoft/SkillOpt/blob/main/docs/sleep/multi-skill-staging.md)
- [CLI reference](https://github.com/microsoft/SkillOpt/blob/main/docs/reference/cli.md)
- [Claude Code plugin](https://github.com/microsoft/SkillOpt/tree/main/plugins/claude-code)
