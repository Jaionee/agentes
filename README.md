# Anti-Generic UI/UX Agent System (Product)

Premium, market-aware UI/UX generation with autonomous Claude Code subagents. Framework-agnostic, resilient by design, and ready-to-run with natural language or a short Slash Command.

- Primary entrypoints: `design-orchestrator` agent, `/anti-iterate` command

## Highlights

- Multi-agent orchestration (market research → personas → design → validation → a11y → perf → resilience → snapshot)
- Framework-agnostic outputs (vanilla HTML/CSS first; React/Vue/Svelte options)
- Market-aware copy and CTA iteration (original; do not copy competitors)
- Locale control (default en-US; no auto-translate unless requested)
- Self-healing UI/UX via `resilience-sentinel` (skeletons, reduced-motion, fallbacks, SSR guards)
  - Visual validation with Playwright MCP; Bright Data + Fetch fallback
  - Project memory under `/.claude/memory/` and optional MCP Memory Service

## Installation

### For Project-Specific Use

```bash
mkdir -p .claude/agents .claude/commands
cp <path-to-repo>/full-system/agents/*.md .claude/agents/
cp <path-to-repo>/.claude/commands/*.md .claude/commands/
```

### For Global Use (All Projects)

```bash
mkdir -p ~/.claude/agents ~/.claude/commands
cp <path-to-repo>/full-system/agents/*.md ~/.claude/agents/
cp <path-to-repo>/.claude/commands/*.md ~/.claude/commands/
```

### Usage

Once installed, Claude Code will automatically detect and use these agents and slash commands.

## Documentation

- Product Overview: `docs/PRODUCT_OVERVIEW.md`
- Quick Start: `docs/QUICK_START.md`
- Integrations: `docs/INTEGRATIONS.md`
- Validation & QA: `docs/VALIDATION.md`
- Security: `docs/SECURITY.md`
- Roadmap: `docs/ROADMAP.md`
- FAQ: `docs/FAQ.md`
- Support: `SUPPORT.md`
- Releasing: `docs/RELEASING.md`

### Translations

- Español: `README_es.md`

## Requirements

- Claude Code (Desktop/CLI) with subagents enabled
- Node 18+ (tested with Node 23) and NPX
- Optional MCPs:
  - Playwright MCP for visual validation
  - Bright Data MCP + Fetch (fallback and web enrichment)
  - Memory MCP (persistent semantic memory)

## Quick Start

Option A (recommended, Natural Language):
1) Select the `design-orchestrator` agent.
2) Paste:
```text
Design anti-generic UI for "<ProjectName>" competing with <Competitor1>, <Competitor2>.
Industry: <Industry>. Audience/Geo: <Audience>. Primary goal: <Goal>. Constraints: <Constraints or none>.
Locale: en-US. Do not copy competitor content. Produce original, differentiated copy.
Run the full premium iteration: market-analyst → persona-forge → design-builder → visual-validator → accessibility-guardian → performance-optimizer → resilience-sentinel → snapshot.
Enforce copy/CTA policy: 2–3 headlines & subheads AND 3 CTA variants per design variant with micro-interaction specs.
Gate: If Uniqueness < 75 or Locale mismatch or CTAs < 3/variant, iterate and revalidate. Persist updates to .claude/memory/project_context.json.
```

Option B (Slash Command):
```text
/anti-iterate project:"<ProjectName>" industry:"<Industry>" audience:"<Audience/Geo>" goal:"<Goal>" locale:"en-US" competitors:"https://competitor1.com, https://competitor2.com"
```
See `/.claude/commands/anti-iterate.md`.

Healthcheck (optional): see `/.claude/commands/healthcheck.md`.

## MCP Setup (optional)

- Playwright MCP (ad-hoc):
```bash
npx @playwright/mcp@latest
```
- Playwright MCP (register once):
```bash
claude mcp add playwright-mcp spawn -- npx @playwright/mcp@latest
claude mcp list
```
- Memory MCP (example with uv):
```bash
claude mcp add memory-service spawn -- /opt/homebrew/bin/uv --directory /Users/<you>/path/to/mcp-memory-service run memory
```

## Permissions (recommended) — `/.claude/settings.local.json`
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

## Directory Layout

```text
.claude/
├─ agents/            # Subagents
├─ commands/          # Slash commands & guides
├─ memory/            # Project context & iteration history
│  ├─ iteration_history/
│  ├─ market_research/
│  ├─ personas/
│  ├─ design_tokens/
│  └─ project_context.json
├─ settings.local.json
variants/             # Generated examples and new variants
reports/              # Validation, a11y, perf, resilience
```

## Agents
- `design-orchestrator` — autonomous controller; bootstraps dirs; reads/writes memory.
- `market-analyst` — research; `messaging_pivots.md` and anti-patterns.
- `persona-forge` — market-aware personas (tone, CTA triggers, locale).
- `design-builder` — variants A/B/C, `design_tokens/tokens.json`, `design_tokens/mapping.json`, `reports/integration.md`.
- `visual-validator` — Playwright MCP; fallback with Bright Data + Fetch; `reports/validation.md`.
- `accessibility-guardian` — WCAG checks.
- `performance-optimizer` — core performance metrics targets.
- `resilience-sentinel` — self-healing checks; `reports/resilience.md`.

## Output & Criteria
- Uniqueness target ≥ 75 (auto-iterate if below)
- Per-variant messaging: 2–3 headlines/subheads + 3 CTA variants (with micro-interactions)
- Locale compliance (default en-US; no auto-translate)
- Reports: visual diffs, a11y, perf, resilience

## Troubleshooting
- Playwright MCP missing → use fallback or register MCP.
- Locale mismatch → update `/.claude/memory/project_context.json`.
- CTAs < 3/variant → orchestrator will reiterate design-builder.
- Permissions → Ensure allowlist above.

## Security
- Never hardcode API keys in the repo. Use local environment and Claude Code permissions.

## License
- MIT License (see `LICENSE`).
