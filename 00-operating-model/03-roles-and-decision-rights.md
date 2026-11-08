# Roles and Decision Rights

Roles describe accountabilities, not mandatory headcount. One person may hold several roles in a small team. For material decisions, name one accountable decision owner.

| Role | Primary accountability |
|---|---|
| Product sponsor | Business intent, funding/context, strategic trade-offs |
| Product manager/owner | User and business outcomes, product scope, prioritization, acceptance |
| Product designer/researcher | User research, journey, interaction, usability, design system |
| Engineering lead/architect | Technical direction, architecture integrity, engineering standards, technical risk |
| Engineers | Implementation, automated tests, maintainability, operational ownership |
| QA/quality engineer | Risk-based test strategy, testability, quality evidence, defect insights |
| Security/privacy lead | Threat, privacy, regulatory, and control guidance; risk review |
| Platform/operations | Build/deploy platform, runtime reliability, monitoring, recovery |
| Delivery facilitator | Flow, dependencies, coordination, impediment removal |

## Decision ownership

| Decision | Accountable owner | Required consultation |
|---|---|---|
| Product vision, outcomes, roadmap | Product sponsor/owner | Users, design, engineering, business stakeholders |
| Feature priority and scope | Product owner | Engineering, design, QA, affected stakeholders |
| UX patterns and experience | Design lead (or named product owner) | Users, product, engineering, accessibility expertise |
| Architecture and technology | Engineering lead/architect | Implementers, security, operations, product |
| Security/privacy risk acceptance | Authorized risk owner | Security/privacy specialist, product, engineering |
| Test strategy and quality evidence | Quality lead or engineering lead | Product, engineering, operations |
| Release go/no-go | Named release owner | Product, engineering, QA, operations, risk owners |
| Production incident command | Incident commander | Service owner, operations, security, communications |

## RACI-lite practice

For each major workflow or high-impact deliverable, identify: one **Accountable** owner, the people **Responsible** for work, those **Consulted**, and those **Informed**. Avoid ambiguous shared accountability.

## Small-team adaptation

For a solo builder, the same person may act as product owner, engineer, and QA. Preserve the decision checkpoints by using written checklists and, for high-risk changes, an independent reviewer or external specialist where feasible. Never imply that a role exists when it does not.
