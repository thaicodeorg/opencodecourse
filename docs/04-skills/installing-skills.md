# How to Install Skills

There are three ways to get skills into your OpenCode setup, depending on where they come from.

```mermaid
flowchart TD
    A([I want to install a skill]) --> B{Where does it\ncome from?}

    B -->|Published npm package\ne.g. superpowers| C["Method 1 — npm install\ncd ~/.config/opencode\nnpm install superpowers"]
    B -->|My own / community\nsingle skill file| D["Method 2 — Manual drop\nCreate ~/.agents/skills/my-skill/\nWrite SKILL.md"]
    B -->|GitHub repo\ncollection of skills| E["Method 3 — git clone\ngit clone repo\n→ ~/.agents/skills/name/"]

    C --> F["Register in opencode.jsonc\n'plugin': ['...superpowers']"]
    D --> G["Auto-discovered ✅\nNo config change needed"]
    E --> G
    F --> H([Skill available in next session])
    G --> H

    style A fill:#4051b5,color:#fff
    style H fill:#2e7d32,color:#fff
    style C fill:#e3f2fd,color:#0d47a1
    style D fill:#e8f5e9,color:#1b5e20
    style E fill:#f3e5f5,color:#4a148c
```

---

## Method 1 — npm package (recommended for shared skill sets)

The `superpowers` package ships 14 production-ready skills in one install.

```powershell
# Navigate to the OpenCode config directory
cd "$env:USERPROFILE\.config\opencode"

# Install the package
npm install superpowers
```

Register it in `opencode.jsonc`:

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "plugin": ["~/.config/opencode/node_modules/superpowers"]
}
```

Skills are immediately available in every new session. No restart required.

---

## Method 2 — Manual file drop (for custom or community skills)

For individual skills (your own or from GitHub):

**Step 1:** Create the skill directory

```powershell
New-Item -ItemType Directory -Path "$env:USERPROFILE\.agents\skills\my-skill"
```

**Step 2:** Create the `SKILL.md` file

```powershell
# Place your SKILL.md in the directory
# See Skill File Structure for what goes inside
```

**Step 3:** Done — OpenCode discovers it automatically

No config change needed. The `~\.agents\skills\` directory is scanned on startup.

---

## Method 3 — Clone a skill repository

For skill collections from GitHub:

```powershell
# Clone directly into your skills directory
git clone https://github.com/<author>/<skills-repo> `
  "$env:USERPROFILE\.agents\skills\<skill-name>"
```

---

## Verify installation

After installing, check what OpenCode sees. Use `Ctrl+P` → **List skills** in a session, or check the directory:

```powershell
# List all custom skills
Get-ChildItem "$env:USERPROFILE\.agents\skills" -Name

# List superpowers skills
Get-ChildItem "$env:USERPROFILE\.config\opencode\node_modules\superpowers\skills" -Name
```

---

## Removing a skill

**npm package skill:** uninstall the package and remove from `opencode.jsonc`

```powershell
cd "$env:USERPROFILE\.config\opencode"
npm uninstall superpowers
```

**Manual skill:** delete the directory

```powershell
Remove-Item -LiteralPath "$env:USERPROFILE\.agents\skills\my-skill" -Recurse -Force
```

---

## Avoiding the duplication trap

If you use both Claude Code and OpenCode, skills may end up duplicated across:

- `~\.agents\skills\` 
- `~\.claude\skills\`

They are identical copies. Remove `~\.claude\skills\` to keep a single source of truth:

```powershell
Remove-Item -LiteralPath "$env:USERPROFILE\.claude\skills" -Recurse -Force
```

See [Skill Locations](skill-locations.md) for full details.
