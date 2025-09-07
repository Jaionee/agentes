# CLAUDE.md

Welcome to the Premium Anti-Generic UI/UX Design System! This file provides a step-by-step guide on how to use Claude Code (claude.ai/code) to generate premium, unique interfaces.

## What is the Premium Anti-Generic UI/UX Design System?

The Premium Anti-Generic UI/UX Design System is a complete system that uses specialized Claude Code agents to generate premium, unique interfaces. The project is **operational** with all agents implemented.

### Project Status

✅ **Multi-Agent System**: 7 agents are configured in `.claude/agents/`
✅ **Memory Persistence**: Project context is stored in `.claude/memory/project_context.json`
✅ **Reference Variants**: 3 complete HTML implementations are available in `/variants/`

### How Does it Work?

**Main Orchestrator**: `design-orchestrator` coordinates the entire workflow. To use it, simply type:
```
Create a premium, anti-generic [component type] for [industry/context]
```
This will activate the `design-orchestrator` and start the workflow.

**Specialized Subagents**:

* `market-analyst`: Conducts market research using web scraping (Bright Data MCP)
* `persona-forge`: Generates market-aware personas with CTA triggers
* `design-builder`: Creates framework-agnostic variants with unique tokens
* `visual-validator`: Performs real-time validation using Playwright MCP
* `accessibility-guardian`: Ensures WCAG compliance while maintaining uniqueness
* `performance-optimizer`: Optimizes production for LCP < 2.5s, CLS < 0.1

### Design Styles Implemented

We have implemented three design styles:

* **Brutalist** (`brutalist-hero.html`): Ultra-bold typography, geometric elements rotated, color schemes #ff2d55/#000000, skew transformations
* **Data-Viz** (`data-viz-hero.html`): Terminal aesthetics, animated gradients, monospace fonts, technical interface elements
* **Neural Network** (`neural-network-hero.html`): Animated nodes with pulse, neon green palette (#00ff88), dark backgrounds, connectivity effects

### Key Commands

**Visual Validation**:
```bash
npx @playwright/mcp@latest
```
**System Health Check**:
```bash
# Run from .claude/commands/healthcheck.md (if exists)
```

### Memory Structure

The memory structure is organized as follows:
```
.claude/memory/
├── project_context.json        # Central configuration (ID, market insights, tokens)
├── iteration_history/          # Iteration history
├── market_research/            # Competitive analysis  
├── design_tokens/              # Unique token systems
└── personas/                   # Specialized personas
```

### Anti-Generics Principles

To ensure uniqueness, we follow these principles:

* **Prohibited**: Bootstrap colors (#007bff), generic border-radius (4px, 8px), predictable layouts
* **Required**: Unique visual signatures, calculated micro-interactions, differentiated palettes
* **Metric**: Uniqueness scoring vs. competition in each iteration

### System Output

The system generates the following output:

* **Framework-Agnostic Code**: HTML/CSS vanilla + React/Vue/Svelte adaptions
* **Design Tokens**: `tokens.json` with unique system variables
* **Market Reports**: Competitive analysis and differentiation opportunities  
* **Performance Metrics**: LCP, CLS, FID within premium targets
* **Accessibility**: AAA compliance + automated visual testing

### Getting Started

The system is ready for immediate use. Simply type the activation command, and the `design-orchestrator` will take care of the rest.