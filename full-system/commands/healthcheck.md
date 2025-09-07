# /healthcheck (Env & MCP readiness)

Run to verify environment readiness. The orchestrator can also trigger these checks autonomously on first run.

## Checks (non-destructive)
- Node & NPX present: `node -v`, `npx -v`
- Playwright MCP availability: `npx -y @playwright/mcp@1 --help` (won't start a long-running server)
  - Prefer pinning major (or exact) versions for reproducibility.
  - If the package is a devDependency, use a project-local script instead of npx (e.g., `pnpm mcp --help`).
- Claude MCP registry (optional): `claude mcp list`
  - Prereq: Claude CLI installed and configured (`claude --version` should succeed).
  - If not installed, skip this step and surface a hint to installation docs.
- Permissions sanity: confirm allow-rules in `.claude/settings.local.json`
  - Clarify path (workspace-local vs user global home). Example (workspace-local):
    - `.claude/settings.local.json` exists
    - contains explicit allow entries for the MCPs used in this repo

## Expected Output
- Versions for node/npx
- Playwright MCP help output
- List of MCP servers (if Claude CLI installed)
- Any missing piece with a one-line fix suggestion

## Notes
- Visual validation step will request permission to start Playwright MCP if not running.
- Memory service is optional but recommended for long-lived context.
