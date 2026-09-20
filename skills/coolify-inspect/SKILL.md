---
name: coolify-inspect
description: Use when browsing Coolify infrastructure via MCP — servers, projects, applications, databases, services, deployments, or log summaries — in a read-only way.
---

# Coolify inspect (read-only)

## Habits

- Prefer overview tools first (`get_infrastructure_overview`, `get_current_team`), then drill down.
- Stay on the team bound to the active token; do not assume other teams are visible.
- Treat responses as structured `data` with optional pagination; env values and full logs are intentionally withheld.
- Summarize for the user in plain language; do not dump huge JSON unless asked.

## Safety

- Inspection only — no deploy, restart, stop, or delete from this skill.
- If a tool needs `deploy` permission, stop and confirm with the user before switching tokens or scopes.
