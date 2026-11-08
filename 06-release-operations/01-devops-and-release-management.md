# DevOps and Release Management

## Delivery pipeline

Design the delivery pipeline to build, validate, package, and deploy software consistently. Use version-controlled configuration and repeatable environments. Protect secrets and production access.

## Pipeline stages

A typical pipeline may include dependency resolution, formatting/linting, static analysis, unit tests, build, security/dependency scans, integration/contract tests, artifact creation, deployment to a test environment, acceptance checks, and controlled production deployment.

Select checks based on stack and risk. Keep pipelines deterministic, observable, and maintainable.

## Environment strategy

Define development, test, staging, and production environments as needed. Document configuration differences, data protection, access permissions, and environment ownership. Avoid relying on undocumented manual configuration.

## Release strategy

Choose a rollout approach suitable for risk: standard deployment, phased rollout, canary, blue/green, feature flags, or another method. Feature flags need owners, expiry/review dates, and cleanup plans.

## Release readiness

Confirm scope, version, build artifact, test evidence, unresolved defects, approvals, data migrations, backward compatibility, monitoring, support communication, deployment window, rollback/forward-fix strategy, and release notes.

## Data and schema migrations

Plan ordering, compatibility between old and new application versions, backups, validation, duration, failure behavior, and recovery. Prefer expand-and-contract approaches where appropriate. Never assume a database rollback is safe without testing it.

## Post-deployment validation

Verify health, critical journeys, error rates, performance, integrations, and business signals. Define observation windows and who can halt or roll back the release.
