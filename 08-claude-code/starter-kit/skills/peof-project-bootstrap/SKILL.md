---
name: peof-project-bootstrap
description: Discover and safely configure PEOF and Claude Code for a new or existing repository. Use for project onboarding, Claude Code setup, or controlled framework adoption; begin read-only and obtain approval before writing.
---

# PEOF Project Bootstrap

1. Route the engagement as greenfield, existing product, modernization, framework migration, mixed, or multi-product.
2. Follow `08-claude-code/09-project-bootstrap-workflow.md` and read only the supporting pages needed.
3. Inventory the developer environment and repository read-only. Do not inspect secret contents or execute commands with side effects.
4. Summarize findings in 10 lines or fewer using found, unknown, user-confirmed, or not applicable labels.
5. Conduct the core interview in at most four questions, then ask one multi-select question for optional capabilities. Ask follow-ups only for selected options.
6. Verify all Claude Code settings, file locations, permission syntax, hook fields, skill/agent frontmatter, and commands against current official documentation and the installed version.
7. Prepare a setup approval plan that separates project files, user-level changes, external integrations, manual steps, limitations, and rollback.
8. Stop and wait for explicit approval. No writes or installations before approval.
9. Implement only approved items with minimal diffs. Preserve existing configuration and do not change application code unless authorized.
10. Validate files, JSON, frontmatter, hooks, permissions, selected integrations, and safe project checks. Report pass/fail/not-run honestly.

## Required output

- Engagement route and repository/environment summary.
- Evidence inventory and unknowns.
- Protected paths and boundaries.
- Interview answers and optional capability selections.
- Proposed setup and approval plan.
- Implemented changes, if approved.
- Validation report and rollback instructions.

Never treat a successful Claude Code bootstrap as proof that the product is ready for implementation or release.
