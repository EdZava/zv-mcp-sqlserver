# Seguridad — zv-mcp-sqlserver

## Principios

1. **Tag git fijado** en el consumidor (`mcp.json` de GestionG5).
2. **`release/uv.lock`**: dependencias PyPI reproducibles al instalar con `uvx --from git+...@TAG?subdir=release`.
3. Regenerar `release/` tras cambios en `pyproject.toml` o codigo fuente.

## Instalacion reproducible (release/)

```text
uvx --from git+https://github.com/EdZava/zv-mcp-sqlserver.git@0.1.0-release.1?subdir=release
```

- `release/uv.lock` fija dependencias PyPI.
- `release/src/` contiene solo el codigo del MCP.

## Regenerar release

Configuracion en `.mcp-release.toml`; sincronizacion con [zv-mcp-release-toolkit](https://github.com/EdZava/zv-mcp-release-toolkit):

```bash
./scripts/sync-release.sh
git add release/ .mcp-release.toml
git tag 0.1.0-release.2   # incrementar release_suffix en .mcp-release.toml
git push origin main --tags
```

## Reporte

Incidencias de seguridad: mantenedor del fork EdZava.
