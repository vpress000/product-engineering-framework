# Official Claude Code Documentation Reference

**Reference checked:** 2026-11-07  
**Purpose:** Navigation index for validating Claude Code configuration before use.

Claude Code changes over time. This index is not a frozen specification. Before creating configuration, open the relevant official page and confirm current support, syntax, scope, platform behavior, and version requirements.

| Topic | Official documentation | Check before |
|---|---|---|
| Overview and supported surfaces | [Overview](https://code.claude.com/docs/en/overview) | Choosing CLI, IDE, Desktop, or cloud workflow |
| Project instructions, rules, AGENTS.md, auto memory | [Memory and instructions](https://code.claude.com/docs/en/memory) | Creating or importing instruction files |
| Settings paths, scopes, precedence | [Settings](https://code.claude.com/docs/en/settings) | Writing settings JSON or choosing user/project/local scope |
| Permission rules and modes | [Permissions](https://code.claude.com/docs/en/permissions) | Allow/ask/deny rules, sandboxing, shell behavior |
| Skills and skill frontmatter | [Skills](https://code.claude.com/docs/en/skills) | Creating project/global skills and controlling invocation |
| Subagents and tool restrictions | [Subagents](https://code.claude.com/docs/en/sub-agents) | Creating agents, choosing tools, delegating tasks |
| Hooks and hook event schemas | [Hooks](https://code.claude.com/docs/en/hooks) | Registering command hooks, event matchers, exit codes, platform behavior |
| MCP servers and scopes | [MCP](https://code.claude.com/docs/en/mcp) | Adding named service integrations and selecting scope |
| Plugins and marketplaces | [Plugins](https://code.claude.com/docs/en/plugins) | Installing or packaging plugins |
| Git worktrees | [Worktrees](https://code.claude.com/docs/en/worktrees) | Parallel sessions, ignored-file sharing, cleanup |
| Agent teams | [Agent teams](https://code.claude.com/docs/en/agent-teams) | Considering experimental multi-agent coordination |
| Desktop app and scheduled tasks | [Desktop](https://code.claude.com/docs/en/desktop) | Selecting desktop workflows or scheduled tasks |
| Diagnostics | [Troubleshooting](https://code.claude.com/docs/en/troubleshooting) | Debugging settings, hooks, MCP, and search |

## Version-aware verification procedure

1. Detect the installed Claude Code version and execution surface.
2. Open the specific official documentation for each capability being configured.
3. Check whether the setting, field, command, hook event, frontmatter, or feature is supported in that version/surface.
4. Confirm whether it belongs in user, project, local, managed, plugin, or MCP scope.
5. Check platform-specific behavior and any experimental/beta status.
6. Record the document URL and date checked in the setup approval plan.
7. Do not create a configuration element if current support cannot be verified; mark it as unresolved and ask the user.

## Key distinctions worth checking

- `CLAUDE.md` and `AGENTS.md` provide instructions, but are context rather than an enforcement boundary. Use permissions/hooks/OS controls for enforcement, understanding their limits.
- `.claude/settings.json` and `.claude/settings.local.json` have different sharing and scope implications.
- MCP local scope is not the same as project-local settings; consult the MCP page.
- Skills, subagents, plugins, and MCP servers are different extension mechanisms. Select the least complex one that meets the need.
- Agent teams are documented as experimental and disabled by default in the current reference; confirm before enabling.
- Hooks execute commands and must be treated as executable code with the user's permissions.

## Maintenance

Recheck this index whenever Claude Code is upgraded or when PEOF is released. Update the `Reference checked` date and amend any workflow impacted by documentation changes. Do not rely on version-specific examples copied into old reports.
