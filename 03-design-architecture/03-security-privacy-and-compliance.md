# Security, Privacy, and Compliance by Design

## Scope

Tailor controls to the data, users, threat model, jurisdictions, contractual obligations, and product impact. Obtain specialist advice where required; this document is not legal advice or a substitute for a formal security program.

## Early discovery

Identify:

- Data categories, sensitivity, purpose, retention, and sharing.
- Users, roles, privileges, and administrative functions.
- Trust boundaries, external integrations, and entry points.
- Threat actors, abuse cases, and high-impact failure scenarios.
- Applicable laws, regulations, standards, and contracts.
- Security and privacy decision owners.

## Engineering controls

Consider secure authentication and authorization, least privilege, secure session handling, input validation, output encoding, secrets management, encryption in transit and at rest, dependency and vulnerability management, audit logging, secure defaults, backup protection, and secure build/release practices.

## Privacy controls

Use data minimization, purpose limitation, transparent notices, retention limits, access controls, deletion/export workflows where applicable, and documented data processors. Avoid placing personal or sensitive data in prompts, logs, test fixtures, or public repositories unless explicitly approved and properly protected.

## Threat modeling

For material features or architecture changes, map assets, actors, entry points, trust boundaries, threats, controls, residual risks, and owners. Revisit after meaningful changes.

## Risk treatment

Record each significant risk, impact, mitigation, residual risk, and authorized acceptance. Engineering teams must not silently accept risks that require product, security, privacy, legal, or executive authority.

## Release considerations

Confirm security-relevant tests, access configuration, secret handling, dependency status, data migration safety, auditability, and incident response readiness before release, as applicable.
