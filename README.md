# LetsBot MCP server — WhatsApp Business for Claude, ChatGPT, Cursor and any MCP client

LetsBot's remote MCP server connects AI assistants to a WhatsApp Business account on
[LetsBot](https://letsbot.net): read and answer customer conversations, send approved templates,
run campaigns and chatbots, manage contacts and get reports.

- **Server URL:** `https://letsbot.net/mcp` (Streamable HTTP)
- **Auth:** OAuth 2.1 with PKCE and dynamic client registration (Claude, ChatGPT), or a LetsBot API key as a Bearer token (Cursor, VS Code, Gemini CLI, Continue)
- **Server card:** https://letsbot.net/.well-known/mcp/server-card.json
- **Docs:** https://letsbot.net/en/whatsapp-mcp.html

## Requirements
- A LetsBot account with the **API + MCP** add-on (US$69.99/month, VAT included, on top of any plan; plans start at US$6.35/month), or an active 14-day free trial.
- A WhatsApp number connected to LetsBot for sending. An API key (LetsBot panel → Developers → Authentication Data) is issued once a channel is connected.
- Bulk campaigns also need the Bulk Messaging add-on.

## Connect

> **Recommended: OAuth** (Claude, ChatGPT and any client that supports it): you sign in with your LetsBot account and never handle a key. Use an API key only in developer tools, and keep it out of shared or committed config files.

**Claude** — Settings → Connectors → add LetsBot from the directory, or "Add custom connector":
```
URL: https://letsbot.net/mcp
Auth: OAuth 2.1 + PKCE (sign in with your LetsBot account)
```

**ChatGPT** — install the LetsBot app, or add a server with `https://letsbot.net/mcp` and sign in.

**Cursor** — `~/.cursor/mcp.json`:
```json
{
  "mcpServers": {
    "letsbot": {
      "url": "https://letsbot.net/mcp",
      "headers": { "Authorization": "Bearer YOUR_LB_API_KEY" }
    }
  }
}
```

**VS Code** — `.vscode/mcp.json`:
```json
{
  "servers": {
    "letsbot": {
      "type": "http",
      "url": "https://letsbot.net/mcp",
      "headers": { "Authorization": "Bearer YOUR_LB_API_KEY" }
    }
  }
}
```

**Gemini CLI**:
```
gemini mcp add --transport http --header "Authorization: Bearer YOUR_LB_API_KEY" letsbot https://letsbot.net/mcp
```

**Continue** — `config.yaml`:
```yaml
mcpServers:
  - name: letsbot
    type: streamable-http
    url: https://letsbot.net/mcp
    requestOptions:
      headers:
        Authorization: Bearer YOUR_LB_API_KEY
```

## What it can do
More than 80 tools in every workspace (up to 166 when optional areas such as CRM, deals, tasks,
tickets and bookings are on): messages and templates, live-chat inbox, contacts and labels,
campaigns, chatbot, store orders and abandoned carts, reports and an owner briefing.

## Safety
- Every send (messages, templates, campaigns) returns a preview first and runs only after an explicit `confirm: true`.
- OAuth access is scoped to the signed-in user's own LetsBot account and can be revoked at any time.
- Team roles, API keys, billing and channel disconnection stay read-only over MCP.

## Listings
- Official MCP Registry: `net.letsbot/mcp`
- Claude connectors directory: https://claude.ai/directory/connectors/3455d00e-518f-425f-9e0d-6a9eac2f54ef

## Support
support@letsbot.net · https://letsbot.net/en/contact-us.html · Privacy: https://letsbot.net/en/privacy.html
