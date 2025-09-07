# Security

Welcome to the Security guide! This document will help you understand the security principles and practices for using the Anti-Generic UI/UX Agent System.

## Security Principles
- **No API Keys in Repo**: Never store API keys directly in the repository.
- **Least Privilege**: Use Claude Code permissions to grant only the necessary access.
- **Transparent Validation**: Validation artifacts are easy to audit and review.

## Permissions
- **Recommended Allowlist**: Use the `/.claude/settings.local.json` file to specify which tools and servers are allowed.
- **External Tools**: MCP servers and other tools should run locally using `npx` or be registered with Claude Code.

## Data Flow
- **Inputs**: Include prompts and competitor URLs, but do not copy content.
- **Outputs**: The system generates variants, tokens, reports, and snapshots.
- **Optional Memory MCP**: Use a local server for semantic recall if needed.

## Compliance
- **No Vendor Keys**: This repository does not include any vendor keys.
- **Follow Security Policies**: Adhere to your organization’s security policies, especially when enabling scraping or validation MCPs.
