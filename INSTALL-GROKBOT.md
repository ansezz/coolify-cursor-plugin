# Install on Grok Bot / Cursor agents

Coolify MCP is **remote Streamable HTTP**. There is no local npm package to run.

Do not paste API tokens into chats when you can use a secret field or plugin variables.

## AddMcpServer (remote)

| Field | Value |
| --- | --- |
| name | `coolify` (or `coolify-staging` / `coolify-production` for multiple teams) |
| url | `https://YOUR-COOLIFY-DOMAIN/mcp` |
| headers | `Authorization`: `Bearer YOUR_TEAM_API_TOKEN` |

Example shape:

```json
{
  "url": "https://YOUR-COOLIFY-DOMAIN/mcp",
  "headers": {
    "Authorization": "Bearer YOUR_TEAM_API_TOKEN"
  }
}
```

## Multiple Coolify teams

API tokens are **team-scoped**. For staging and production (or any two teams), add **two** MCP servers with different names/labels and different tokens. Same base URL is fine if both teams live on one instance.

## Verify

Ask the agent to call `get_current_team` or `get_infrastructure_overview`. Confirm the team matches the token you installed.

## Permissions

- `read` — inspect resources
- `deploy` — only if the agent must trigger deployments / lifecycle tools
