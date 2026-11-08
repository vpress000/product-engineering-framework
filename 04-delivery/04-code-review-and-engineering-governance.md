# Code Review and Engineering Governance

## Code review goals

Review for correctness, security, maintainability, test quality, compatibility, performance implications, and consistency with product requirements and architecture.

## Pull request expectations

A pull request should explain the problem, scope, approach, relevant group/issue, key decisions, test evidence, screenshots or recordings where useful, migration/configuration impacts, and known risks. Keep changes focused and reviewable.

## Review behavior

- Review the change, not the author's worth.
- Prioritize correctness and risk over style preferences handled by automation.
- Ask questions where context is unclear.
- Distinguish blocking findings from suggestions.
- Resolve or explicitly record significant concerns.
- Ensure required checks have passed before merge.

## Governance controls

Use lightweight controls for routine changes and stronger review for changes involving security, sensitive data, payments, core architecture, public APIs, data migrations, availability, or regulatory scope.

## Technical debt

Record debt with its impact, cause, risk, affected areas, proposed treatment, and owner. Prioritize debt by user/business impact, failure likelihood, change friction, and future cost—not by code age alone.

## Engineering decisions

Record consequential decisions in ADRs or an equivalent system. Identify the decision owner, alternatives, consequences, and whether/when the decision should be revisited.
