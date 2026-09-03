# Tips & Tricks

## Use Ctrl+P constantly

The command palette (`Ctrl+P`) is the fastest way to access everything — model switching, session management, skill invocation, settings.

## Start every complex task with a skill

Before writing any code for a non-trivial feature:

```
skill brainstorming
```

This forces requirement clarification before implementation. Saves hours of rework.

## Keep skills single-purpose

A skill that does one thing well beats a skill that tries to do everything. If your skill has more than 5 steps, consider splitting it.

## Audit your skills location once

Run this check after any major config change to ensure no duplicate skill directories exist:

```powershell
Compare-Object `
  (Get-ChildItem "$env:USERPROFILE\.agents\skills" -Name | Sort-Object) `
  (Get-ChildItem "$env:USERPROFILE\.claude\skills" -Name -ErrorAction SilentlyContinue | Sort-Object)
```

## Commit config to git

Put your `opencode.json` and `opencode.jsonc` under version control (in a private repo). Exclude `auth.json` and `mcp-auth.json`.

```gitignore
# .gitignore for ~/.config/opencode/
node_modules/
auth.json
mcp-auth.json
```

## Use `logLevel: DEBUG` when debugging

Temporarily set `"logLevel": "DEBUG"` in `opencode.json` to see exactly what OpenCode is doing. Check the log at:

```
%USERPROFILE%\.local\share\opencode\log\opencode.log
```

Reset to `"INFO"` when done — `DEBUG` generates a lot of output.

## Set `autoupdate: notify`

```json
{ "autoupdate": "notify" }
```

This tells you when a new version is available without auto-updating mid-session.
