# SkillOpt Compatibility, Upgrades, and Change Control

## Purpose

Keep PEOF's integration compatible with the evolving Microsoft SkillOpt repository and prevent accidental use of features absent from the installed package.

## Source of truth

Use this order when documentation conflicts:

1. Actual checked-out SkillOpt source and tests for the pinned commit.
2. The exact CLI's `--help` output and selected configuration schema.
3. Version-matched documentation in that checkout.
4. Current official Microsoft documentation pages.
5. PEOF notes, which are guidance and may become stale.

Do not assume a repository `main` page describes the PyPI wheel or the version installed in the project.

## Package vs. source checkout

The reviewed Microsoft installation page stated that PyPI 0.2.0 did not yet include several newer `main` capabilities, including some Sleep backends/integrations, handoff, preferences, multi-skill fan-out, and reviewed subset adoption. This list is time-sensitive. Recheck the installation page and release notes before deciding whether a package install is sufficient.

Because PEOF v1.4's recommended integration uses repository plugin files and project-specific benchmark adapters, use a pinned source checkout or a controlled fork unless a later published package explicitly contains all required files and features.

## Upgrade procedure

1. Read upstream CHANGELOG and installation/CLI docs.
2. Review new features, deprecated flags, changed defaults, safety boundaries, and migration notes.
3. Fetch upstream changes without overwriting local patches.
4. Compare current pinned commit to candidate commit.
5. Inspect dependency/security changes and license notices.
6. Run source tests and the PEOF adapter contract tests.
7. Run Sleep `status`/mock dry-run and relevant backend capability probes.
8. Run the integration benchmark with the same smoke manifest.
9. Verify staged artifact schema and adoption/rollback still work.
10. Update integration profile, compatibility matrix, and PEOF changelog.
11. Approve and pin the new commit; retain previous checkout/commit for rollback.

## Breaking-change triggers

Treat as a breaking or high-risk change if it alters CLI flags, config keys/defaults, session source format, target-skill resolution, staging layout, report schema, scoring, backend isolation, plugin paths, tool permissions, supported OS/shells, multi-skill adoption, or validation-gate semantics.

## Local patches

Keep custom PEOF benchmark adapters in a maintained branch/fork or separable extension where practical. Record the upstream base commit and patch list. Do not make untracked edits in a shared clone. Rebase or port patches only after tests pass.

## Compatibility matrix

Maintain a project table with:

- PEOF version;
- SkillOpt remote, tag/commit, package version;
- research-engine CLI and Sleep CLI versions;
- Python and OS/shell;
- agent plugin/version;
- backend and source;
- custom adapter revision;
- verified capabilities and known restrictions;
- last verification date and owner.

## Rollback

If an upgrade breaks a workflow, stop new runs, restore the previous pinned checkout/environment, restore compatible config and adapter versions, and validate the last known-good integration. Do not roll forward by changing several unrelated components at once.
