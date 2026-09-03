# Path Cheatsheet

Quick reference for every OpenCode path on Windows.

## Binary

| Path | Description |
|------|-------------|
| `C:\ProgramData\chocolatey\bin\opencode.exe` | Shim on PATH |
| `C:\ProgramData\chocolatey\lib\opencode\tools\opencode.exe` | Actual binary |

## Config (`%USERPROFILE%\.config\opencode\`)

| Path | Description |
|------|-------------|
| `opencode.json` | Primary config (model, snapshot, logLevel…) |
| `opencode.jsonc` | Plugin declarations |
| `package.json` | npm plugin manifest |
| `node_modules\superpowers\` | Built-in skills package |
| `node_modules\superpowers\skills\` | 14 built-in skill files |

## Data (`%USERPROFILE%\.local\share\opencode\`)

| Path | Description |
|------|-------------|
| `opencode.db` | SQLite session database |
| `auth.json` | API keys / OAuth tokens (**keep private**) |
| `mcp-auth.json` | MCP server credentials (**keep private**) |
| `log\opencode.log` | Application log |
| `snapshot\` | Pre-write file snapshots |
| `storage\session_diff\` | Per-session file diffs |
| `tool-output\` | Temporary tool output |

## Skills

| Path | Description |
|------|-------------|
| `%USERPROFILE%\.agents\skills\` | Your custom skills (primary) |
| `%USERPROFILE%\.config\opencode\node_modules\superpowers\skills\` | Built-in skills |
| `%USERPROFILE%\.claude\skills\` | Legacy duplicate — delete if present |

## macOS / Linux equivalents

| Windows | macOS / Linux |
|---------|--------------|
| `%USERPROFILE%\.config\opencode\` | `~/.config/opencode/` |
| `%USERPROFILE%\.local\share\opencode\` | `~/.local/share/opencode/` |
| `%USERPROFILE%\.agents\skills\` | `~/.agents/skills/` |
