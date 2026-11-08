# Product Engineering Lifecycle and Quality Gates

The lifecycle is a feedback system, not a rigid one-way waterfall. Teams may revisit discovery, requirements, design, or architecture when new evidence appears.

## Lifecycle overview

1. **Opportunity and strategy:** define the problem space, target outcomes, strategic fit, and constraints.
2. **Discovery:** validate users, needs, feasibility, desirability, viability, and major risks.
3. **Requirements and scope:** define behavior, quality attributes, boundaries, acceptance conditions, and priorities.
4. **Experience and technical design:** design user journeys, interfaces, data, integrations, architecture, and operational approach.
5. **Planning:** decompose and group work, identify dependencies, estimate uncertainty, and sequence delivery.
6. **Implementation:** build in version-controlled, reviewable increments with continuous validation.
7. **Verification and acceptance:** execute appropriate automated and human tests; resolve or explicitly accept remaining risks.
8. **Release:** prepare operational readiness, deploy safely, validate production behavior, and communicate change.
9. **Operate and learn:** monitor outcomes and reliability, support users, manage incidents, and feed learning into the roadmap.

## Gates

| Gate | Decision | Minimum evidence |
|---|---|---|
| G0: Opportunity | Is this worth exploring? | Problem/opportunity, target users, strategic rationale, initial uncertainty |
| G1: Discovery | Is there enough evidence to define a solution? | Research or evidence summary, key assumptions, feasibility and risk view |
| G2: Scope and readiness | Is the work sufficiently understood to plan? | Requirements or stories, acceptance criteria, priority, dependencies, non-functional needs |
| G3: Design readiness | Is the proposed solution coherent and safe to build? | Relevant UX/technical design, key decisions, security/privacy considerations |
| G4: Implementation completion | Is the increment built to agreed standards? | Reviewed code, passing required checks, updated documentation, traceability |
| G5: Release readiness | Is release risk acceptable? | Test evidence, operational readiness, rollback/mitigation, approvals, known issues |
| G6: Outcome review | Did the release achieve its intended result? | Usage/outcome data, feedback, reliability review, follow-up decisions |

## Gate tailoring

A low-risk copy change may pass through a lightweight checklist. A change to payments, authentication, sensitive data, safety-critical behavior, or core architecture needs stronger evidence and review. Document the selected controls in the product profile.

## Gate outcomes

Every gate ends with one of: **Proceed**, **Proceed with conditions**, **Rework**, or **Stop/defer**. Record the decision owner, rationale, outstanding actions, and expiry/review date for accepted risks.

## Continuous flow

Do not make gates into long queues. Define expected evidence in advance, automate repeatable checks, and let reviewers work concurrently where practical. Escalate unresolved blockers quickly.
