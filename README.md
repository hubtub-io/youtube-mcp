<p align="center">
  <a href="https://hubtub.io/mcp"><img src="https://hubtub.io/hubtub-icon-512.png" width="72" height="72" alt="HubTub"></a>
</p>

<h1 align="center">YouTube MCP server: HubTub Pulse</h1>

<p align="center">
  Connect your YouTube channels to Claude and other AI assistants.<br>
  Ask about revenue, views, retention and thumbnail clicks in plain words.
</p>

<p align="center">
  <a href="https://claude.ai/directory/hubtub"><img src="assets/add-to-claude.svg" height="44" alt="Add to Claude"></a>
</p>

<p align="center">
  <a href="https://hubtub.io/mcp">Website</a> ·
  <a href="https://hubtub.io/pulse/ai">Documentation</a> ·
  <a href="https://hubtub.io/privacy">Privacy Policy</a>
</p>

```
https://app.hubtub.io/api/mcp
```

HubTub Pulse is a free analytics app for YouTube creators and agencies. Its MCP server lets the AI assistant you use read your channels’ YouTube Analytics reports when you ask: what grew, what dropped, which videos earn the most and where viewers come from.

- **Your private analytics.** Revenue, watch time, audience retention and thumbnail clicks from YouTube Analytics, not only what anyone can see.
- **Nothing to set up.** No API keys, no Google Cloud project, nothing to install. Sign in with Google and allow access.
- **Read-only.** It can’t upload, edit or delete anything, and never changes your YouTube or HubTub settings.
- **YouTube’s own figures.** Every number is exactly what YouTube reports, channel by channel. HubTub adds no estimates or scores.
- **All your channels.** Every channel you added to Pulse, and channels shared with you whose owners allowed AI assistants.
- **Free** for every creator, with no limit on channels.

## Set up

You need a free HubTub account with your channel in [Pulse](https://app.hubtub.io/dashboard/pulse).

### Claude

1. Open [HubTub Pulse in Claude’s connector directory](https://claude.ai/directory/hubtub) and click **Connect**.
2. Sign in to HubTub with Google, check what Claude will be able to read and click **Allow access**.
3. Ask about your channel in any chat: Claude reads Pulse when it needs your numbers.

Or in Claude: **Settings → Connectors → Add custom connector**, with the address `https://app.hubtub.io/api/mcp`.

### Other apps

Works in apps that support remote MCP servers with sign-in (OAuth).

1. In your app’s settings, add a remote MCP server (often called a connector).
2. Paste `https://app.hubtub.io/api/mcp`. No API key is needed.
3. Sign in to HubTub when the app asks, and allow access.

## Questions to start with

- How much did my channel earn in the last 28 days, compared with the 28 days before?
- Why did my views drop last week? Look at the last 90 days by day.
- What do my best videos of the last 28 days have in common?
- Where do viewers stop watching my top video?
- Which videos had many impressions but few clicks?
- Which countries watch my channel the most?

[More questions by topic](https://hubtub.io/mcp#prompts)

## Tools

Four tools, all read-only. Your assistant picks the one it needs for your question.

| Tool | What it reads |
| --- | --- |
| `list_channels` | Your channels at a glance: subscribers, videos and total views, with the last 7 or 28 days of YouTube Analytics beside the period before. |
| `get_channel_report` | One channel in detail: 90 days by day, 12 months by month, audience, traffic sources and the 50 most-viewed videos with revenue, watch time and engagement. |
| `get_video_retention` | Audience retention of your top videos: where viewers keep watching and where they leave. |
| `get_thumbnail_impressions` | Thumbnail impressions and YouTube’s click-through rate by video and day, for up to 30 days. |

It never calls YouTube while you chat: it reads the reports Pulse already keeps, refreshed every night.

## Privacy and security

- You approve each assistant on a HubTub page. It signs in with OAuth and never sees your Google password.
- Revenue only where the channel’s owner gave HubTub the revenue permission. Nothing else from your HubTub account, such as payouts or contracts.
- See and disconnect your assistants in Pulse → Connected AI; one not used for 90 days is disconnected by itself.
- Your assistant’s provider handles the reports it receives under its own terms: check its settings to see whether chats train its models.

## For developers

- Remote server, Streamable HTTP (stateless), JSON-RPC 2.0; tools only.
- OAuth 2.1: authorization code with PKCE (S256), dynamic client registration, refresh tokens.
- Protected resource metadata (RFC 9728): `https://app.hubtub.io/.well-known/oauth-protected-resource/api/mcp`.
- Listed in the [MCP Registry](https://registry.modelcontextprotocol.io) from [`server.json`](server.json).

## Questions

**Is there an official YouTube MCP server?**
HubTub Pulse isn’t made by YouTube. It’s an independent app that reads your channels’ YouTube Analytics through YouTube’s official API, with your permission, and lets the AI assistants you choose read the same reports.

**How is it different from other YouTube MCP servers on GitHub?**
Most of them read public data with an API key you create: video titles, view counts, transcripts. HubTub Pulse reads your private YouTube Analytics (revenue, watch time, retention, thumbnail clicks), runs on our servers and needs no keys.

**How do I disconnect it?**
In Pulse → Connected AI, or in your assistant’s connector settings. A disconnected assistant loses access at once.

## About

This repository holds HubTub Pulse’s MCP documentation and its registry listing. The server runs at app.hubtub.io; its code isn’t public. The full documentation is at [hubtub.io/pulse/ai](https://hubtub.io/pulse/ai).

Questions: [creators@hubtub.io](mailto:creators@hubtub.io). We answer within a working day.

HubTub Pulse is an independent app, not made or endorsed by YouTube or Google. Claude is a trademark of Anthropic.
