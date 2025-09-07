# Iterate Premium (Anti-Generic)

Use this command file to guide the orchestrator through a full iteration.

## Inputs (fill before running)
- Project name: [required]
- Industry / domain: [required]
- Audience & geography: [required]
- Primary goal (e.g., signup, trial, conversion): [required]
- Constraints (brand colors, typography, tone): [optional]
- Locale: [default = en-US] (Do NOT translate copy unless explicitly requested)
- Copy/CTA policy: e.g., replace competitor copy, propose 2–3 alt headlines & 3 CTA variants per variant
## Steps
0) Locale & Copy Policy
1. Locale & Copy Policy
   - Respect `Locale` (default en-US). Do NOT translate unless requested.
   - Replace competitor copy; generate new messaging: 2–3 alternative headlines/subheads, and 3 CTA variants per page variant.
   - Persist policy and chosen language in `.claude/memory/project_context.json`.
2. Market Research → `market-analyst`
   - Write to `.claude/memory/market_research/<project>.json`
   - Additionally output `differentiation_opportunities.md`, `anti_pattern_blacklist.yaml`, and `messaging_pivots.md` (value props, tone, CTA patterns to avoid).
3. Personas → `persona-forge`
   - Output to `.claude/memory/personas/<project>/`
   - Each persona includes tone of voice, objection handling, and CTA triggers.
4. Design Variants → `design-builder`
   - Output to `variants/<project>/{A,B,C}/`
   - Emit `design_tokens/tokens.json`
   - Produce `decisions.md` (visual + messaging rationale) and propose per-variant: 2–3 headlines/subheads and 3 CTA variants with micro-interactions.
   - Enforce locale; do not auto-translate.
5. Validation → `visual-validator`
   - Playwright MCP visual/interaction report
   - Verify CTA affordances and that the UI language matches `Locale`.
6. Accessibility → `accessibility-guardian`
   - Report to `reports/accessibility.md`
7. Performance → `performance-optimizer`
   - Report to `reports/perf.md`
8. Self-Healing Resilience Check
   - Ensure skeleton/loading states, prefers-reduced-motion fallbacks, network/asset failure fallbacks, and SSR mismatch guards are present.
   - Document in `reports/resilience.md`.
9. Snapshot iteration → `.claude/memory/iteration_history/<timestamp>.json`
- Uniqueness score ≥ 75
- Accessibility: No critical issues (AA+)
Perf targets: LCP < 2.5s, CLS < 0.1, INP < 200ms
- Messaging differentiation: new copy vs competitors with clear value-prop changes.
- CTA experimentation: ≥ 3 CTA variants per design variant with interaction specs.
- Locale respected: final outputs match requested language; no unintended translation.
- Resilience: skeletons, reduced-motion support, and graceful fallbacks verified.
