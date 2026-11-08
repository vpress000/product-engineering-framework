# Framework Change Management

## Change proposal

Every material framework change should identify the problem, evidence, affected products/roles, proposed wording or artifact, alternatives, adoption cost, risks, and whether the change is mandatory, recommended, optional, or informational.

## Review and approval

The framework owner coordinates review with affected domain stewards. Security, privacy, legal, regulatory, and production-risk guidance requires review by appropriately qualified owners. Record the approver, effective date, and rationale.

## Release process

1. Update the relevant files and `CHANGELOG.md`.
2. Update `PACKAGE-CONTENTS.md` and README navigation when the structure changes.
3. Run link, file inventory, terminology, and consistency checks.
4. Validate template completeness and examples.
5. Recheck external tool instructions against their official documentation.
6. Assign the appropriate version.
7. Publish and communicate the release.

## Breaking changes

For a breaking change, explain affected workflows, provide migration guidance, identify the transition window, and state when prior guidance becomes unsupported. Preserve prior versions or approved history when users depend on them.

## Feedback and exceptions

Collect user feedback and recurring exceptions. A recurring exception may indicate that the standard is unclear, too costly, or unsuitable. Review it as a potential framework improvement rather than normalizing untracked deviations.
