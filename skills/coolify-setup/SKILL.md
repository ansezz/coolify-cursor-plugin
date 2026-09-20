---
name: coolify-setup
description: Use when connecting Coolify MCP for the first time — enable instance/team MCP, create a team token, set COOLIFY_BASE_URL and COOLIFY_API_TOKEN, and verify with get_current_team.
---

# Coolify MCP setup

## Steps

1. Confirm Coolify HTTPS base URL (no trailing slash).
2. Enable **instance** MCP (Settings → Configuration → Advanced → API and MCP).
3. Enable **team** MCP for the team that will own the token.
4. Create an API token (Keys & Tokens) while that team is active. Start with `read` only.
5. Set plugin variables or remote MCP:
   - URL: `{COOLIFY_BASE_URL}/mcp`
   - Header: `Authorization: Bearer {token}`
6. Verify: call `get_current_team` or `get_infrastructure_overview`.

## Multi-team

One token = one team. For staging and production, install two MCP servers with different tokens.

## Do not

- Commit tokens
- Paste secrets into chat when a secret field exists
- Enable `deploy` until the user needs lifecycle tools
