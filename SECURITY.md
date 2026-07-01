# Seguridad — zv-mcp-sqlserver

## Principios

1. **Commit SHA fijado** en el consumidor (`mcp.json` de GestionG5).
2. **`uv.lock`** en la raiz: dependencias Python reproducibles al instalar con `uvx --from git+...@<sha>`.
3. Actualizar el lock solo con revision y `uv lock` tras cambios en `pyproject.toml`.

## Instalacion reproducible (release/)

```text
uvx --from git+https://github.com/EdZava/zv-mcp-sqlserver.git@0.1.0-edzava.1?subdir=release
```

- `release/uv.lock` fija dependencias PyPI.
- `release/src/` contiene solo el codigo del MCP.

## Regenerar release

```bash
python scripts/sync-python-release.py
git add release/ scripts/sync-python-release.py
git tag 0.1.0-edzava.2
git push origin main --tags
```

## Antes de actualizar el tag en GestionG5

```bash
uv lock
uv export --format requirements.txt --output-file /tmp/deps.txt  # opcional, revision
git add uv.lock && git commit -m "chore: uv.lock"
git push origin main
```

## Reporte

Incidencias de seguridad: mantenedor del fork EdZava.
