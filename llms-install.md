# Installing the LetsBot MCP server (for AI agents)

LetsBot is a hosted remote MCP server. There is nothing to clone, build or run.

## Cline (`cline_mcp_settings.json`)

```json
{
  "mcpServers": {
    "letsbot": {
      "type": "streamableHttp",
      "url": "https://letsbot.net/mcp"
    }
  }
}
```

On first use the client opens LetsBot's OAuth 2.1 sign-in page (dynamic client registration, PKCE). The user signs in to their LetsBot workspace and approves access.

## API key instead of OAuth

If the client cannot do OAuth, use a workspace API key as a Bearer token. The user gets it in the LetsBot panel → Developers → Authentication Data.

```json
{
  "mcpServers": {
    "letsbot": {
      "type": "streamableHttp",
      "url": "https://letsbot.net/mcp",
      "headers": { "Authorization": "Bearer YOUR_LETSBOT_API_KEY" }
    }
  }
}
```

## Check it works

`tools/list` answers without credentials. Every `tools/call` needs the sign-in or the key. Ask the agent to run `get_account_overview`: it is read-only and returns the workspace plan and connected channels.

Tools that send messages, delete data or start campaigns ask for `confirm=false` first. They return a preview, and nothing is sent until the user approves.
