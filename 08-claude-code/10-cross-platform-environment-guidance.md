# Cross-Platform Environment Guidance

## Purpose

Make Claude Code setup portable without assuming a specific developer operating system, shell, terminal, IDE, or execution surface.

## Discover first

Record:

- Operating system and version.
- Native OS, WSL, container, SSH/remote machine, cloud session, or desktop environment.
- Default shell and available alternatives.
- Terminal and IDE/editor.
- Claude Code version and invocation surface.
- Available runtimes used by project hooks/scripts.
- Git and repository host tools.
- Filesystem, network, proxy, and enterprise policy constraints that materially affect setup.

Do not hardcode the profile of the framework author into the product project. The framework may include examples for Windows, but the selected product configuration must reflect the actual developer environment.

## Windows considerations

- Distinguish native Windows from WSL. Do not assume they have identical path, shell, filesystem, permissions, or hook behavior.
- Determine whether Claude Code is invoking Git Bash, PowerShell, or another documented shell/tool path.
- When Git Bash is absent, current hook documentation describes different behavior for shell-form hooks and specific failure modes. Check the latest guidance before writing a blocking hook.
- If using PowerShell hooks, verify the configured shell and failure behavior explicitly. Test in the same environment used for development.
- Prefer direct executable invocation when the current hook format supports it and the executable is available; do not assume `.cmd`/`.bat` launch behavior matches `.exe` or script execution. On Windows without Git Bash, current docs describe special handling for shell-form hooks and direct executable hooks; check the current hook reference and explicitly set/test failure behavior.
- Resolve executable paths on the target machine rather than embedding another developer's absolute path.
- Avoid assuming a native Windows sandbox limitation or capability from memory. Check the current permissions/sandbox documentation and verify actual behavior on the installed version.
- Treat Read/Edit deny patterns as one layer only. Indirect shell/script access may have different behavior.

## macOS and Linux considerations

- Confirm the shell, executable paths, file permissions, line endings, package manager, and installed runtimes.
- Test hook process permissions, environment-variable handling, and file-system behavior in the target environment.
- Avoid assuming GNU/BSD command compatibility or availability of tools such as `sed`, `grep`, `find`, `timeout`, or `jq` without checking.

## WSL, containers, SSH, and cloud sessions

- Identify where code and configuration physically reside and which filesystem is mounted.
- Confirm which user/project/managed settings and credentials are available in that session type.
- Do not assume local user settings, machine credentials, hooks, or project settings all carry into cloud sessions.
- Check path translation, file watching, executable permissions, network access, and secret injection.
- Do not copy local credential files into containers, worktrees, remote sessions, or cloud environments.

## Portable automation

- Prefer scripts with explicit interpreter/runtime requirements and documented inputs/outputs.
- Declare expected shell and minimum runtime in the setup plan.
- Avoid shell-specific syntax when a small cross-platform script is practical.
- Do not claim portability until the script has been tested on the target platform.
- Record untested platforms as unverified, not supported.

## Documentation references

- [Claude Code settings and scopes](https://code.claude.com/docs/en/settings)
- [Claude Code hooks, including Windows behavior](https://code.claude.com/docs/en/hooks)
- [Claude Code permissions and PowerShell rules](https://code.claude.com/docs/en/permissions)
- [Claude Code troubleshooting](https://code.claude.com/docs/en/troubleshooting)
