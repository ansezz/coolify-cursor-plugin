# Coolify MCP — Cursor Plugin

**Publisher:** [XCO Agency](https://xco.agency) (Shopify Plus Partner)

Cursor marketplace plugin for **Coolify's built-in** [Model Context Protocol](https://coolify.io/docs/mcp/setup) server. It does **not** reimplement Coolify APIs.

- MCP lives on your instance: `{COOLIFY_BASE_URL}/mcp`
- Transport: **Streamable HTTP**
- Auth: `Authorization: Bearer <team API token>`
- Docs: [Set up MCP](https://coolify.io/docs/mcp/setup) · [How MCP works](https://coolify.io/docs/mcp/how-mcp-works) · [Cursor client](https://coolify.io/docs/mcp/clients/cursor)

## What you get

- `mcp.json` — remote MCP URL + Bearer header via plugin variables
- Skills: setup, inspect, deploy
- `INSTALL-GROKBOT.md` — AddMcpServer / multi-team notes

Each installer uses **their own** Coolify instance and team token. No shared infrastructure.

## Requirements

- A Coolify Cloud or self-hosted instance with a public HTTPS URL
- Instance MCP enabled (Settings → Configuration → Advanced → API and MCP)
- Team MCP enabled for the team that owns the token
- API token with at least `read` (add `deploy` only if you need lifecycle tools)

## Install

### Cursor Marketplace (after listing)

Install **coolify**, then set plugin variables:

| Variable | Required | Notes |
| --- | --- | --- |
| `COOLIFY_BASE_URL` | yes | Origin only, no trailing slash (e.g. `https://app.coolify.io`) |
| `COOLIFY_API_TOKEN` | yes | Team-scoped token from Keys & Tokens |

### Manual MCP

```json
{
  "mcpServers": {
    "coolify": {
      "url": "${COOLIFY_BASE_URL}/mcp",
      "headers": {
        "Authorization": "Bearer ${COOLIFY_API_TOKEN}"
      }
    }
  }
}
```

Or paste the absolute URL and Bearer header in Cursor → Settings → Tools & MCP → New remote MCP server.

### Multiple teams

Create one token per Coolify team (e.g. staging vs production). Install two MCP entries with different names and tokens. See [INSTALL-GROKBOT.md](./INSTALL-GROKBOT.md).

## Verify

Ask the assistant to call `get_current_team` or `get_infrastructure_overview`. The response should match the team bound to your token.

## Security

- Prefer least privilege (`read` unless you need `deploy`)
- Never commit tokens; rotate if they leak
- MCP does not return full env values or full deployment logs (see Coolify docs)
- Revoking the API token immediately cuts off MCP access for that client

## License

MIT — see [LICENSE](./LICENSE). Coolify itself remains under its own license.

## About XCO Agency

[XCO Agency](https://xco.agency) — Shopify Plus Partner. Built and maintained for the Cursor / agent ecosystem.

> Repo note: published from `ansezz/coolify-cursor-plugin` until transferred under `XCO-Agency` (org create needs admin).
