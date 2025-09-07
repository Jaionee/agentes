# FAQ — Frequently Asked Questions

Welcome to the FAQ! Here you’ll find simple answers to common questions about the Anti-Generic UI/UX Agent System.

## Why is it called “anti-generic”?
Because generic templates don’t stand out. This system makes sure your designs are unique and use market-aware messaging.

## How do I change the language or locale?
Open the file `/.claude/memory/project_context.json`. The default is `en-US`, but you can set it to your preferred locale.

## What happens if there are less than 3 CTAs per design variant?
The system automatically tries again: the orchestrator will run the design-builder agent and revalidate until you have at least 3 CTAs per variant.

## How do I use this with React or Next.js?
After running the system, check `/reports/integration.md` and read `docs/INTEGRATIONS.md` for step-by-step integration instructions.

## Can I use this without Playwright MCP?
Yes! If Playwright MCP isn’t available, the system will use Bright Data + Fetch as a fallback. (Tip: Playwright MCP gives better visual checks if you can use it.)

## Where can I find my outputs?
- **Design Variants**: `/variants/`
- **Reports**: `/reports/`
- **Tokens & Snapshots**: `/.claude/memory/`

If you have more questions, check the documentation or ask in support.
