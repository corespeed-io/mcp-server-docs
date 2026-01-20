# Notion MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@makenotion/notion-mcp-server": {
      "url": "https://mcp.notion.com/mcp"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=notion&config=eyJ1cmwiOiJodHRwczovL21jcC5ub3Rpb24uY29tL21jcCJ9)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=notion&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.notion.com%2Fmcp%22%7D) |

Official Notion MCP Server implementation that enables AI agents to interact with the Notion API through the Model Context Protocol (MCP).

## Overview

Notion MCP is a hosted server implementing the Model Context Protocol (MCP), an open standard enabling AI assistants to securely interact with Notion workspaces. It provides secure access to your Notion workspace and is designed for tools like ChatGPT, Cursor, and Claude.

> **Note:** Notion is prioritizing and only providing active support for Notion MCP (remote). As a result, they may sunset the local MCP server repository in the future.

## Key Features

- **Easy setup** - Connect through simple OAuth, with one-click installation for supported AI tools
- **Full workspace access** - AI tools can read and write to your Notion pages
- **Optimized for AI** - Built specifically for AI agents with efficient data formatting

## Use Cases

- **Documentation generation** - Creating PRDs, tech specs, and architecture documents
- **Content search** - AI tools can query across Notion and connected workspace data
- **Task management** - Auto-generating code snippets and updating project statuses
- **Report creation** - Producing release notes and performance summaries
- **Campaign planning** - Generating briefs and tracking progress

## Installation

### Option 1: Notion MCP Remote (Recommended)

The easiest way to connect is via Notion's hosted MCP server.

#### Via Notion App

1. Open Settings in Notion
2. Navigate to Connections → Notion MCP
3. Select your AI tool
4. Complete the OAuth authentication flow

#### Manual Configuration

**Streamable HTTP (Recommended)**

```json
{
  "mcpServers": {
    "@makenotion/notion-mcp-server": {
      "url": "https://mcp.notion.com/mcp"
    }
  }
}
```

**SSE (Server-Sent Events)**

URL: `https://mcp.notion.com/sse`

**STDIO (Local Server using mcp-remote)**

```json
{
  "mcpServers": {
    "notionMCP": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.notion.com/mcp"]
    }
  }
}
```

### Option 2: Self-Hosted (Open Source)

For teams requiring full control over their infrastructure, the open-source implementation is available.

#### Step 1: Create Notion Integration

1. Go to [notion.so/profile/integrations](https://www.notion.so/profile/integrations)
2. Create a new internal integration
3. Copy the API token (starts with `ntn_`)
4. Optionally configure read-only capabilities

#### Step 2: Connect Content

Grant the integration access to relevant pages and databases through:
- The integration's Access tab, or
- Individual page connections menu

#### Step 3: Configure MCP Client

**npm (Recommended)**

```json
{
  "mcpServers": {
    "notionApi": {
      "command": "npx",
      "args": ["-y", "@notionhq/notion-mcp-server"],
      "env": {
        "NOTION_TOKEN": "ntn_****"
      }
    }
  }
}
```

**Docker**

```json
{
  "mcpServers": {
    "notionApi": {
      "command": "docker",
      "args": ["run", "--rm", "-i", "-e", "NOTION_TOKEN", "mcp/notion"],
      "env": {
        "NOTION_TOKEN": "ntn_****"
      }
    }
  }
}
```

## Transport Options

### STDIO (Default)

Standard input/output communication for most MCP clients.

### Streamable HTTP

Web-based alternative running on configurable ports with bearer token authentication. Supports three authentication methods:
- Auto-generated tokens (development)
- Command-line specified tokens
- Environment variables

## Breaking Changes in v2.0.0

Version 2.0.0 migrates to Notion API 2025-09-03, introducing data sources as the primary abstraction for databases.

### Removed Tools (4)
- `post-database-query`
- `retrieve-a-database`
- `update-a-database`
- `create-a-database`

### New Tools (6)
- `query-data-source`
- `retrieve-a-data-source`
- `update-a-data-source`
- `create-a-data-source`
- `list-data-source-templates`
- `move-page`

### Parameter Changes
- `database_id` → `data_source_id`

## Usage Examples

Once connected, you can instruct the AI to interact with Notion naturally:

- "Comment 'Hello MCP' on page 'Getting started'"
- "Add a page titled 'Notion MCP' to page 'Development'"
- "Find all tasks assigned to me in the Project Tracker database"
- Reference content directly by page ID

## Development

For the self-hosted version:

```bash
# Build and test
npm run build && npm test

# Run in development mode
npm run dev

# Publish
npm run publish
```

## Resources

- [Official GitHub Repository](https://github.com/makenotion/notion-mcp-server)
- [Notion MCP Documentation](https://developers.notion.com/docs/mcp)
- [Getting Started Guide](https://developers.notion.com/docs/get-started-with-mcp)
- [Self-Hosting Guide](https://developers.notion.com/docs/hosting-open-source-mcp)
- [Notion Help Center - MCP](https://www.notion.com/help/notion-mcp)

## License

See the [GitHub repository](https://github.com/makenotion/notion-mcp-server) for license information.
