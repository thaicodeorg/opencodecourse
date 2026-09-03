# Config Directory

```
%USERPROFILE%\.config\opencode\
├── opencode.json        ← primary config (model, snapshot, share…)
├── opencode.jsonc       ← secondary config (plugins)
├── package.json         ← npm manifest for plugins
├── package-lock.json
└── node_modules\        ← installed plugin packages
    ├── superpowers\     ← built-in skills package
    ├── @opencode-ai\
    ├── @ai-sdk\
    └── zod\
```

## How config loads at startup

```mermaid
flowchart LR
    A([opencode starts]) --> B["Read opencode.json\nmodel, snapshot, logLevel"]
    A --> C["Read opencode.jsonc\nplugin declarations"]
    B --> D[Merge into\nruntime config]
    C --> D
    D --> E{Plugins declared?}
    E -->|Yes| F["Load node_modules/\nplugin packages"]
    E -->|No| G[Start session]
    F --> G

    style A fill:#4051b5,color:#fff
    style G fill:#2e7d32,color:#fff
    style D fill:#e3f2fd,color:#0d47a1
```

## Two config files

OpenCode merges both files at startup. The split is conventional:

| File | Purpose |
|------|---------|
| `opencode.json` | Core settings: model, snapshot, log level |
| `opencode.jsonc` | Plugin declarations (supports comments) |

## Plugin packages

Plugins are standard npm packages installed into `node_modules\`. The `superpowers` package is the most common — it ships the built-in skills.

```powershell
# Install a plugin
cd %USERPROFILE%\.config\opencode
npm install <package-name>
```

See [Installing Plugins](../05-plugins-mcp/installing-plugins.md) for full details.
