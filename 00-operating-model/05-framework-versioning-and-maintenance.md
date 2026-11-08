# Framework Versioning and Maintenance

## Purpose

Keep the shared framework coherent, current, understandable, and safe to adopt across products. The framework itself is a maintained product: it needs ownership, versioning, change control, validation, and a deprecation policy.

## Ownership

Name a framework owner and, where needed, domain stewards for product, architecture, delivery, quality, security, operations, and AI-assisted engineering guidance. The framework owner maintains the index, release notes, review calendar, and cross-document consistency.

## Versioning

Use semantic-style versions:

- **MAJOR:** a change that breaks expected workflows, changes key definitions, or requires substantial re-adoption.
- **MINOR:** backward-compatible additions, new playbooks, templates, or optional practices.
- **PATCH:** corrections, clarifications, link repairs, and non-breaking improvements.

Every release records the version, date, summary, affected documents, migration/adoption notes, and approving owner. Product-specific tailoring has its own version history and must not silently change the shared baseline.

## Change workflow

1. Record the problem, proposed change, evidence, and affected users of the framework.
2. Check for duplication, conflicts, and impacts on existing product profiles.
3. Draft the change and identify whether it is mandatory, recommended, optional, or a template-only update.
4. Review it with relevant domain owners.
5. Validate links, examples, terminology, templates, and Claude Code syntax where relevant.
6. Approve, version, publish, and communicate the change.
7. Provide transition guidance when teams need to update existing practices.

## Review cadence

Review the framework at least annually and after material security, regulatory, technology, or operating-model changes. Review fast-changing integration guidance more frequently. Do not change a standard merely because a tool or trend is popular; explain the practical benefit and migration cost.

## Deprecation

Mark outdated content as deprecated, identify its replacement, state the effective date, and provide a transition period where needed. Do not silently remove approved decisions or historical records.

## Health measures

Review adoption friction, repeated exceptions, stale links/templates, conflicting guidance, and whether teams can complete real work using the framework. Remove process that adds cost without improving decisions, outcomes, or risk control.
