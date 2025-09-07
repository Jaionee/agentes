# Validation & QA

Welcome to the Validation & QA guide! This document will help you understand how to validate your UI/UX designs using the Anti-Generic UI/UX Agent System.

## Visual Validation (Primary)
- **Playwright MCP**: This is the primary tool for visual validation. Run the following command to start:
```bash
npx @playwright/mcp@latest
```
- **What It Does**: The system takes responsive screenshots (small, medium, large) and performs basic interaction checks.
- **Where to Find Results**: Check the outputs in `/reports/visual_diff/` and `/reports/validation.md`.

## Fallback Validation
- **Bright Data MCP + Fetch**: Used when Playwright MCP is unavailable.
- **What It Captures**: HTML, text, and screenshots.
- **What It Validates**:
  - Locale compliance (should be en-US).
  - At least 3 CTA variants per design variant with hover/focus effects.

## Acceptance Criteria
- **Uniqueness**: Score should be 75 or higher.
- **Locale**: Must match the setting in `.claude/memory/project_context.json`.
- **CTA Variants**: Each design variant must have 3 or more CTA variants.
- **Accessibility**: No critical contrast issues.

## Troubleshooting
- **If Validation Fails**: The orchestrator will automatically re-iterate the design-builder.
- **Check Permissions**: Ensure that permissions are correctly set in `/.claude/settings.local.json`.
