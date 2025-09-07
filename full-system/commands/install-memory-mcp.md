# Install MCP Memory Service (optional but recommended)

Persistent memory lets subagents recall context across sessions.

## 1) Install the service
Follow the repo instructions (example uses UV):
```bash
# clone the service somewhere on your machine
# git clone https://github.com/<org>/mcp-memory-service
# cd mcp-memory-service
# optional: create venv; ensure uv installed
```

## 2) Register with Claude Code
Replace paths with yours:
```bash
claude mcp add memory-service spawn -- /opt/homebrew/bin/uv --directory /Users/<you>/path/to/mcp-memory-service run memory
claude mcp list
```

You should see `memory-service` in the list.

## 3) Use in agents
Orchestrator and subagents will read/write project context and recall memories using the MCP server once available.

Notes:
- This is optional. The system still works with filesystem-based memory under `.claude/memory/`.
- For large teams, a shared memory service can centralize knowledge across repos.
