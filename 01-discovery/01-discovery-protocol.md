# Discovery Protocol: Ask, Inspect, Assess, Recommend, Approve

## Non-negotiable rule

Do not configure or migrate the framework until the product context is understood. Do not edit, overwrite, rename, delete, reorganize, or deploy project assets without explicit authorization from the appropriate owner.

## Step 1 — Route the engagement

Determine whether the engagement is primarily:

- Greenfield product creation.
- Adoption into an existing product.
- Engineering/process modernization.
- Migration from another framework.
- Multi-product standardization.

Allow mixed cases. If unclear, ask the user rather than guessing.

## Step 2 — Ask questions in progressive rounds

Use the smallest question batch that unlocks the next decision. For a Claude Code project bootstrap, follow `08-claude-code/09-project-bootstrap-workflow.md` and its two-round interview: no more than four core questions, then one multi-select question for optional capabilities. For broader product discovery, adapt the same progressive approach rather than forcing the Claude-specific questionnaire onto every engagement.

Core product questions may cover:

- Product/engagement route, problem domain, target users, and product stage.
- Desired business/user outcome and the principal reason for adopting PEOF.
- Team, delivery model, and technical context.
- Available source materials, repository access, constraints, risks, and non-negotiable boundaries.

For existing repositories, inspect what can be verified first and ask the user to confirm only material findings or unknowns. For new projects, ask for the missing product, technology, and operating decisions; do not infer them from a blank folder.

Ask only what is needed now. Do not dump the full question bank, re-ask answered questions, or force free-text details such as exact commands and path lists into multiple-choice options.

## Step 3 — Inspect available evidence

With permission and access, inspect relevant source materials such as repository structure, current instructions, requirements, architecture, tests, build/deployment configuration, and process documents. Start read-only. Do not assume a file exists because a template names it.

When Claude Code setup is in scope, also follow `08-claude-code/05-environment-discovery-and-inventory.md`: inventory developer OS/shell/tooling, global and project-level Claude configuration, AGENTS.md and other AI-tool instructions, monorepo conventions, CI, safe project commands, and protected paths. Never dump secrets or raw credential stores. Distinguish global developer environment from product-specific profile.

For each finding, label its source:

- **Verified:** directly observed in a file, system, or reliable evidence.
- **User-stated:** supplied by the user but not independently verified.
- **Inferred:** a reasoned interpretation; state confidence.
- **Unknown:** evidence is unavailable or insufficient.

Do not turn an inference into a fact.

## Step 4 — Assess context and maturity

Use `03-assessment-and-maturity.md`. Identify strengths to preserve, high-risk gaps, duplicated or conflicting practices, and near-term opportunities.

## Step 5 — Recommend target configuration

Present:

- Engagement type and rationale.
- Product summary and current state.
- Maturity and risk assessment.
- Existing practices/assets to retain.
- Gaps and target practices.
- Tailored lifecycle and decision rights.
- Required artifact set.
- Claude Code integration scope, if requested.
- Adoption/migration phases, dependencies, effort bands, risks, and rollback approach.
- Open questions and assumptions.

## Step 6 — Obtain approval

Ask for explicit approval of the proposed target state and the exact scope of changes. Approval to assess is not approval to modify. Approval to create a separate framework folder is not approval to change application code or existing project documentation.

## Step 7 — Implement incrementally

Create or update only approved files. Prefer a separate framework directory and a separate product profile. Make changes in reviewable batches. Keep a manifest of created, updated, retained, superseded, and archived items.

## Step 8 — Validate and hand over

Check links, structure, consistency, traceability, and the applicable technical workflows. For Claude Code setup, use `08-claude-code/08-setup-validation-and-handoff.md` and the validation report template. Summarize what changed, what did not change, validation evidence, outstanding decisions, and how to use the framework.

## Stop conditions

Pause and ask for direction if access is insufficient, permissions are unclear, material requirements conflict, sensitive data may be exposed, a destructive change is proposed, or a decision exceeds the authority granted.
