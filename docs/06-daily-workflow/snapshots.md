# Snapshots

When `snapshot: true` is set in `opencode.json`, OpenCode saves a copy of each file before modifying it. This gives you a safety net for every tool write.

## Enable snapshots

```json
{
  "snapshot": true
}
```

## How snapshots work

```mermaid
flowchart TD
    A([Agent is about to edit a file]) --> B{snapshot: true\nin opencode.json?}
    B -->|No| E["✏️ Edit file directly\nno backup"]
    B -->|Yes| C["📸 Save current file state\nto snapshot/repo-hash/file-hash"]
    C --> D["✏️ Edit file"]
    D --> F{Something\nwent wrong?}
    F -->|No| G([Continue normally])
    F -->|Yes| H["Navigate to\nsnapshot/ directory"]
    H --> I["Copy snapshot file\nback to original path"]
    I --> J([File restored ✅])

    style A fill:#4051b5,color:#fff
    style C fill:#e8f5e9,color:#1b5e20
    style G fill:#2e7d32,color:#fff
    style J fill:#2e7d32,color:#fff
    style E fill:#fff3e0,color:#e65100
```

## Where snapshots live

```
%USERPROFILE%\.local\share\opencode\snapshot\
└── <repo-content-hash>\
    └── <file-hash>    ← snapshot of a specific file state
```

Each subdirectory corresponds to a repository (identified by content hash). Each file inside is a snapshot of a file at a point in time.

## Restoring from a snapshot

Snapshots are currently browsed manually — navigate to the snapshot directory, find the file version you want, and copy it back.

!!! tip "Use `share: manual`"
    Combined with `snapshot: true`, `share: "manual"` gives you full control: nothing is shared or overwritten without your explicit action.

## Disk usage

Snapshots accumulate over time. Clean up old ones periodically:

```powershell
# Remove all snapshots (safe — they are just backups)
Remove-Item "$env:USERPROFILE\.local\share\opencode\snapshot\*" -Recurse -Force
```
