# Wix MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@wix/wix-mcp": {
      "url": "https://mcp.wix.com/sse"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=wix&config=eyJ1cmwiOiJodHRwczovL21jcC53aXguY29tL3NzZSJ9)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=wix&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.wix.com%2Fsse%22%7D) |

The Wix MCP (Model Context Protocol) server enables AI clients to integrate with Wix tools and services. It allows developers to search Wix documentation, write platform code, and make API calls to Wix sites without manually consulting documentation.

## Prerequisites

- Node.js version 19.9.0 or higher required

## Configuration

### Remote MCP Configuration

Add the following JSON to your MCP server settings:

```json
{
  "mcpServers": {
    "wix-mcp-remote": {
      "url": "https://mcp.wix.com/mcp"
    }
  }
}
```

Supported `type` values are `"sse"` and `"http"`. The type you select depends on your agent.

### Supported Clients

- Claude Desktop
- Claude Web
- Cursor
- Windsurf
- VS Code
- Gemini CLI

### Local/Alternative Tools

Platforms without remote MCP support (such as n8n or A2A) can authenticate using API keys combined with your Wix account ID.

## Available Tools

The server provides the following built-in tools:

| Tool | Description |
|------|-------------|
| **SearchWixWDSDocumentation** | Query Wix Design System documentation |
| **SearchWixRESTDocumentation** | Query Wix REST API documentation |
| **SearchWixSDKDocumentation** | Query Wix SDK documentation |
| **SearchBuildAppsDocumentation** | Query Wix Build Apps documentation |
| **SearchWixHeadlessDocumentation** | Query Wix Headless documentation |
| **WixBusinessFlowsDocumentation** | Access multi-step workflow instructions |
| **ReadFullDocsArticle** | Retrieve complete article content by URL |
| **ReadFullDocsMethodSchema** | Get API method request/response schemas |
| **ListWixSites** | Query account sites |
| **CallWixSiteAPI** | Execute site-level operations |
| **ManageWixSite** | Perform account-level actions like site creation |
| **SupportAndFeedback** | Collect user feedback for Wix |

## Troubleshooting

If experiencing errors:

1. Review IDE logs
2. Verify latest Node.js version is default
3. Confirm `-y` flag and correct npm registry in npx configuration
4. Use full Node.js path
5. Restart the IDE
6. Test directly: `npx -y @wix/mcp-remote https://mcp.wix.com/sse`
7. Delete `~/.mcp-auth` (Mac) or `C:\Users\<username>\.mcp-auth` (Windows) if connection drops after inactivity or account switch
8. Consult the MCP debugging guide for additional assistance

## Resources

- [GitHub Repository](https://github.com/wix/wix-mcp)
- [Official Documentation](https://dev.wix.com/docs/sdk/articles/use-the-wix-mcp/about-the-wix-mcp)
- [Wix Site MCP Documentation](https://dev.wix.com/docs/develop-websites/articles/get-started/about-the-wix-site-mcp)
- [npm Package (@wix/mcp)](https://www.npmjs.com/package/@wix/mcp)
- [Wix Studio MCP Server](https://www.wix.com/studio/developers/mcp-server)
