# Framework Tailoring Guide

## Purpose

Configure the minimum effective operating model for each product. The framework is a menu of connected practices, not a mandate to create every document or hold every ceremony.

## Tailoring dimensions

Assess:

- Product and domain complexity.
- User impact and business criticality.
- Data sensitivity and security exposure.
- Regulatory or contractual obligations.
- Architecture and integration complexity.
- Team size, capability, and distribution.
- Release frequency and deployment risk.
- Product maturity and current process reliability.
- Availability, performance, and recovery needs.

## Practice classification

Mark each practice:

- **Required:** necessary for material risk, legal obligation, or essential traceability.
- **Recommended:** useful default; may be tailored with rationale.
- **Optional:** use when it adds value.
- **Not applicable:** deliberately excluded, with rationale when the omission could be misunderstood.

## Tailoring procedure

1. Establish the product profile and risk context.
2. Select lifecycle gates proportionate to risk.
3. Choose the minimum artifact set needed to make decisions and maintain traceability.
4. Define decision owners and review expectations.
5. Define testing layers and release controls.
6. Identify tools and automation that already exist.
7. Document deliberate exclusions, exceptions, and assumptions.
8. Review tailoring after major changes, incidents, or maturity shifts.

## Minimum viable operating model

For a low-risk early product, a practical minimum may be: product brief, prioritized backlog, concise acceptance criteria, lightweight architecture notes, code review or self-review checklist, automated tests appropriate to the stack, release checklist, and basic monitoring/backup plan.

Add more formal SRS, threat modeling, traceability, independent testing, formal approvals, disaster recovery, or compliance evidence when product risk demands it.

## Anti-patterns

- Creating documents solely to satisfy a template.
- Applying heavyweight governance to trivial changes.
- Skipping security or operational review because the team is small.
- Treating estimates as commitments when uncertainty is high.
- Using process compliance as a substitute for user outcomes.
- Keeping exceptions permanently without review.
