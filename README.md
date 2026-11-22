# Profullstack plugins for Claude and ChatGPT

Each plugin is a remote MCP server with OAuth 2.1 sign-in, so the same URL
works in Claude Code, claude.ai, the Claude apps and ChatGPT.

| Plugin | MCP server | What it does |
| --- | --- | --- |
| **c0mpute** | `https://c0mpute.com/api/mcp` | Publish a website on the c0mpute network (three self-healing copies on everyday computers, free through the shared cloud node), chat with open models on the network, make promo videos. See [c0mpute.com](https://c0mpute.com) and [cloud.killer.pit.world](https://cloud.killer.pit.world/). |
| **r4ck** | `https://r4ck.dev/api/mcp` | Search every VPS, cloud, bare metal, GPU and PaaS offer for sale by spec, price and place. No key needed to search. See [r4ck.dev](https://r4ck.dev). |
| **board-saas** | `https://board.saas.pit.world/mcp` | Hosted AI board meeting on a decision: five advisors give verdicts and debate, a chair writes the minutes. First meeting free, then $9. See [board.saas.pit.world](https://board.saas.pit.world). |
| **cheapestwayz** | `https://cheapestwayz.com/mcp` | Find the cheapest way to get something done: priced DIY, online and local methods ranked by cost, local quotes, referral links and earnings. Reading needs no account; OAuth sign-in (email link or CoinPay) for the rest. See [cheapestwayz.com](https://cheapestwayz.com). |
| **threatcrush** | `https://threatcrush.com/api/mcp?login` (connectors) / `/api/mcp` (Claude Code) | Security findings and triage, incidents, IP/domain/file-hash reputation, fleet, webhooks. |

## Claude Code

```
/plugin marketplace add profullstack/claude-plugins
/plugin install c0mpute@profullstack
/plugin install threatcrush@profullstack
/plugin install r4ck@profullstack
/plugin install board-saas@profullstack
/plugin install cheapestwayz@profullstack
/plugin install boardroom@profullstack
```

**boardroom** is not an MCP server: it is a set of agents and a
`/boardroom:meet` command that run the five advisors and the chair locally in
Claude Code ([profullstack/boardroom](https://github.com/profullstack/boardroom)).

The first tool call opens your browser to sign in (r4ck needs no sign-in to search).

## claude.ai and the Claude apps

Settings, Connectors, **Add custom connector**, paste the MCP server URL above.

## ChatGPT

Settings, Apps & Connectors, Advanced settings, turn on **Developer mode**,
then **Create**: paste the MCP server URL, authentication **OAuth**.

## License

MIT
