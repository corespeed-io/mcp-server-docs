# Webflow's MCP server

## Server Config

```json
{
  "mcpServers": {
    "@webflow/mcp-server": {
      "url": "https://mcp.webflow.com/sse"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=webflow&config=eyJ1cmwiOiJodHRwczovL21jcC53ZWJmbG93LmNvbS9zc2UifQ==)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=webflow&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.webflow.com%2Fsse%22%7D) |

A Node.js server implementing Model Context Protocol (MCP) for Webflow using the [Webflow JavaScript SDK](https://github.com/webflow/js-webflow-api). Enable AI agents to interact with Webflow APIs. Learn more about Webflow's Data API in the [developer documentation](https://developers.webflow.com/data/reference).

[![npm shield](https://img.shields.io/npm/v/webflow-mcp-server)](https://www.npmjs.com/package/webflow-mcp-server)
![Webflow](https://img.shields.io/badge/webflow-%23146EF5.svg?style=for-the-badge&logo=webflow&logoColor=white)

## Prerequisites

- [Node.js](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
- [NPM](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
- [A Webflow Account](https://webflow.com/signup)

## 🚀 Remote installation

Get started by installing Webflow's remote MCP server. The remote server uses OAuth to authenticate with your Webflow sites, and a companion app that syncs your live canvas with your AI agent.

### Requirements

- Node.js 22.3.0 or higher

> Note: The MCP server currently supports Node.js 22.3.0 or higher. If you run into version issues, see the [Node.js compatibility guidance.](https://developers.webflow.com/data/v2.0.0/docs/ai-tools#nodejs-compatibility)

### Cursor

#### Add MCP server to Cursor

1. Go to `Settings → Cursor Settings → MCP & Integrations`.
2. Under MCP Tools, click `+ New MCP Server`.
3. Paste the following configuration into `.cursor/mcp.json` (or add the `webflow` part to your existing configuration):

```json
{
  "mcpServers": {
    "@webflow/mcp-server": {
      "url": "https://mcp.webflow.com/sse"
    }
  }
}
```

> Tip: You can create a project-level `mcp.json` to avoid repeated auth prompts across multiple Cursor windows. See Cursor's docs on [configuration locations.](https://docs.cursor.com/en/context/mcp#configuration-locations)

4. Save and close the file. Cursor will automatically open an OAuth login page where you can authorize Webflow sites to use with the MCP server.

#### Open the Webflow Designer

- Open your site in the Webflow Designer, or ask your AI agent:

```text
Give me a link to open <MY_SITE_NAME> in the Webflow Designer
```

#### Open the MCP Webflow App

1. In the Designer, open the Apps panel (press `E`).
2. Launch your published "Webflow MCP Bridge App".
3. Wait for the app to connect to the MCP server.

#### Write your first prompt

Try these in your AI chat:

```text
Analyze my last 5 blog posts and suggest 3 new topic ideas with SEO keywords
```

```text
Find older blog posts that mention similar topics and add internal links to my latest post
```

```text
Create a hero section card on my home page with a CTA button and responsive design
```

### Reset your OAuth token

To reset your OAuth token, run the following command in your terminal.

```bash
rm -rf ~/.mcp-auth
```

### Node.js compatibility

Please see the Node.js [compatibility guidance on Webflow's developer docs.](https://developers.webflow.com/data/v2.0.0/docs/ai-tools#nodejs-compatibility)

## 🛠️ Available tools

See the `./tools` directory for a list of available tools

# 🗣️ Prompts & resources

This implementation **doesn't** include `prompts` or `resources` from the MCP specification. However, this may change in the future when there is broader support across popular MCP clients.

## 📄 Webflow developer resources

- [Webflow API Documentation](https://developers.webflow.com/data/reference)
- [Webflow JavaScript SDK](https://github.com/webflow/js-webflow-api)

## ⚠️ Known limitations

### Static page content updates

The `pages_update_static_content` endpoint currently only supports updates to localized static pages in secondary locales. Updates to static content in the default locale aren't supported and will result in errors.
