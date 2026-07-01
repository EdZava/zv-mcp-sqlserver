# Seguridad — zv-mcp-sqlserver

## Principios

1. **Commit SHA fijado** en el consumidor (`mcp.json` de GestionG5).
2. **`uv.lock`** en la raiz: dependencias Python reproducibles al instalar con `uvx --from git+...@<sha>`.
3. Actualizar el lock solo con revision y `uv lock` tras cambios en `pyproject.toml`.

## Antes de actualizar el SHA en GestionG5

```bash
uv lock
uv export --format requirements.txt --output-file /tmp/deps.txt  # opcional, revision
git add uv.lock && git commit -m "chore: uv.lock"
git push origin main
```

## Reporte

Incidencias de seguridad: mantenedor del fork EdZava.
