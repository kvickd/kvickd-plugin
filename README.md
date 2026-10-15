# Kvickd plugin

Swedish bookkeeping for small companies, run by your AI.

[Kvickd](https://www.kvickd.com) is a hosted bookkeeping service for small Swedish limited companies (aktiebolag). This repository connects AI agents to the Kvickd MCP server so you can book vouchers, handle invoices, VAT, payroll and year-end closing through conversation.

It contains an MCP server configuration, plugin manifests for Claude Code, Cursor, Codex and the [`plugins`](https://www.npmjs.com/package/plugins) CLI, and a skill with bookkeeping rules for the agent.

MCP server URL:

```
https://api.kvickd.com/mcp
```

Sign-in happens with OAuth in your browser the first time the agent connects. No API key is needed.

## Installation

### Plugin (Claude Code, Cursor, Codex and more)

```bash
npx plugins add kvickd/kvickd-plugin
```

### Skill only

```bash
npx skills add kvickd/kvickd-plugin
```

### Manual connection

Add the server URL in your client:

- **Claude** (claude.ai and Claude Desktop): Settings → Connectors → Add custom connector, and paste the URL. In Claude Code:

  ```bash
  claude mcp add --transport http kvickd https://api.kvickd.com/mcp
  ```

- **ChatGPT**: Settings → Apps & Connectors, create a custom connector (developer mode) and paste the URL.

- **Cursor**: add this to `~/.cursor/mcp.json`:

  ```json
  {
    "mcpServers": {
      "kvickd": {
        "url": "https://api.kvickd.com/mcp"
      }
    }
  }
  ```

- **Codex**:

  ```bash
  codex mcp add kvickd --url https://api.kvickd.com/mcp
  ```

More details: [www.kvickd.com/mcp](https://www.kvickd.com/mcp)

## På svenska

Kvickd är bokföring för små svenska aktiebolag, skött av din AI. Det här repot kopplar AI-agenter som Claude, ChatGPT, Cursor och Codex till Kvickds MCP-server. Installera med `npx plugins add kvickd/kvickd-plugin`, eller lägg till adressen `https://api.kvickd.com/mcp` som anpassad koppling i din klient. Du loggar in med ditt Kvickd-konto första gången. Mer information finns på [www.kvickd.com/mcp](https://www.kvickd.com/mcp).

## License

The files in this repository are released under the [MIT License](LICENSE).

Configuration only. Kvickd is a proprietary hosted service.
