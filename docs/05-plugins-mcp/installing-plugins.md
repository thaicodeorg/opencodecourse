# Installing Plugins

Plugins are npm packages installed into `%USERPROFILE%\.config\opencode\node_modules\`.

## Install a plugin

```powershell
cd "$env:USERPROFILE\.config\opencode"
npm install <package-name>
```

## Register the plugin

Add it to `opencode.jsonc`:

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "plugin": [
    "~/.config/opencode/node_modules/superpowers",
    "~/.config/opencode/node_modules/<package-name>"
  ]
}
```

## The superpowers plugin

The most important plugin. Installs the built-in skills package.

```powershell
cd "$env:USERPROFILE\.config\opencode"
npm install superpowers
```

```jsonc
{
  "plugin": ["~/.config/opencode/node_modules/superpowers"]
}
```

## Uninstall a plugin

```powershell
cd "$env:USERPROFILE\.config\opencode"
npm uninstall <package-name>
```

Then remove it from the `plugin` array in `opencode.jsonc`.

!!! warning "Plugin path format"
    Use `~/.config/opencode/node_modules/...` (forward slashes, tilde) in the JSON even on Windows. OpenCode resolves the tilde cross-platform.
