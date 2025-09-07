# Product Overview — Anti-Generic UI/UX Agent System

Welcome to the Anti-Generic UI/UX Agent System! This document provides an overview of how our system helps you create premium, unique user interfaces quickly and easily.

## Who is this for?
- **Product Teams**: Need rapid, premium UI/UX variants.
- **Growth, Marketing, and Design Ops**: Seek consistent experimentation.
- **CTOs/Design Leads**: Enforce resilience, accessibility, and performance gates.

## Key Differentiators
- **Anti-Generic by Design**: Original messaging and CTAs (never copy competitors).
- **Market-Aware Iteration Loop**: Research → Personas → Design → Validation.
- **Locale Control**: Default en-US; no auto-translate unless requested.
- **Self-Healing UI/UX**: Skeletons, reduced motion, fallbacks, SSR guards.
- **Visual Validation**: Via Playwright MCP with Bright Data + Fetch fallback.
- **Drop-In Integration Artifacts**: `design_tokens/mapping.json`, `reports/integration.md`.

## Architecture (High Level)
- **Orchestrator**: `/.claude/agents/design-orchestrator.md`.
- **Subagents**: Market-analyst, persona-forge, design-builder, visual-validator, accessibility-guardian, performance-optimizer, resilience-sentinel.
- **Memory**: `/.claude/memory/` (context, tokens, snapshots).
- **Commands**: `/.claude/commands/` (iterate, healthcheck, install MCPs).

## Core Deliverables
- **Variants A/B/C**: With unique copy and CTAs.
- **Tokens + Mapping**: For integration with popular stacks.
- **Validation Reports**: Visual diff, a11y, performance, resilience.
- **Iteration Snapshots**: `/.claude/memory/iteration_history/`.

## Success Criteria
- **Uniqueness ≥ 75**: Locale compliance; 3+ CTAs per variant; basic WCAG checks.
- **Integration Doc Produced**: Tokens mapped; visual checks pass at sm/md/lg.

## Product Checklist
- [x] Autonomous iteration (slash command or NL).
- [x] Validation + fallback.
- [x] Memory persistence.
- [x] Integration artifacts.
- [x] Setup & troubleshooting docs.
