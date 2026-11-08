# Discovery Question Bank

Use this as a question bank, not a form to send all at once. Select questions that resolve current uncertainty. Do not re-ask what is already known.

## A. Engagement and objectives

- Is the engagement greenfield, existing-product adoption, modernization, framework migration, multi-product, or mixed?
- What decision or outcome should this engagement enable?
- What would make the framework successful in 30, 90, and 180 days?
- What must not be disrupted?
- Who sponsors and approves the work?

## B. Product and users

- What does the product do, and what problem does it solve?
- Who are the primary users, buyers, administrators, and other stakeholders?
- What are the most important user journeys and product capabilities?
- What is the business model and strategic context?
- What evidence exists about user needs and product-market fit?
- Which languages, regions, accessibility needs, and platforms are in scope?

## C. Product maturity and scope

- Is the product an idea, prototype, MVP, active development, production, or scaling?
- What is in scope now, later, and explicitly out of scope?
- What are the most important current initiatives?
- What is the roadmap and how are priorities decided?
- What customer commitments or deadlines exist?

## D. Team and ways of working

- Who performs product, design, engineering, QA, security, and operations work?
- Is development solo, in-house, outsourced, distributed, or mixed?
- How is work tracked and reviewed?
- What delivery method is used (continuous flow, Scrum, Kanban, or another approach)?
- Where do handoffs, delays, or rework commonly occur?

## E. Technology and architecture

- What languages, frameworks, platforms, databases, and hosting are used or preferred?
- What are the system boundaries and major components?
- Which external services and integrations are critical?
- What are the deployment environments and CI/CD practices?
- What are the primary scalability, performance, availability, and compatibility needs?
- What architectural constraints or decisions must be preserved?

## F. Quality and operations

- What automated and manual tests exist?
- How are defects prioritized and release quality assessed?
- How are builds, releases, rollbacks, and hotfixes handled?
- What is monitored in production, and who responds to incidents?
- What are backup, recovery, and business continuity expectations?
- What quality problems or production incidents recur?

## G. Security, privacy, and compliance

- What categories of data are collected, processed, stored, or shared?
- Are authentication, authorization, payment, health, financial, child, or other sensitive-data capabilities involved?
- Which jurisdictions, regulations, customer contracts, or industry standards apply?
- Who owns security and privacy decisions?
- Are threat models, security tests, access reviews, or audit trails required?

## H. Existing assets and migration

- Which requirements, architecture documents, runbooks, test plans, and standards are authoritative?
- Are documents current and consistent with the actual implementation?
- What existing practices work well and should be preserved?
- Which practices or files conflict or are duplicated?
- Is there an existing framework or methodology to migrate from?
- Are there active releases or teams that cannot be interrupted?
- Is migration expected to be documentation-only, process-only, tool/configuration, or technical as well?

## I. Claude Code and AI-assisted engineering

- Is Claude Code already used? By whom and for what tasks?
- Does the repository already contain `CLAUDE.md`, `.claude/rules/`, skills, agents, or hooks?
- What tasks should AI assist with, and which decisions must remain human-owned?
- Are there restrictions on code, customer data, secrets, or external tools?
- What review and verification is required for AI-generated changes?

## J. Constraints and preferences

- What budget, schedule, staffing, and tool constraints exist?
- What technologies, vendors, or practices are mandated or prohibited?
- Which existing files or directories are protected from modification?
- What should be deferred to a later phase?
- What is the preferred level of documentation and governance?

## Questioning method

Ask the smallest set of questions that unlocks the next decision. Use follow-ups to clarify ambiguous answers. Summarize what was learned and invite correction before treating it as the baseline.


## K. Developer environment and Claude Code bootstrap

Use only when Claude Code/project onboarding is in scope. Inspect first; ask only for unknowns or items that require confirmation.

- Which operating system, shell, terminal, IDE, and Claude Code surface/version are in use?
- Is the project local, WSL, containerized, remote over SSH, or in a cloud session?
- Which global Claude instructions, settings, rules, skills, and agents already exist?
- Which project-level Claude settings, instructions, skills, agents, hooks, MCP servers, and plugins already exist?
- Are there `AGENTS.md`, Cursor, Copilot, or other AI-tool instruction files that must remain authoritative?
- Which paths must never be read, written, or executed automatically?
- Which routine commands are safe, confirmed, and permitted? Which commands can mutate data, deploy, publish, or access paid/production services?
- What autonomy and approval posture is preferred?
- Which external services should Claude access directly? Ask for exact service names; do not infer.
- Which optional capabilities are actually wanted: prompt library, selected skills/agents, review workflow, plan persistence, output style, plugin, CI, schedule, worktrees, agent teams, browser/desktop integration?
- Which manual authentication, marketplace approval, CI secret, or organization-admin steps will the user perform?

Do not request secret values. Ask only for path names, capability choices, and non-sensitive environment facts.
