# Ahrefs MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@ahrefs/ahrefs-mcp-server": {
      "url": "https://api.ahrefs.com/mcp/mcp",
      "headers": {
        "Authorization": "Bearer <AHREFS_API_KEY>"
      }
    }
  }
}
```

> **Note:** Replace `<AHREFS_API_KEY>` with your Ahrefs API v3 key. Get one from [Ahrefs API key management](https://docs.ahrefs.com/docs/api/reference/api-keys-creation-and-management).

A Model Context Protocol server to connect AI assistants to Ahrefs SEO tools and data.

## Resources

- [Remote MCP server documentation](https://docs.ahrefs.com/docs/mcp/reference/introduction)
- [API key management](https://docs.ahrefs.com/docs/api/reference/api-keys-creation-and-management)
