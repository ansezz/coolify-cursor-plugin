---
name: coolify-deploy
description: Use when the user asks to deploy, restart, stop, or otherwise change Coolify app/service lifecycle via MCP. Require deploy-capable token and explicit confirmation before destructive actions.
---

# Coolify deploy / lifecycle

## Before acting

1. Confirm the target (project, application/service, environment) from inspect tools.
2. Confirm the active MCP token has `deploy` (or equivalent) permission for that team.
3. For production or irreversible actions, get an explicit go-ahead from the user in chat.

## Rules

- Prefer the smallest lifecycle action that matches the ask.
- Never invent deploy parameters; read current resource state first.
- After a change, re-check status/deployment summary and report outcome briefly.
- If MCP returns 403, the team MCP may be disabled or the token lacks permission — report that, do not brute-force.
