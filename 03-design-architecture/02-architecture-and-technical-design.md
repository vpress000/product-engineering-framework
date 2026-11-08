# Architecture and Technical Design

## Purpose

Make technical choices that satisfy product requirements while controlling complexity, risk, cost, and operational burden.

## Architecture workflow

1. Understand functional scope, NFRs, constraints, and lifecycle needs.
2. Identify system boundaries, actors, data flows, and trust boundaries.
3. Compare viable architecture options and trade-offs.
4. Design components, interfaces, data ownership, and integration contracts.
5. Assess scalability, performance, availability, resilience, security, privacy, maintainability, and cost.
6. Record material decisions in ADRs.
7. Validate risky assumptions with prototypes or spikes.
8. Keep architecture documentation aligned with actual implementation.

## Architecture principles

- Prefer the simplest design that meets known needs with reasonable headroom.
- Separate responsibilities and establish clear boundaries.
- Minimize coupling and make interfaces explicit.
- Make data ownership and consistency behavior clear.
- Design for failure at integration and service boundaries.
- Avoid premature distribution and speculative abstraction.
- Prefer reversible decisions when uncertainty is high.
- Consider migration and backward compatibility for existing products.

## Technical design documents

A TDD should explain context, scope, proposed design, alternatives, interfaces, data model, failure behavior, security/privacy implications, observability, rollout, testing, and open questions. Scale the detail to the change.

## Architecture Decision Records

Create an ADR for consequential decisions that are difficult or costly to reverse, affect multiple components/teams, or constrain future direction. Record status, context, decision, alternatives, consequences, owner, and date. Supersede rather than silently rewrite an accepted decision.

## Architecture review

Review changes that materially affect boundaries, data ownership, shared contracts, security, reliability, cost, or migration strategy. Keep routine low-risk implementation choices with the responsible engineers.
