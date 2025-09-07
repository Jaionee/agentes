# Install/Use Playwright MCP

Playwright MCP is used by `visual-validator` for screenshots, diffs y validación de interacciones.

## Opción A (simple, por ejecución)
No requiere registro permanente. Cuando el validador lo pida, ejecuta:

```bash
npx @playwright/mcp@latest
```

## Opción B (registrar como MCP server en Claude Code)
Requiere Claude Code CLI. Regístralo una vez y quedará disponible:

```bash
claude mcp add playwright-mcp spawn -- npx @playwright/mcp@latest
```

Verifica el registro:
```bash
claude mcp list
```

Notas:
- La Opción A es suficiente para la mayoría de flujos.
- El orquestador pedirá permiso antes de iniciar Playwright MCP.
