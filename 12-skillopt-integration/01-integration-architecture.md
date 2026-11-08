# SkillOpt Integration Architecture

## Purpose

Define how PEOF uses Microsoft's SkillOpt repository as its primary external optimization implementation for agent skills. PEOF remains the product-engineering governance framework; SkillOpt supplies execution engines for selected skill-optimization workflows. The integration must be project-aware where repository-level performance is being evaluated, version-pinned, auditable, and safe to adopt.

## Architectural decision

Use the Microsoft SkillOpt source repository as a separately managed tool checkout. Do not copy the entire SkillOpt repository into each product repository, and do not place optimizer state, credentials, transcripts, caches, or generated experiments in the product's source tree unless a specific project policy approves a project-local artifact.

Recommended workspace:

```text
workspace/
├── product-engineering-framework/       # PEOF standards and templates
├── tools/
│   └── SkillOpt/                        # separate Microsoft source checkout / owned fork
└── products/
    └── product-a/
        ├── src/
        ├── tests/
        ├── docs/
        ├── .claude/skills/               # live project skills
        └── .skillopt-sleep/              # project-specific staging/state only if approved
```

The paths are illustrative. A team may use another layout, but it must keep PEOF, the SkillOpt tool checkout, product source, and sensitive state logically distinct.

## Two SkillOpt workflows; do not conflate them

| Workflow | Primary purpose | PEOF use |
|---|---|---|
| SkillOpt research engine (`skillopt`, `skillopt-train`, `skillopt-eval`) | Reproducible optimization of a skill against an explicit benchmark/task environment | Use for controlled training and repeatable baseline/candidate evaluation. Add a project-specific benchmark adapter when actual repository tasks must be executed and scored. |
| SkillOpt-Sleep (`skillopt_sleep`, `skillopt-sleep`) | Deployment-time, usage-driven cycle: harvest supported agent sessions, mine recurring tasks, replay, reflect, stage candidate memory/skill updates behind a held-out gate | Use as an optional learning loop for real development-session experience. It is documented by Microsoft as a preview; retain manual review and adoption. |

They have separate entry points, configuration, and safety boundaries. Microsoft's current documentation says the Sleep package has no runtime dependency on the research `skillopt/` package (its validation gate is vendored). Installing one workflow must not be assumed to configure the other.

## Responsibilities

**PEOF owns:** asset inventory, product context, task selection, evaluation intent, split/exposure governance, risk classification, access policy, approvals, versioning, publication policy, rollback, and the decision whether optimization is warranted.

**SkillOpt owns:** its documented optimization/replay mechanics, model backend handling, skill-edit proposals, supported session harvesting, validation-gate implementation, staging artifacts, and CLI/plugin behavior.

**The project adapter owns:** safe access to the specific product snapshot, benchmark task setup, isolated workspaces, approved commands, test execution, scoring, artifact capture, and cleanup.

Do not claim that SkillOpt automatically understands a product's source code merely because `--project` points to its directory. The meaning of project scope and repository access depends on the selected workflow, backend, adapter, and current implementation. See `06-backend-selection-and-isolation.md` and `05-project-aware-benchmark-adapter.md`.

## Integration modes

1. **Documentation-only:** PEOF defines and reviews skills; no SkillOpt installation.
2. **Sleep pilot:** SkillOpt-Sleep reviews approved local session sources and stages proposals. Start with `mock`/dry-run, then reviewed task replay with a real backend only after privacy approval.
3. **Research benchmark:** the research engine optimizes a skill over an explicit benchmark and split manifest.
4. **Project-aware benchmark:** a custom adapter uses a pinned project snapshot and isolated task worktree to exercise real repository tasks and independent checks.
5. **Combined:** use Sleep to find recurring pain points and research/project benchmarks to validate proposed changes. The two result streams remain distinguishable in the evidence record.

## Non-goals

- No model-weight fine-tuning is implied; SkillOpt optimizes skill text.
- No automatic adoption into the live project by default.
- No automatic modification of the product repository during discovery or dry-run.
- No guarantee of general improvement from a single validation result.
- No assumption that every Sleep backend has repository, shell, browser, or MCP access.

## Required integration record

Use [`../09-templates/29-skillopt-integration-profile-template.md`](../09-templates/29-skillopt-integration-profile-template.md). Record SkillOpt remote, exact commit/tag, install method, Python and CLI versions, selected workflow, backend/source, target skill paths, project adapter version, model/provider IDs, task manifest hash, data boundary, budget, and approval.

## Sources

- [SkillOpt overview](https://microsoft.github.io/SkillOpt/docs/)
- [SkillOpt installation](https://github.com/microsoft/SkillOpt/blob/main/docs/guide/installation.md)
- [SkillOpt-Sleep overview](https://github.com/microsoft/SkillOpt/blob/main/docs/sleep/README.md)
