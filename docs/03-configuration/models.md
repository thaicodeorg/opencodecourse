# Switching Models

## Change the default model

Edit `opencode.json`:

```json
{
  "model": "anthropic/claude-opus-4-5"
}
```

## Available models

### Anthropic

| Model ID | Notes |
|----------|-------|
| `anthropic/claude-sonnet-4-6` | Recommended default — fast, capable |
| `anthropic/claude-opus-4-5` | Most capable, slower, higher cost |
| `anthropic/claude-haiku-4-5` | Fastest, lowest cost |

### OpenAI

| Model ID | Notes |
|----------|-------|
| `openai/gpt-4o` | Strong general model |
| `openai/gpt-4o-mini` | Fast and cheap |

## Switch model mid-session

Use the command palette (`Ctrl+P`) → **Change model** to switch without editing config.

## `model` vs `small_model`

| Key | Used for |
|-----|---------|
| `model` | All user-facing conversations |
| `small_model` | Internal lightweight tasks (summarisation, routing) |

Setting both to the same model is fine — it simplifies billing and keeps behaviour predictable.

!!! tip "Start with Sonnet"
    `claude-sonnet-4-6` is the best balance of speed and capability for daily use. Switch to Opus only when you need maximum reasoning depth.
