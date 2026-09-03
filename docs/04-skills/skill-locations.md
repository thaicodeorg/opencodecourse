# Skill Locations

Skills are discovered from multiple directories. Understanding them prevents duplication.

## Discovery order

```
1. %USERPROFILE%\.agents\skills\<name>\SKILL.md       ← user skills (primary)
2. %USERPROFILE%\.config\opencode\node_modules\        ← plugin skills
   superpowers\skills\<name>\SKILL.md
3. %USERPROFILE%\.claude\skills\<name>\SKILL.md        ← Claude Code compat (avoid)
```

## The duplication trap

If you previously used Claude Code, skills may exist in both `~\.agents\skills\` and `~\.claude\skills\`. They are identical copies — one is wasted space.

**Check for duplicates:**

```powershell
$a = Get-ChildItem "$env:USERPROFILE\.agents\skills" -Name | Sort-Object
$c = Get-ChildItem "$env:USERPROFILE\.claude\skills" -Name | Sort-Object
Compare-Object $a $c
```

No output = identical sets = safe to remove one.

**Remove the duplicate:**

```powershell
Remove-Item -LiteralPath "$env:USERPROFILE\.claude\skills" -Recurse -Force
```

## Rule of thumb

| Location | Use for |
|----------|---------|
| `~\.agents\skills\` | All your custom and third-party skills |
| `superpowers\skills\` | Built-in skills (don't edit these) |
| `~\.claude\skills\` | Don't use — legacy path |
