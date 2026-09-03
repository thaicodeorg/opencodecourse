# The Binary

## Windows (Chocolatey install)

| Path | Role |
|------|------|
| `C:\ProgramData\chocolatey\bin\opencode.exe` | Shim on `PATH` — what you type |
| `C:\ProgramData\chocolatey\lib\opencode\tools\opencode.exe` | Actual executable |

The shim delegates to the real binary. You rarely need to touch either directly.

## Verify your install

```powershell
# Which binary is on PATH?
where.exe opencode

# What version?
opencode --version
```

## Updating

```powershell
choco upgrade opencode
```

OpenCode can also notify you of updates automatically — see [autoupdate in opencode.json](../03-configuration/opencode-json.md).
