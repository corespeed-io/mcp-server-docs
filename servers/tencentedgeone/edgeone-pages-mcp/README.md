# EdgeOne Pages MCP

## Server Config

```json
{
  "mcpServers": {
    "@tencentedgeone/edgeone-pages-mcp": {
      "url": "https://mcp-on-edge.edgeone.site/mcp-server"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=edge-one-pages&config=eyJ1cmwiOiJodHRwczovL21jcC1vbi1lZGdlLmVkZ2VvbmUuc2l0ZS9tY3Atc2VydmVyIn0=)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=edge-one-pages&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp-on-edge.edgeone.site%2Fmcp-server%22%7D) |

An MCP service for deploying HTML content, folders, or full-stack projects to EdgeOne Pages and obtaining publicly accessible URLs.

[![GitHub](https://img.shields.io/badge/GitHub-TencentEdgeOne%2Fedgeone--pages--mcp-blue)](https://github.com/TencentEdgeOne/edgeone-pages-mcp)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

EdgeOne Pages MCP is a Model Context Protocol (MCP) service that enables rapid deployment of web applications to Tencent Cloud EdgeOne Pages. It allows AI models to securely interact with EdgeOne's edge serverless infrastructure to deploy and host web content.

## Requirements

- Node.js 18 or higher

## MCP Configuration

### stdio MCP Server (Recommended)

Full-featured MCP service supporting the `deploy_folder` tool for deploying full-stack projects.

**Tencent Cloud International (Default):**

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "timeout": 600,
      "command": "npx",
      "args": ["edgeone-pages-mcp-fullstack@latest"]
    }
  }
}
```

**Tencent Cloud China:**

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "timeout": 600,
      "command": "npx",
      "args": ["edgeone-pages-mcp-fullstack@latest", "--region", "china"]
    }
  }
}
```

**Legacy Configuration (Deprecated):**

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "command": "npx",
      "args": ["edgeone-pages-mcp@latest"],
      "env": {
        "EDGEONE_PAGES_API_TOKEN": "",
        "EDGEONE_PAGES_PROJECT_NAME": ""
      }
    }
  }
}
```

### Streaming HTTP MCP Server

For HTTP streaming-capable clients (supports `deploy_html` only):

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "url": "https://mcp-on-edge.edgeone.site/mcp-server"
    }
  }
}
```

Alternative URL for HTML content sharing:

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "url": "https://mcp-on-edge.edgeone.app/mcp-server"
    }
  }
}
```

## Tools

### deploy_html

Deploys HTML content to EdgeOne Pages and returns a publicly accessible URL.

**Architecture Workflow:**
1. Large Language Model generates HTML content
2. Content sent to EdgeOne Pages MCP Server
3. Server deploys to EdgeOne Pages Edge Functions
4. Content stored in EdgeOne KV Store
5. Server returns publicly accessible URL
6. Users access via browser with fast edge delivery

**Features:**
- Uses EdgeOne Pages KV storage for content management
- Auto-generates accessible URLs per deployment
- Comprehensive API error handling
- Integrates with EdgeOne Pages Functions serverless platform

### deploy_folder

Enables complete project deployment to EdgeOne Pages.

**Capabilities:**
- Static website project deployment
- Full-stack application deployment
- Create new projects or update existing ones

**Requirements:**
For deploying folders or zip files, you need to provide an EdgeOne Pages API token. You can obtain your API token from the EdgeOne dashboard.

## Supported Clients

- Cursor
- VSCode
- Windsurf
- ChatWise
- Cherry Studio
- And other MCP-compatible clients

## Self-Hosted Option

You can self-host the EdgeOne Pages MCP server with your own custom domain.

**Repository:** https://github.com/TencentEdgeOne/self-hosted-pages-mcp

**Setup Requirements:**
1. Configure KV storage with namespace variable `my_kv`
2. Bind a custom domain

**Configuration after deployment:**

```json
{
  "mcpServers": {
    "edgeone-pages": {
      "url": "https://your-custom-domain/mcp-server"
    }
  }
}
```

**API deployment example:**

```bash
curl -X POST https://your-custom-domain/kv/set \
  -H "Content-Type: application/json" \
  -d '{"value": "<html><body><h1>Hello, World!</h1></body></html>"}'
```

## Why EdgeOne Pages

EdgeOne Pages leverages Tencent's global edge nodes to provide:
- Edge serverless architecture
- Fast content delivery via edge computing infrastructure
- Scalability without infrastructure management
- Layer-4/7 security protection and acceleration services

## License

MIT

## Links

- [GitHub Repository](https://github.com/TencentEdgeOne/edgeone-pages-mcp)
- [Self-Hosted Repository](https://github.com/TencentEdgeOne/self-hosted-pages-mcp)
- [EdgeOne Pages Documentation](https://pages.edgeone.ai/document/pages-mcp)
- [Tencent EdgeOne](https://edgeone.ai)
