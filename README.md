# Profullstack plugins for Claude and ChatGPT

Each plugin is a remote MCP server with OAuth 2.1 sign-in, so the same URL
works in Claude Code, claude.ai, the Claude apps and ChatGPT.

| Plugin | MCP server | What it does |
| --- | --- | --- |
| **c0mpute** | `https://c0mpute.com/api/mcp` | Publish a website on the c0mpute network (three self-healing copies on everyday computers, free through the shared cloud node), ask open models, make promo videos. See [cloud.killer.pit.world](https://cloud.killer.pit.world/). |
| **threatcrush** | `https://threatcrush.com/api/mcp?login` (connectors) / `/api/mcp` (Claude Code) | Security findings and triage, incidents, IP/domain/file-hash reputation, fleet, webhooks. |

## Claude Code

```
/plugin marketplace add profullstack/claude-plugins
/plugin install c0mpute@profullstack
/plugin install threatcrush@profullstack
```

The first tool call opens your browser to sign in.

## claude.ai and the Claude apps

Settings, Connectors, **Add custom connector**, paste the MCP server URL above.

## ChatGPT

Settings, Apps & Connectors, Advanced settings, turn on **Developer mode**,
then **Create**: paste the MCP server URL, authentication **OAuth**.

## License

MIT
