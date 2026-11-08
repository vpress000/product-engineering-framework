# Claude Code Starter Kit and Adoption

## What this package provides

The `starter-kit/` folder contains copy-ready Markdown examples for project instructions, specialist subagents, reusable skills, a first-message bootstrap prompt, and a read-only configuration reviewer. These are optional starting points, not an auto-installed plugin and not permission to alter a repository.

## Copy map

Copy only after project discovery and owner approval:

- `starter-kit/CLAUDE.md` → project root `CLAUDE.md` (or merge relevant sections into the existing file).
- `starter-kit/agents/*.md` → `.claude/agents/`.
- `starter-kit/skills/<skill-name>/SKILL.md` → `.claude/skills/<skill-name>/SKILL.md`.

Do not overwrite existing instructions or files. Reconcile the current project instructions first. Keep the starter kit in this framework library as the canonical template and customize copies in each product repository.

## Bootstrap workflow

For new and existing project onboarding, start with `PROJECT-SETUP-FIRST-MESSAGE.md` or invoke the `peof-project-bootstrap` skill. The workflow begins read-only, summarizes findings, interviews in progressive rounds, presents a complete approval plan, and writes only approved items. Use the separate developer environment profile; do not mix OS/shell/Claude preferences into the product profile.

The optional `claude-code-config-reviewer` agent is read-only and is intended to identify configuration conflicts before/after setup. Do not treat it as a substitute for validating the installed version or human approval.

## Why the kit is conservative

The included skill files use the required `SKILL.md` naming and minimal `name`/`description` frontmatter. The agent files use `name` and `description` frontmatter. More advanced fields, tool restrictions, permissions, hooks, and settings are deliberately not preconfigured because they should be selected for the actual tools, risk, operating system, and current Claude Code version. The bootstrap prompt and setup guides require current documentation verification before writing them.

## Setup and validation

1. Check current official Claude Code documentation linked below.
2. Inspect existing `CLAUDE.md`, `.claude/rules/`, `.claude/agents/`, `.claude/skills/`, settings, hooks, and plugins.
3. Merge project-specific context and existing rules; keep `CLAUDE.md` concise.
4. Copy the selected agents and skills into the approved project paths.
5. Do not grant broad tool permissions by default. Use the least capability needed.
6. Test that each skill is discoverable and that each agent gives the expected bounded output.
7. Review generated changes, run the project's checks, and confirm configuration status using the current CLI guidance.
8. Record the installed version and any customizations in the product profile.

## Official documentation

- [Claude Code memory and project instructions](https://code.claude.com/docs/en/memory)
- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [Claude Code subagents](https://code.claude.com/docs/en/sub-agents)
- [Claude Code hooks](https://code.claude.com/docs/en/hooks)
- [Claude Code settings](https://code.claude.com/docs/en/settings)

Documentation checked for this framework review on 2026-11-07. Recheck before implementation because supported fields and behavior can change.


## User-level versus project-level setup

Do not copy personal skills, prompt libraries, or global settings into the project automatically. List them, explain their scope, and ask which ones should be reused. Project-shared configuration should contain only team-relevant settings; machine-specific configuration and credentials stay local. Check the current official docs for settings, AGENTS.md, skills, agents, hooks, MCP, plugins, and worktrees before installation.
