# Quick Start

Welcome to the Quick Start guide! This document will help you get started with the Anti-Generic UI/UX Agent System quickly and easily.

## Prerequisites
- **Claude Code with Subagents**: Make sure you have Claude Code installed with subagents enabled.
- **Node 18+ and NPX**: Required for running commands.
- **Optional**: Playwright MCP, Bright Data MCP, Memory MCP for additional features.

## Option A — Natural Language (Recommended)
1) **Select the `design-orchestrator` agent**: This agent will coordinate the entire workflow.
2) **Paste the following command**:
```text
Design anti-generic UI for "<ProjectName>" competing with <Competitor1>, <Competitor2>.
Industry: <Industry>. Audience/Geo: <Audience>. Primary goal: <Goal>. Constraints: <Constraints or none>.
Locale: en-US. Do not copy competitor content. Produce original, differentiated copy.
Run the full premium iteration: market-analyst → persona-forge → design-builder → visual-validator → accessibility-guardian → performance-optimizer → resilience-sentinel → snapshot.
Enforce copy/CTA policy: 2–3 headlines & subheads AND 3 CTA variants per design variant with micro-interaction specs.
Gate: If Uniqueness < 75 or Locale mismatch or CTAs < 3/variant, iterate and revalidate. Persist updates to .claude/memory/project_context.json.
```

## Option B — Slash Command
Use this command to start the iteration process quickly:
```text
/anti-iterate project:"<ProjectName>" industry:"<Industry>" audience:"<Audience/Geo>" goal:"<Goal>" locale:"en-US" competitors:"https://competitor1.com, https://competitor2.com"
```

## Healthcheck
- **Run**: `/.claude/commands/healthcheck.md` to ensure everything is set up correctly.
- **Fallback Validation**: If Playwright MCP is unavailable, fallback validation is automatic (Bright Data + Fetch).

## Outputs
- **Variants**: Generated designs will be saved in `/variants/`.
- **Reports**: Validation and other reports will be found in `/reports/`.
- **Tokens/Mapping**: Design tokens and mappings are located in `/.claude/memory/design_tokens/` and `/reports/integration.md`.
- **Snapshots**: Iteration history is stored in `/.claude/memory/iteration_history/`.

For detailed setup instructions, see: `/.claude/SETUP_NATIVE_SUBAGENTS.md`.
