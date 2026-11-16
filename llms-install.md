# Installing the SpaceJobs.Now MCP server (for AI agents)

This is a hosted remote server: there is nothing to download, build or run, and no API key.

1. Add this entry to the client's MCP settings (for Cline: `cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "spacejobs-now": {
      "url": "https://spacejobs.now/api/mcp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

2. If the client cannot connect to remote (Streamable HTTP) servers, use the bridge instead:

```json
{
  "mcpServers": {
    "spacejobs-now": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://spacejobs.now/api/mcp"]
    }
  }
}
```

3. Check it works: call `list_space_employers` with no arguments; it returns the space employers with their open role counts.
