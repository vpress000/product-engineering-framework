# Framework Review Report — Version 1.2.0

**Baseline reviewed:** Product Engineering Operating Framework v1.1.0 (70 Markdown files)  
**Comparison source:** `setup-new-project-prompt-v2.md` supplied by the user  
**Review date:** 2026-11-07  
**Updated version:** 1.2.0

## 1. Executive summary

Version 1.1.0 provided a broad product engineering operating model, but its Claude Code integration was less operational than the user's project-setup prompt. The v2 prompt supplied a concrete setup sequence: read-only inspection, concise findings, a two-round interview, tailored configuration, explicit approval, limited writes, and self-validation.

Version 1.2.0 adds a distinct **PEOF Claude Bootstrap** layer while preserving the universal product engineering framework. It is intended to work for greenfield, existing, modernization, framework-migration, mixed, and multi-product engagements.

## 2. Source-to-framework traceability

| Setup prompt v2 concept | v1.2.0 location | Status |
|---|---|---|
| No writes before approval | `08-claude-code/09-project-bootstrap-workflow.md`; setup first-message prompt | Implemented |
| Verify current docs, do not rely on memory | `08-claude-code/11-official-documentation-reference.md`; bootstrap workflow | Implemented |
| Never overwrite config; minimal diff | `08-claude-code/06-permissions-and-configuration-management.md` | Implemented |
| Inspect global Claude setup | `08-claude-code/05-environment-discovery-and-inventory.md` | Implemented with privacy safeguards |
| Inspect project AI configuration | Environment inventory and bootstrap workflow | Implemented |
| Inspect repo manifests, README, CI, Git, monorepo, commands | Environment inventory | Implemented |
| Inspect available developer tools | Developer environment inventory/profile | Implemented |
| Findings in 10 lines or fewer | Bootstrap workflow and prompt | Implemented |
| Two-round interview | Bootstrap workflow and first-message prompt | Implemented |
| Ask only what evidence cannot answer | Bootstrap workflow | Implemented |
| CLAUDE.md concise; scoped rules | Bootstrap workflow and existing Claude integration | Implemented; current docs recommend under 200 lines as a target |
| AGENTS.md interoperability | Environment inventory and bootstrap workflow | Implemented; verified against current docs |
| User/project/local settings separation | Permissions/config management | Implemented and updated to current docs terminology |
| Sensitive paths and permission safeguards | Permission management and inventory | Implemented with explicit limitations |
| Native Windows/shell handling | Cross-platform environment guidance | Implemented as configurable, not hardcoded |
| Hooks and portable scripts | Optional capabilities, cross-platform guidance, validation | Implemented with current Windows-specific caveats |
| Skills/subagents and least privilege | Optional capabilities, starter kit | Implemented |
| MCP service scope/authentication | Optional capabilities and permission management | Implemented |
| Plugins, CI, schedules, worktrees, agent teams | Optional capability catalogue | Implemented as opt-in |
| Approval plan with project and user-level changes separate | Setup approval template | Implemented |
| JSON/hook/project-check validation | Setup validation guide/report template | Implemented |
| Handoff, commands, commit/local guidance | Validation and handoff guide | Implemented; commands are version-aware rather than hardcoded |

## 3. Important accuracy updates from current documentation

The framework does not mechanically copy every statement from the supplied prompt. Where the prompt's details needed a current-doc check, v1.2.0 uses the more cautious, current-documentation-led rule:

- Claude Code documentation currently distinguishes user settings, shared project settings, project-local settings, and managed settings. MCP local scope is a separate concept and its local server state is stored in `~/.claude.json`; the framework explicitly says not to dump or edit that sensitive state.
- Current documentation supports `AGENTS.md` as an instruction-file alternative/companion, but the exact loading rules depend on configuration/context. The framework says to verify actual loading rather than blindly creating a duplicate `CLAUDE.md`.
- Current documentation recommends keeping CLAUDE.md instruction files concise (under 200 lines is the documented target). The framework uses this as guidance, not a rigid limit.
- Hooks have platform-specific behavior. On Windows without Git Bash, shell-form hook failures can block tool calls depending on failure handling; PowerShell-specific behavior must be tested. The framework does not promise that one hook recipe works on every shell.
- Hooks execute commands with the user's permissions and therefore require code review and safe testing.
- Agent teams are currently described in official docs as experimental and disabled by default. They remain opt-in.
- MCP, plugins, worktrees, schedules, and other extensions are optional and must be verified for the installed version and surface.

## 4. Added files

### Claude Code integration guides

- `08-claude-code/05-environment-discovery-and-inventory.md`
- `08-claude-code/06-permissions-and-configuration-management.md`
- `08-claude-code/07-optional-capabilities-and-integrations.md`
- `08-claude-code/08-setup-validation-and-handoff.md`
- `08-claude-code/09-project-bootstrap-workflow.md`
- `08-claude-code/10-cross-platform-environment-guidance.md`
- `08-claude-code/11-official-documentation-reference.md`

### Starter kit

- `08-claude-code/starter-kit/PROJECT-SETUP-FIRST-MESSAGE.md`
- `08-claude-code/starter-kit/skills/peof-project-bootstrap/SKILL.md`
- `08-claude-code/starter-kit/agents/claude-code-config-reviewer.md`

### Templates

- `09-templates/20-claude-code-setup-and-approval-plan-template.md`
- `09-templates/21-developer-environment-profile-template.md`
- `09-templates/22-setup-validation-report-template.md`

## 5. Preserved boundaries

- The 1.1.0 product engineering content remains in place.
- The 1.1.0 review report is preserved as `REVIEW-REPORT-V1.1.md`.
- No product repository, user-level Claude configuration, external service, or live Claude Code installation was modified by creating this documentation package.
- The included setup prompt and starter files are templates; they are not installed automatically.

## 6. Validation performed on v1.2.0 package

- Compared the uploaded setup prompt's major steps and optional capabilities to PEOF documents.
- Reviewed current official Claude Code documentation for settings, permissions, memory/instruction files, skills, subagents, hooks, MCP, plugins, worktrees, agent teams, desktop/schedules, and troubleshooting.
- Generated the Markdown inventory from the actual package contents.
- Checked relative Markdown links and local file references.
- Checked ZIP integrity.
- Confirmed the new starter skill/agent file shapes and that examples avoid hardcoding the user's personal Windows environment.

## 7. Remaining product-specific decisions

The framework still cannot select these without project discovery:

- OS, shell, IDE, execution surface, installed Claude Code version, and toolchain.
- Which global skills, agents, prompt library entries, plugins, MCP servers, or integrations to reuse.
- Sensitive/protected paths and permissible commands.
- Autonomy and approval posture.
- Which CI, schedule, worktree, hook, or agent-team capabilities are useful and acceptable.
- Product requirements, architecture, compliance, data, and production controls.

These are deliberately discovered per product/developer rather than hardcoded as universal defaults.

## 8. Limitations

This is a documentation-level review and package validation. It does not install or exercise the starter kit in a live Claude Code installation, test scripts on every OS/shell, validate organization-managed settings, or verify a specific product repository. Those checks must occur during the approved project bootstrap on the actual target environment.
