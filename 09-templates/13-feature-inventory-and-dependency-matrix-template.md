# Feature Inventory and Dependency Matrix — [Product / Release]

- **Owner:** [name/role]
- **Baseline date / version:** [date/version]
- **Source of truth:** [backlog / SRS / repository / other]

## Feature inventory
| Feature ID | Feature / capability | Outcome / user journey | Requirement link | Shared component/data/API | Complexity | Risk / uncertainty | Status |
|---|---|---|---|---|---|---|---|
| [F-001] | [name] | [outcome] | [link] | [shared assets] | [low/medium/high] | [notes] | [status] |

## Dependency matrix
| Feature ID | Depends on | Blocks | Dependency type | Owner | Needed by | Confidence |
|---|---|---|---|---|---|---|
| [F-001] | [IDs] | [IDs] | [technical/data/API/business/external] | [owner] | [date/stage] | [low/medium/high] |

## Shared functionality and grouping rationale
[Common capabilities, data models, interfaces, design work, test fixtures, and why bundling creates value.]

## Proposed implementation groups
| Group ID | Group name | Included feature IDs | Predecessor groups | Group outcome | Validation boundary |
|---|---|---|---|---|---|
| [G-01] | [name] | [IDs] | [IDs] | [outcome] | [criteria] |

## Sequencing and quick wins
[Independent parallel work, prerequisites, critical path, quick wins, and risks.] 

## Grouping checks
- [ ] No unrelated features were grouped only for convenience.
- [ ] Shared work and integration overhead are identified.
- [ ] Group size remains reviewable and testable.
- [ ] Tests run continuously within the group, not only at the end.
- [ ] Cross-group contracts and dependencies are explicit.
- [ ] Deployment coupling is deliberate and documented.
