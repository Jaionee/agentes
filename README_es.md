# Sistema de Agentes Anti-Genérico UI/UX (Producto)

Bienvenido al Sistema de Agentes Anti-Genérico UI/UX. Este documento te guiará paso a paso para usar los agentes de Claude Code y generar interfaces únicas y premium.

## ¿Qué es el Sistema de Agentes Anti-Genérico UI/UX?

Es un sistema completo que utiliza agentes especializados de Claude Code para crear interfaces premium y únicas. El sistema está **operativo** con todos los agentes implementados.

- **Puntos de entrada principales**: agente `design-orchestrator`, comando `/anti-iterate`

## Destacados

- **Orquestación Multi-Agente**: Investigación de mercado → Personas → Diseño → Validación → Accesibilidad → Rendimiento → Resiliencia → Instantánea
- **Salidas Framework-Agnostic**: Primero HTML/CSS vanilla; opciones React/Vue/Svelte
- **Iteración de Copy y CTA basada en Mercado**: Original; NO copiar competidores
- **Control de Locale**: Por defecto en-US; sin auto-traducción salvo petición
- **UI/UX Auto-Curativa**: Con `resilience-sentinel` (skeletons, reduced-motion, fallbacks, SSR guards)
  - Validación visual con Playwright MCP; fallback con Bright Data + Fetch
  - Memoria del proyecto en `/.claude/memory/` y opcional MCP Memory Service

## Instalación

### Para uso en un proyecto (Project-Specific)

```bash
mkdir -p .claude/agents .claude/commands
cp <path-to-repo>/full-system/agents/*.md .claude/agents/
cp <path-to-repo>/.claude/commands/*.md .claude/commands/
```

### Para uso global (todos los proyectos)

```bash
mkdir -p ~/.claude/agents ~/.claude/commands
cp <path-to-repo>/full-system/agents/*.md ~/.claude/agents/
cp <path-to-repo>/.claude/commands/*.md ~/.claude/commands/
```

### Uso

Una vez copiados, Claude Code detectará automáticamente estos agentes y slash commands.

## Documentación

- **Visión de Producto**: `docs/PRODUCT_OVERVIEW.md`
- **Inicio Rápido**: `docs/QUICK_START.md`
- **Integraciones**: `docs/INTEGRATIONS.md`
- **Validación & QA**: `docs/VALIDATION.md`
- **Seguridad**: `docs/SECURITY.md`
- **Roadmap**: `docs/ROADMAP.md`
- **FAQ**: `docs/FAQ.md`
- **Soporte**: `SUPPORT.md`
- **Lanzamientos**: `docs/RELEASING.md`

### Traducciones

- **English**: `README.md`
- **Español**: `README_es.md`

## Requisitos

- Claude Code (Desktop/CLI) con subagentes habilitados
- Node 18+ (probado con Node 23) y NPX
- MCPs opcionales:
  - Playwright MCP (validación visual)
  - Bright Data MCP + Fetch (fallback y enriquecimiento web)
  - Memory MCP (memoria semántica persistente)

## Inicio Rápido

### Opción A (recomendada, Lenguaje Natural):
1) Selecciona el agente `design-orchestrator`.
2) Pega:
```text
Design anti-generic UI for "<ProjectName>" competing with <Competitor1>, <Competitor2>.
Industry: <Industry>. Audience/Geo: <Audience>. Primary goal: <Goal>. Constraints: <Constraints or none>.
Locale: en-US. Do not copy competitor content. Produce original, differentiated copy.
Run the full premium iteration: market-analyst → persona-forge → design-builder → visual-validator → accessibility-guardian → performance-optimizer → resilience-sentinel → snapshot.
Enforce copy/CTA policy: 2–3 headlines & subheads AND 3 CTA variants per design variant with micro-interaction specs.
Gate: If Uniqueness < 75 or Locale mismatch or CTAs < 3/variant, iterate and revalidate. Persist updates to .claude/memory/project_context.json.
```

### Opción B (Slash Command):
```text
/anti-iterate project:"<ProjectName>" industry:"<Industry>" audience:"<Audience/Geo>" goal:"<Goal>" locale:"en-US" competitors:"https://competitor1.com, https://competitor2.com"
```
Ver `/.claude/commands/anti-iterate.md`.

## Configuración MCP (opcional)

- **Playwright MCP (ad-hoc)**:
```bash
npx @playwright/mcp@latest
```
- **Playwright MCP (registrar una vez)**:
```bash
claude mcp add playwright-mcp spawn -- npx @playwright/mcp@latest
claude mcp list
```
- **Memory MCP (ejemplo con uv)**:
```bash
claude mcp add memory-service spawn -- /opt/homebrew/bin/uv --directory /Users/<you>/path/to/mcp-memory-service run memory
```

## Permisos recomendados — `/.claude/settings.local.json`
```json
{
  "permissions": {
    "allow": [
      "mcp__brave-search__brave_web_search",
      "mcp__fetch__fetch_markdown",
      "mcp__fetch__fetch_html",
      "mcp__brightdata-server__scrape_as_markdown",
      "mcp__brightdata-server__scraping_browser_navigate",
      "mcp__brightdata-server__scraping_browser_screenshot",
      "mcp__brightdata-server__scraping_browser_get_text",
      "mcp__brightdata-server__scraping_browser_get_html",
      "mcp__brightdata-server__scraping_browser_links",
      "mcp__brightdata-server__scraping_browser_wait_for",
      "mcp__brightdata-server__scraping_browser_scroll",
      "mcp__brightdata-server__scraping_browser_click",
      "mcp__brightdata-server__scraping_browser_type"
    ]
  }
}
```

## Estructura

```text
.claude/
├─ agents/            # Subagentes
├─ commands/          # Slash commands y guías
├─ memory/            # Contexto del proyecto e historial
│  ├─ iteration_history/
│  ├─ market_research/
│  ├─ personas/
│  ├─ design_tokens/
│  └─ project_context.json
├─ settings.local.json
variants/             # Ejemplos y nuevas variantes
reports/              # Validación, a11y, performance, resiliencia
```

## Agentes
- `design-orchestrator` — controlador autónomo; bootstrap de carpetas; lectura/escritura de memoria.
- `market-analyst` — research; `messaging_pivots.md` y anti-patterns.
- `persona-forge` — personas aware (tono, triggers de CTA, locale).
- `design-builder` — variantes A/B/C, `design_tokens/tokens.json`, `design_tokens/mapping.json`, `reports/integration.md`.
- `visual-validator` — Playwright MCP; fallback Bright Data + Fetch; `reports/validation.md`.
- `accessibility-guardian` — auditoría WCAG.
- `performance-optimizer` — métricas core de performance.
- `resilience-sentinel` — self-healing; `reports/resilience.md`.

## Criterios de Salida
- Uniqueness ≥ 75 (auto-iterar si está por debajo)
- Por variante: 2–3 headlines/subheads + 3 CTAs (con micro-interacciones)
- Cumplimiento de Locale (por defecto en-US; sin auto-traducción)
- Reportes: visual diffs, a11y, performance, resiliencia

## Troubleshooting
- Falta Playwright MCP → usa fallback o registra MCP.
- Locale incorrecto → actualiza `/.claude/memory/project_context.json`.
- CTAs < 3/variante → el orquestador reitera `design-builder`.
- Permisos → asegúrate del allowlist.

## Seguridad
- No hardcodear API keys en el repo. Usa entorno local y permisos de Claude Code.

## Licencia
- Licencia MIT (ver `LICENSE`).
