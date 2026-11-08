# Project Instructions for Claude Code — Template

> Replace bracketed placeholders with verified product information. Keep this file concise. Link to detailed documentation rather than copying entire standards here. Verify current Claude Code documentation before using this template in a repository.

## Project summary

- Product: [name and one-sentence purpose]
- Users: [primary users]
- Stage: [idea/prototype/development/production/scaling]
- Main technologies: [verified stack]
- Architecture overview: [link]
- Product profile: [link]

## Source of truth

- Requirements: [location]
- Architecture/ADRs: [location]
- UX/design: [location]
- Backlog/work tracking: [tool/location]
- Testing strategy: [location]
- Operations/runbooks: [location]

If sources conflict, do not guess. Identify the conflict and ask the responsible owner or follow the documented authority order.

## Engineering workflow

1. Understand the task, requirements, and affected implementation group.
2. Inspect relevant code and existing patterns before proposing changes.
3. Summarize assumptions, dependencies, and intended file changes.
4. Implement the smallest coherent, reviewable increment.
5. Add or update appropriate tests and documentation.
6. Run the relevant project checks and report actual results.
7. Review the diff for unintended changes and compatibility risks.

## Project-specific standards

- Language/framework conventions: [link]
- Formatting/lint/type checks: [commands]
- Test commands: [commands]
- Build commands: [commands]
- Security/privacy rules: [link]
- Commit/PR conventions: [link]

## Boundaries

- Do not modify protected paths: [list or state none known].
- Do not access, print, commit, or expose secrets or sensitive user data.
- Do not deploy, change production data, or alter infrastructure without explicit approval.
- Do not make broad refactors unrelated to the task.
- Ask before destructive or hard-to-reverse changes.

## Product-specific constraints

[List only confirmed, current constraints. Include owner/source and effective date for constraints that may change.]

## Required completion report

Summarize changes, requirements addressed, tests/checks actually run and results, known limitations, risks, and any decisions needing human approval.


## Session efficiency

- Keep this instruction file concise and link to detailed standards.
- Load only the documents and skills relevant to the current work package.
- Use the project's current status/handoff file to resume work; do not repeat full discovery without a reason.
- Prefer targeted reads and concise command output.
- Use model/effort and subagents proportionately to task complexity and risk.
- Do not mistake `/clear`, `/compact`, or a new session for a subscription-usage reset.
