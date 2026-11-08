# Staging, Adoption, and Multi-Skill Governance with SkillOpt

## Purpose

Connect SkillOpt's staged candidate artifacts to PEOF's versioned asset release process without bypassing human approval or project safety controls.

## Expected stages

SkillOpt-Sleep's documented workflow writes reports and proposed skill/memory files to a staging area; a held-out gate determines whether a proposal is accepted for staging. Live files should remain unchanged until the user explicitly adopts. The research engine produces candidate/best skill artifacts and experiment outputs. Both must enter PEOF review before publication.

## Promotion workflow

1. Identify the exact candidate artifact and intended live target.
2. Verify its baseline skill version and content hash.
3. Verify the task manifest, split/exposure ledger, model/provider, backend, adapter, SkillOpt commit, and run identifier.
4. Review the full candidate diff and protected regions.
5. Inspect task-level results, hard/soft scores, validation/test gates, no-regression results, and uncertainty.
6. Inspect failed, skipped, timed-out, missing, or invalid tasks; do not silently exclude failures.
7. Confirm privacy review, cost, backend isolation, tool permissions, and compatibility.
8. Confirm the live skill has not changed since the baseline was captured.
9. Obtain explicit approval for the exact paths and content hashes.
10. Back up live files, adopt the approved subset, write an adoption receipt, and verify hashes.
11. Run the post-adoption smoke suite and monitor real usage.

## SkillOpt-Sleep staged output

The current docs describe staging under a project `.skillopt-sleep/staging/<timestamp>/` path, including report and structured evidence/diagnostics artifacts. Verify the actual layout in the pinned version. Do not assume every run produces a candidate: a rejected gate may create a report without a proposed live-file replacement.

## Multi-skill fan-out

Enable only after single-skill cycles have demonstrated value. The current Sleep documentation describes opt-in multi-skill fan-out, which runs independent consolidation/gating for hinted skills and increases calls/token use. The review process must:

- resolve each skill to a canonical path and exact live bytes;
- keep each skill's task hints and recalled tasks scoped appropriately;
- preserve an independent gate and report for each skill;
- skip missing, ambiguous, aliased, unreadable, unsafe, or colliding paths with reasons;
- never fall back to a generic managed skill when a named project skill cannot be resolved;
- adopt only the explicitly selected subset after reviewing every selected item.

An aggregate report or aggregate pass is not blanket approval for every proposed skill.

## Atomicity and rollback

For multi-file adoption, validate every destination before the first write. Use locks, backups, a recovery journal, atomic replacement where supported, and a receipt per target. If the filesystem cannot guarantee compare-and-swap or atomic multi-file writes, document the limitation and coordinate a maintenance window. Stop on a stale lock, baseline mismatch, path ambiguity, hash mismatch, or unexpected user edit.

## Keep generated artifacts out of live paths

Do not point SkillOpt's output directory directly at the production skill directory. Use separate candidate and staging paths. Promote by a reviewed copy/adoption process, not by editing the live file in place during optimization.

## Required records

Use templates 32 (improvement proposal), 33 (adoption/rollback), and 34 (run review). Keep all approval and hash records.
