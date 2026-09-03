# Data Directory

```
%USERPROFILE%\.local\share\opencode\
├── opencode.db          ← SQLite: sessions, messages, state
├── opencode.db-shm      ← SQLite shared memory
├── opencode.db-wal      ← SQLite write-ahead log
├── auth.json            ← authentication credentials
├── mcp-auth.json        ← MCP server credentials
├── log\
│   └── opencode.log     ← application log
├── snapshot\
│   └── <repo-hash>\     ← file snapshots per repo
├── storage\
│   └── session_diff\    ← per-session file diffs
└── tool-output\         ← temporary tool output files
```

## Key files explained

### `opencode.db`
SQLite database storing all session history, messages, and application state. Do not edit manually.

### `auth.json`
Stores your API keys and OAuth tokens. Keep this file private — never commit it to git.

### `snapshot\`
When `snapshot: true` is set in `opencode.json`, OpenCode saves file state before each tool invocation here. Enables undo. Each subdirectory is named after a repo content hash.

### `log\opencode.log`
Useful for debugging. Log level is controlled by `logLevel` in `opencode.json`.

### `tool-output\`
Temporary files written by tool calls (e.g. large command output). Auto-cleaned periodically.

!!! warning "Don't commit data dir to git"
    The data directory contains credentials and personal session history. Always add it to `.gitignore`.
