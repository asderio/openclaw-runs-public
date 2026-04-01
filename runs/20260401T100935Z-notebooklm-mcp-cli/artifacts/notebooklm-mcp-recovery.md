# NotebookLM MCP Recovery

## What was wrong

- The registered command used `npx -y notebooklm-mcp@latest`.
- In this environment, npm registry lookup fails, so the MCP server may never launch.
- NotebookLM auth is also currently not configured.

## Immediate workaround

Use the local wrapper in this request folder instead of `npx`:

```text
outputs/notebooklm-mcp-offline.sh
```

It resolves the newest cached `notebooklm-mcp` binary under `~/.npm/_npx` and runs it directly.

## Recommended config change

Change the NotebookLM MCP command from:

```text
npx -y notebooklm-mcp@latest
```

to:

```text
/absolute/path/to/outputs/notebooklm-mcp-offline.sh
```

## After launch is fixed

1. Run NotebookLM auth setup.
2. Verify health shows `authenticated: true`.
3. If auth is still broken, close Chrome and do cleanup with library preservation before re-auth.

## Known package bug

The cached package also has an ESM settings-loader issue:

- file: `dist/utils/settings-manager.js`
- symptom: `ReferenceError: require is not defined`

A patch file is included at:

```text
outputs/notebooklm-mcp-settings-manager.patch
```
