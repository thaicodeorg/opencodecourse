# Path Structure

Understanding where OpenCode stores files is essential for configuration, debugging, and cleanup. OpenCode separates concerns across three root locations.

## Quick map

```mermaid
graph TD
    EXE["⚙️ Binary\nchocolatey\\bin\\opencode.exe"]

    subgraph CFG ["📁 Config — ~/.config/opencode/"]
        C1["opencode.json\nmain settings"]
        C2["opencode.jsonc\nplugin declarations"]
        C3["node_modules/\ninstalled plugins"]
        C4["node_modules/superpowers/skills/\n14 built-in skills"]
        C3 --> C4
    end

    subgraph DATA ["💾 Data — ~/.local/share/opencode/"]
        D1["opencode.db\nsession database"]
        D2["auth.json\ncredentials 🔒"]
        D3["log/opencode.log\napplication log"]
        D4["snapshot/\nfile backups"]
        D5["tool-output/\ntemp files"]
    end

    subgraph SKILLS ["🧠 Skills — ~/.agents/skills/"]
        S1["your-skill/SKILL.md"]
        S2["code-review/SKILL.md"]
        S3["tdd/SKILL.md"]
        S4["37 more..."]
    end

    EXE --> CFG
    EXE --> DATA
    CFG --> SKILLS

    style CFG fill:#e3f2fd,stroke:#1565c0
    style DATA fill:#fce4ec,stroke:#880e4f
    style SKILLS fill:#e8f5e9,stroke:#2e7d32
    style D2 fill:#ffcdd2,stroke:#c62828
```

## Lessons

1. [The Binary](binary.md)
2. [Config Directory](config.md)
3. [Data Directory](data.md)
4. [Skills Locations](skills-locations.md)
