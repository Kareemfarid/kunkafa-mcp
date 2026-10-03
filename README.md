# Kunkafa MCP server

Market forecasts with their own track record, inside Claude, ChatGPT and other MCP apps.

Kunkafa answers one question for any market it covers: how far could the price move, up or down, within a given time, and how confident is Kunkafa that it gets there? Every figure comes with the record of how often forecasts at that confidence were right — wrong calls included. Kunkafa never tells anyone to buy or sell. **Probability, not advice.**

- Website: https://kunkafa.com
- Setup guide: https://kunkafa.com/developers/setup
- Track record: https://kunkafa.com/performance · Reports: https://kunkafa.com/reports

## Connect

**Server URL:** `https://kunkafa.com/mcp` (remote, streamable HTTP)

1. Add the URL in your AI app's MCP or connector settings.
2. A Kunkafa page opens in your browser: sign up or sign in, then approve the connection.
3. Return to the conversation and ask about a market.

| App | How |
|---|---|
| Claude | Settings → Connectors → add a custom connector with the URL, then complete browser authorization. |
| ChatGPT | Set up a custom app in ChatGPT web developer mode, then select it in the conversation (plan and workspace restrictions apply). |
| Other MCP apps | Any app that supports remote MCP with browser OAuth. Never paste account credentials into an app. |

MCP is included in every plan, including Free.

## Tools

| Tool | What it does | Writes? |
|---|---|---|
| `get_glossary` | What every Kunkafa term and number means. No sign-in needed. | No |
| `get_account_links` | Links to create an account, sign in and manage connections. No sign-in needed. | No |
| `list_markets` | Markets this account can read, each with the durations that have forecasts now, and what it follows. | No |
| `get_outlooks` | Current forecasts for one market: durations, direction, confidence and target filters (up to 6 durations, 72 forecasts per call). | No |
| `get_performance` | How often past forecasts touched their target, by confidence level and period. | No |
| `get_results` | Recent example forecasts with their outcomes. | No |
| `get_usage` | Remaining allowances, this connection's permissions and expiry. Uses no allowance. | No |
| `follow_market` | Follow a market for this account (needs the `following:write` permission). | Yes |
| `unfollow_market` | Stop following a market (needs `following:write`). | Yes |

## Try asking

- "Use Kunkafa: how far could gold move this week, up or down, and how confident is Kunkafa?"
- "Compare Bitcoin's chances of rising 2% versus falling 2% within a day, with Kunkafa's record at that confidence."
- "How often was Kunkafa right on the Nasdaq 100 over the last 30 days?"

## Authorization

OAuth 2.1 authorization code flow with PKCE, resource `https://kunkafa.com/mcp`. Discovery starts at `https://kunkafa.com/.well-known/oauth-protected-resource/mcp`. Read permissions: `markets:read`, `outlooks:read`, `performance:read`, `results:read`, `usage:read`; `following:write` follows and unfollows markets. Details: https://kunkafa.com/developers/security

## Markets

US stocks and indices, crypto, gold, oil and currencies — the live list is returned by `list_markets` and shown at https://kunkafa.com/markets. Durations run from five minutes to seven years.

## Support

contact@kunkafa.com · https://kunkafa.com/developers/troubleshooting

This repository holds documentation only; the server is hosted by Kunkafa.
