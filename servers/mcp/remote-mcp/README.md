# Remote MCP

## Server Config

```json
{
  "mcpServers": {
    "@remote-mcp/server": {
      "url": "https://mcp.remote-mcp.com"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=remote-mcp&config=eyJ1cmwiOiJodHRwczovL21jcC5yZW1vdGUtbWNwLmNvbSJ9)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=remote-mcp&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.remote-mcp.com%22%7D) |

Remote MCP encompasses two related projects: **remote-mcp.com** (an MCP server directory) and **Remote-MCP** (a TypeScript library for remote MCP communication).

## remote-mcp.com - AI Connectors Directory

**Website**: https://remote-mcp.com

Remote MCP is a comprehensive directory of MCP (Model Context Protocol) Remote servers designed for integration with Claude Custom Connectors and ChatGPT Custom Connectors.

### Key Features

**Server Directory**
The platform hosts 70+ MCP servers across various categories including:
- Software Development (GitHub, Vercel, Netlify)
- Project Management (Asana, Linear, Notion)
- Payments (Stripe, PayPal, Square)
- CMS platforms (Webflow, Wix)
- RAG-as-a-Service (Dappier, Needle, OneContext)
- Documentation services (Astro, Cloudflare)

**Search & Discovery**
- Searchable server directory by name, category, or provider
- Filter by authentication type (OAuth2.1, API Key, Open)
- Installation activity metrics (14-day tracking)

**Quick Start Options**
- Separate guides for ChatGPT and Claude connector setup
- One-click server connection interface

### Community

The directory is maintained at [awesome-remote-mcp-servers](https://github.com/jaw9c/awesome-remote-mcp-servers) on GitHub, allowing community contributions of new MCP servers.

---

## Remote-MCP - TypeScript Library

**GitHub**: https://github.com/RemoteMCP/Remote-MCP

Remote-MCP is a TypeScript library enabling bidirectional remote Model Context Protocol (MCP) communication. It provides a type-safe, bidirectional and simple solution for remote MCP communication.

### Architecture

The system uses a decoupled architecture:
- **Client-side**: Local MCP server (`@remote-mcp/client`) proxies requests to remote endpoints
- **Server-side**: Remote MCP implementation (`@remote-mcp/server`) handles actual context operations
- **Protocol**: tRPC over HTTP establishes the communication layer between components

This contrasts with traditional setups where clients connect directly to multiple local MCP servers.

### Core Capabilities

**Currently Implemented:**
- Type-safe client-server communication
- MCP tool invocation
- MCP command execution
- MCP prompt management
- Custom HTTP headers with authentication support

**In Development:**
- Crash-safe error handling (priority feature)
- Event subscription system for resource changes
- Tool/prompt list notifications
- Middleware framework

### Repository Structure

Two primary packages comprise this monorepo:
- `@remote-mcp/client`: Client library functioning as a local MCP proxy
- `@remote-mcp/server`: Server library for creating remotely accessible MCP services

### Project Status

**Stage**: Experimental/active development

> Warning: Expect breaking changes and potential issues

### License

MIT License

### Links

- Website: https://remote-mcp.com
- GitHub: https://github.com/RemoteMCP/Remote-MCP
- NPM Client: https://www.npmjs.com/package/@remote-mcp/client
- NPM Server: https://www.npmjs.com/package/@remote-mcp/server
- Awesome Remote MCP Servers: https://github.com/jaw9c/awesome-remote-mcp-servers
