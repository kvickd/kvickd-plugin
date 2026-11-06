# Kvickd plugin

Swedish bookkeeping for small companies, with your AI.

[Kvickd](https://www.kvickd.com) is a hosted bookkeeping service for small Swedish companies: limited companies (aktiebolag), sole traders (enskild firma) and partnerships (handelsbolag, kommanditbolag). This repository connects AI agents to the Kvickd MCP server so you can book vouchers, handle invoices, VAT, payroll, year-end closing and tax returns (INK2, NE-bilaga, INK4) through conversation.

It contains an MCP server configuration, plugin manifests for Claude Code, Codex, Cursor and the [`plugins`](https://www.npmjs.com/package/plugins) CLI, and a skill with bookkeeping rules for the agent.

MCP server URL:

```
https://api.kvickd.com/mcp
```

Sign-in happens with OAuth in your browser the first time the agent connects. No API key is needed.

## Installation

### Plugin (Claude Code, Codex, Cursor and more)

```bash
npx plugins add kvickd/kvickd-plugin
```

### Skill only

```bash
npx skills add kvickd/kvickd-plugin
```

### Manual connection

Add the server URL in your client:

- **Claude** (claude.ai and Claude Desktop): Kvickd is in [Claude's connector directory](https://claude.ai/directory/kvickd). Open it, click Connect and sign in. In Claude Code:

  ```bash
  claude mcp add --transport http kvickd https://api.kvickd.com/mcp
  ```

- **ChatGPT**: add Kvickd as a custom plugin. On chatgpt.com, go to Plugins, Add, Create custom MCP server, and paste the URL. Creating a custom plugin requires ChatGPT Go, Plus or Pro. Step by step: [www.kvickd.com/guider/koppla-chatgpt](https://www.kvickd.com/guider/koppla-chatgpt)

- **Codex**:

  ```bash
  codex mcp add kvickd --url https://api.kvickd.com/mcp
  ```

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

More details: [www.kvickd.com/mcp](https://www.kvickd.com/mcp)

## På svenska

Kvickd är bokföring för små svenska företag (aktiebolag, enskild firma, handelsbolag och kommanditbolag), med hjälp av din AI. Det här repot kopplar AI-agenter som Claude, ChatGPT, Codex och Cursor till Kvickds MCP-server. Installera med `npx plugins add kvickd/kvickd-plugin`, eller lägg till adressen `https://api.kvickd.com/mcp` som anpassad koppling i din klient. Du loggar in med ditt Kvickd-konto första gången. Mer information finns på [www.kvickd.com/mcp](https://www.kvickd.com/mcp).

## License

The files in this repository are released under the [MIT License](LICENSE).

Configuration only. Kvickd is a proprietary hosted service.
