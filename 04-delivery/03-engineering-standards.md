# Engineering Standards

## General standards

Adopt standards that fit the selected languages, frameworks, and repository conventions. Prefer established ecosystem tooling over bespoke rules when it is reliable.

## Code structure and maintainability

- Use clear names and cohesive modules.
- Separate domain logic, infrastructure, and presentation where appropriate.
- Avoid unnecessary duplication and speculative abstraction.
- Make side effects and dependencies visible.
- Keep functions and modules understandable.
- Handle errors intentionally; do not swallow failures silently.
- Avoid hard-coded secrets, environment-specific values, and personal data.

## Interfaces and data

- Define API contracts, validation, authorization, error responses, and versioning expectations.
- Define data ownership, constraints, migrations, and retention.
- Maintain compatibility deliberately where clients or services depend on contracts.
- Treat schema changes as deployable changes with rollback or forward-recovery planning.

## Reliability and observability

Use structured, useful logs; relevant metrics; tracing where justified; health checks; and actionable alerts. Do not log secrets or sensitive user data. Make failures diagnosable without excessive noise.

## Dependencies and configuration

Pin or constrain dependencies appropriately, review changes, remove unused packages, and monitor vulnerabilities. Separate configuration from code. Store secrets in approved secret-management systems.

## Documentation

Document how to build, run, test, configure, deploy, and troubleshoot the system. Update documentation when behavior or operational ownership changes. Prefer concise, discoverable docs close to the relevant code.

## Automated checks

Use formatting, linting, static analysis, type checks, tests, and security/dependency scans where supported and useful. Keep checks deterministic and maintain them as production code.

## Exceptions

Record material deviations, rationale, risk, owner, and review date. Do not allow temporary exceptions to become invisible permanent standards.
