# Skill Versioning, Adoption, and Rollback

## Purpose

Make changes to shared agentic assets traceable, reviewable, recoverable, and resistant to stale or ambiguous proposals from manual work, SkillOpt research runs, or SkillOpt-Sleep.

## Versioning model

Use semantic versioning as a convention for material shared assets: major for scope/permissions/output compatibility changes; minor for backward-compatible capability additions; patch for clarifications and low-risk wording changes. Record a cryptographic content hash as well; a version string alone does not prove file identity.

## Provenance record

Record asset ID/type/path/platform; baseline and candidate versions/hashes; SkillOpt remote/commit/package version; workflow (research/Sleep); plugin/CLI version; benchmark/adapter revision; model/provider/backend; run ID; task manifest/split/exposure; report and diagnostics; gate results; costs; approver/date; adoption receipt; backup and rollback.

## Staging and adoption

- Keep candidate output separate from live skills.
- Verify baseline and candidate hashes.
- Re-check live file hash immediately before adoption.
- Adopt only explicitly selected paths/skills.
- Treat each skill from multi-skill fan-out independently.
- Back up before replacement and write an adoption receipt.
- Verify published content and run post-adoption smoke checks.

SkillOpt-Sleep stages proposals and offers explicit adoption commands; do not confuse staging or an accepted gate with publication. Do not enable `--auto-adopt` by default.

## Concurrency and transaction safety

Use locks, per-target coordination, write-ahead recovery, and atomic replacement where supported. Validate all targets before a multi-file change. Fail closed on stale baseline, path ambiguity, unexpected edits, or mismatched hashes. A Git worktree protects version-control state but does not substitute for OS/container security isolation.

## Rollback

Stop promotion, identify active hash and known-good backup, confirm no later legitimate edit would be overwritten, record approval/reason, restore exact backup, verify hash, run smoke/evaluation checks, and write a rollback receipt. Never blindly overwrite a changed file.

## Release channels and retention

Use draft/candidate/stable/deprecated channels where useful. Retain approved asset versions and necessary evidence; do not retain raw sessions or sensitive task examples without an explicit retention reason and policy.

## SkillOpt transaction records

Use [`../09-templates/33-skillopt-improvement-proposal-template.md`](../09-templates/33-skillopt-improvement-proposal-template.md) and [`../09-templates/34-skillopt-run-and-adoption-receipt-template.md`](../09-templates/34-skillopt-run-and-adoption-receipt-template.md). For Sleep-specific approvals, use template 31.
