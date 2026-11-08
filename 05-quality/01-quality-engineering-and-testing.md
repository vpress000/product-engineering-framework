# Quality Engineering and Testing Strategy

## Quality model

Quality includes functional correctness, usability, accessibility, performance, reliability, security, privacy, compatibility, maintainability, and operability. Tailor the dimensions to the product.

## Test layers

- **Unit:** isolated logic and domain rules.
- **Component:** component behavior and contracts.
- **Integration:** interactions among services, databases, APIs, and external dependencies.
- **Contract:** compatibility across service or client boundaries.
- **End-to-end:** critical user journeys through the integrated product.
- **Exploratory/manual:** usability, complex behavior, and scenarios poorly suited to automation.
- **Non-functional:** performance, security, accessibility, resilience, and compatibility as relevant.
- **Acceptance:** confirmation that requirements and user/business outcomes are met.

Do not pursue a fixed test pyramid ratio. Choose a mix that gives fast, reliable feedback at reasonable maintenance cost.

## Test planning

For each implementation group:

1. Map requirements and acceptance criteria to validation methods.
2. Identify high-risk paths, boundaries, permissions, and failure modes.
3. Define test data, environments, dependencies, and cleanup.
4. Automate stable, repeatable checks.
5. Plan exploratory testing for uncertainty and usability.
6. Define expected results and defect severity.
7. Preserve evidence and link it to the group/release.

## Shift-left and continuous validation

Run fast checks early and frequently. Execute tests at appropriate levels during implementation, not only after the entire group is built. Run collective group acceptance and regression checks before release.

## Defect management

A defect record should include observed behavior, expected behavior, reproduction steps, environment/build, impact, severity, evidence, suspected scope, and resolution/verification. Prioritize by user impact and risk.

## Test environment and data

Keep environments representative enough for the test purpose. Use synthetic or properly protected data. Control test credentials and access. Make tests repeatable and avoid dependence on unstable external services where practical.

## AI agent, skill, and prompt evaluation (when applicable)

If the product or engineering workflow uses reusable AI agents, skills, or prompts, treat them as testable engineering assets. Define representative tasks, observable acceptance criteria, static checks, safety/permission tests, and operational measures. Compare candidates with a pinned baseline on the same task set and equivalent configuration. Maintain separate development, validation, and held-out test tasks when optimization is performed; record task exposure and do not reuse exposed tasks as pristine holdouts. Use deterministic checks where possible and document the limitations of model-based judges.

A material asset must pass its predeclared quality and no-regression gates, and receive human approval before publication. Missing/invalid results, evaluator failures, or contaminated holdouts should yield an inconclusive or failed result, not a pass. See [`../11-agentic-engineering/03-skill-evaluation-and-benchmarking.md`](../11-agentic-engineering/03-skill-evaluation-and-benchmarking.md).

## Quality reporting

Report meaningful evidence: pass/fail by risk area, escaped defects, flaky tests, coverage of critical requirements, unresolved high-severity issues, release risk, and (where applicable) agent/skill evaluation results. Code coverage or agent success rate alone is not a quality verdict.
