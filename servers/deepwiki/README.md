# DeepWiki MCP Server

## Server Config

```json
{
  "mcpServers": {
    "deepwiki": {
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/deepwiki"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=deepwiki&config=eyJ1cmwiOiJodHRwczovL2dhdGV3YXkubWNwLmNvcmVzcGVlZC5pby9tY3AtZ2F0ZXdheS9kZWVwd2lraSJ9)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=deepwiki&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fgateway.mcp.corespeed.io%2Fmcp-gateway%2Fdeepwiki%22%7D) |

The **DeepWiki MCP Server** provides programmatic access to DeepWiki's public repository documentation and AI-powered search capabilities (Ask Devin). It is a free, remote, no-authentication-required service that allows AI agents to explore and understand GitHub repositories through structured documentation.

---

## 🚀 Server Endpoints

The server supports two wire protocols for maximum compatibility:

* **SSE (Server-Sent Events) - Recommended:** `https://gateway.mcp.corespeed.io/mcp-gateway/deepwiki`
* **Streamable HTTP:** `https://gateway.mcp.corespeed.io/mcp-gateway/deepwiki`

---

## 🛠 Available Tools

Once connected, your AI agent will have access to the following tools:

* **`read_wiki_structure`**: Get a list of documentation topics/structure for a specific GitHub repository.
* **`read_wiki_contents`**: Retrieve and view detailed documentation content about a GitHub repository.
* **`ask_question`**: Ask any natural language question about a repository and receive an AI-powered, context-grounded response.

---

## ⚙️ Setup Instructions

### For Cursor / Windsurf
Add the following to your MCP configuration settings:

```json
{
  "mcpServers": {
    "deepwiki": {
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/deepwiki"
    }
  }
}
```

### For Claude Code

Run the following command in your terminal:

```bash
claude mcp add -s user -t http deepwiki [https://gateway.mcp.corespeed.io/mcp-gateway/deepwiki](https://gateway.mcp.corespeed.io/mcp-gateway/deepwiki)

```

### For Claude Desktop

Add the server as a Custom Connector using the SSE URL:

* **Name:** DeepWiki
* **URL:** `https://gateway.mcp.corespeed.io/mcp-gateway/deepwiki`

---

## 🔒 Private Repositories

The public server provides access to **public repositories only**. If you need DeepWiki capabilities for private repositories, sign up for a [Devin account](https://devin.ai) to use the Devin MCP server with your personal API key.
