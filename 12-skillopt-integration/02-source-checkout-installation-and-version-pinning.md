# SkillOpt Source Checkout, Installation, and Version Pinning

## Purpose

Specify a reproducible way to use Microsoft's SkillOpt repository alongside PEOF and a product repository.

## Recommended installation choice

For the PEOF integration described in this release, prefer a **separate source checkout** of `microsoft/SkillOpt`, because the official installation page distinguishes the PyPI wheel from source-only assets and states that some features documented on `main` require a source install until the next package release. The source repository also contains agent integration shells, benchmark configurations, data materializers, tests, and plugin files that are not all included in the wheel.

This is a point-in-time statement. Before each installation or upgrade, inspect the current official installation page and release notes. Do not assume the feature list or package version remains unchanged.

## Workspace layout

Keep the SkillOpt checkout outside the product repository, for example:

```text
workspace/
├── tools/SkillOpt/             # Microsoft source checkout or controlled fork
└── products/my-product/        # actual product repository
```

This allows multiple products to use a shared, pinned SkillOpt installation without copying upstream source into each product. If projects require incompatible SkillOpt revisions, use separate worktrees or clones and record the mapping in each integration profile.

## Initial checkout and installation

From a tools directory:

```bash
git clone https://github.com/microsoft/SkillOpt.git
cd SkillOpt
git remote -v
git status --short
git rev-parse HEAD
python --version
python -m venv .venv
```

Activate the virtual environment using the command for the current shell/OS (for example, PowerShell: `./.venv/Scripts/Activate.ps1`; macOS/Linux: `source .venv/bin/activate`), then:

```bash
python -m pip install --upgrade pip
python -m pip install -e .
python -m skillopt_sleep --help
python scripts/train.py --help
python scripts/eval_only.py --help
```

The official repository currently documents Python 3.10 or newer. Optional extras are benchmark/backend specific; install only the extras required by the selected use case. Check the checkout's own `pyproject.toml`, docs, and `--help` output before relying on a command or option.

## Pin the integration

Do not deploy from a moving `main` branch without recording the resolved revision. After checkout:

1. Record `git remote get-url origin`.
2. Record `git rev-parse HEAD` as the exact source commit.
3. Record the `skillopt` and `skillopt_sleep` version output available in that checkout.
4. Record Python version, OS, shell, CLI paths, and installed optional dependencies.
5. Keep local PEOF patches on a named branch or maintained fork; do not silently edit upstream `main`.
6. Before upgrade, inspect release notes, diff the upstream changes, rerun the integration smoke suite, and update the integration profile.

A tag or commit is the reproducibility anchor. The string `main` alone is not.

## Native Windows runner

For a native Windows setup, use PowerShell and the SkillOpt checkout's documented PowerShell runner when the selected integration provides one (the repository documents a `plugins/run-sleep.ps1` route for supported integrations). Otherwise invoke the Python module/CLI from the activated environment. Do not assume the Claude plugin's `.sh` wrapper is executable in PowerShell. Verify the actual runner file exists in the pinned checkout and that it invokes the intended Python environment.

## Claude Code plugin integration

If the project uses Claude Code and the SkillOpt checkout contains the documented plugin, follow its current README from the checkout root. The current repository documentation describes this pattern:

```text
/plugin marketplace add ./plugins/claude-code
/plugin install skillopt-sleep@skillopt-sleep
/skillopt-sleep status
```

Verify the exact marketplace/plugin command against the checked-out plugin README before use. Test `/skillopt-sleep status` immediately after installation. Some plugin wrappers depend on shared runner files outside the plugin cache; if the wrapper cannot locate its runner, use the documented source-checkout runner or installed CLI instead of improvising a path. Installing the plugin does not itself authorize session harvesting, provider transmission, scheduling, or adoption. Review the skill/plugin permissions and current instructions first.

## Native Windows and shell considerations

SkillOpt's repository includes Windows robustness work and Windows-specific runner scripts for some integrations. Do not assume a Unix shell script runs natively in PowerShell. Prefer the documented PowerShell runner where provided, or invoke the installed Python module/CLI from the intended virtual environment. Verify paths, quoting, authentication, and scheduled-task environment explicitly. Do not switch to WSL unless the developer profile permits it.

## Do not commit local state or secrets

Keep API keys, provider configuration, venvs, local transcript data, session archives, evidence logs, run outputs, staging folders, and machine-specific settings out of source control unless a deliberate sanitized fixture is approved. Add appropriate ignore rules after inspecting existing `.gitignore`; do not overwrite it.

## Reproducibility record

Use the SkillOpt Integration Profile template. At minimum capture:

- remote URL, branch, tag/commit SHA, dirty/clean status;
- `skillopt` and `skillopt_sleep` versions;
- Python and OS/shell versions;
- install mode (`editable source`, package, or other documented mode);
- optional extras and plugin version;
- command paths and model/backend configuration identifiers (never credentials);
- benchmark/adapter revision and task manifest hashes.

## Sources

- [Official installation guide](https://github.com/microsoft/SkillOpt/blob/main/docs/guide/installation.md)
- [Repository README](https://github.com/microsoft/SkillOpt)
- [Claude Code plugin README](https://github.com/microsoft/SkillOpt/tree/main/plugins/claude-code)
