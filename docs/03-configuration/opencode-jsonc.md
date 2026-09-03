# opencode.jsonc & Plugins

**Location:** `%USERPROFILE%\.config\opencode\opencode.jsonc`

The `.jsonc` file supports comments and is conventionally used for plugin declarations.

## Example

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  // Load the superpowers skills package
  "plugin": ["~/.config/opencode/node_modules/superpowers"]
}
```

## The `plugin` key

`plugin` is an array of paths to npm packages. Each package can contribute:

- **Skills** — workflow instruction files loaded into the system prompt
- **MCP servers** — tool providers exposed to OpenCode
- **Prompts** — reusable prompt templates

## Installing a plugin package

```powershell
cd "$env:USERPROFILE\.config\opencode"
npm install <package-name>
```

Then register it:

```jsonc
{
  "plugin": [
    "~/.config/opencode/node_modules/superpowers",
    "~/.config/opencode/node_modules/<package-name>"
  ]
}
```

## Plugin loading flow

```mermaid
flowchart TD
    A([OpenCode reads opencode.jsonc]) --> B["Parse plugin array\n[path1, path2, ...]"]
    B --> C{For each plugin path}
    C --> D["Resolve path\n~/ → USERPROFILE"]
    D --> E["Load package\nfrom node_modules/"]
    E --> F{What does\nthe package provide?}
    F -->|skills/| G["Inject SKILL.md files\ninto system prompt"]
    F -->|mcp servers| H["Register MCP tools\nfor the session"]
    F -->|prompts| I["Make prompt templates\navailable"]
    G --> J([Session starts with\nall capabilities loaded])
    H --> J
    I --> J

    style A fill:#4051b5,color:#fff
    style J fill:#2e7d32,color:#fff
    style G fill:#e8f5e9,color:#1b5e20
    style H fill:#e3f2fd,color:#0d47a1
```

## Why two config files?

| File | Syntax | Best for |
|------|--------|----------|
| `opencode.json` | Strict JSON | Core settings (model, snapshot…) |
| `opencode.jsonc` | JSON with comments | Plugin lists (comments explain each plugin) |

Both are merged — there is no conflict between them.
