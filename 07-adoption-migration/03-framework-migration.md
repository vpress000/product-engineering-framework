# Framework and Process Migration Playbook

## Objective

Move from existing standards, templates, tools, or workflows to PEOF without losing important knowledge or interrupting delivery unnecessarily.

## 1. Define migration scope

Clarify whether migration covers documentation, process, roles, tool configuration, code standards, CI/CD, architecture, or a combination. Define what is explicitly excluded.

## 2. Inventory and map

Create an inventory of existing artifacts and practices. Map each to its PEOF equivalent or classify it as unique. Identify owners, authority, usage, freshness, and dependencies.

## 3. Classify each item

Use the following outcomes:

- **Retain:** current and useful; keep as-is.
- **Improve:** useful but incomplete or outdated.
- **Consolidate:** overlapping sources should become one controlled source of truth.
- **Replace:** a target standard is approved and migration is justified.
- **Archive:** no longer active but retained for historical/reference reasons.
- **Create:** a required capability or artifact is missing.
- **Defer:** low-value or high-risk migration is postponed with an owner/review date.

## 4. Reconcile conflicts

Do not choose the newest-looking document automatically. Identify the authoritative owner, compare actual practice, resolve contradictions, record decisions, and preserve history. Never silently overwrite a meaningful decision.

## 5. Plan migration waves

Each wave should have scope, sequence, owner, dependencies, impact, validation criteria, communication, rollback/containment plan, and exit conditions. Prioritize risk reduction and high-value improvements over cosmetic cleanup.

## 6. Pilot and learn

Test migration on a bounded scope. Gather feedback from people who use the process. Measure friction and adjust before wider rollout.

## 7. Cutover and retire

Communicate the effective date, new source of truth, training, support route, and old-process retirement plan. Keep read-only archives where needed. Avoid running conflicting systems indefinitely.

## 8. Validate

Confirm migrated content is accurate, links work, responsibilities are clear, workflows are usable, and no required control was lost.

## Migration controls

Maintain a migration register with source item, target item, classification, owner, status, validation evidence, and decision history. Do not migrate secrets, production credentials, or unnecessary personal data into documentation or AI context.
