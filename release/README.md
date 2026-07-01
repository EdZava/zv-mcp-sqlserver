# release-microsoft_sql_server_mcp (release)

Paquete **standalone** para `uvx --from git+...@TAG?subdir=release`.

## Cliente MCP (`mcp.json`)

```json
"git+https://github.com/EdZava/zv-mcp-sqlserver.git#0.1.0-release.1?subdir=release"
```

## Regenerar

```bash
mcp-release-toolkit sync --config .mcp-release.toml
git add release/ .mcp-release.toml
git tag 0.1.0-release.1
git push origin main --tags
```
