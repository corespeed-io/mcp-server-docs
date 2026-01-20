# Context Awesome - MCP Server

## Server Config

```json
{
  "mcpServers": {
    "context-awesome": {
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/context-awesome"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=context-awesome&config=eyJ1cmwiOiJodHRwczovL2dhdGV3YXkubWNwLmNvcmVzcGVlZC5pby9tY3AtZ2F0ZXdheS9jb250ZXh0LWF3ZXNvbWUifQ==)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=context-awesome&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fgateway.mcp.corespeed.io%2Fmcp-gateway%2Fcontext-awesome%22%7D) |

Give your AI agents access to **8,500+ Awesome Lists** with over **1 million curated resources** from GitHub.

**Context Awesome** is a Model Context Protocol (MCP) server that provides instant access to the entire "awesome" ecosystem. It enables AI agents to discover and retrieve high-quality, community-curated resources across any domain, replacing random search results with vetted tools and libraries.

---

## 🚀 Quick Setup (Hosted Server)

No installation is required. You can simply add the following configuration to your preferred MCP client:

**Hosted Server URL:** `https://gateway.mcp.corespeed.io/mcp-gateway/context-awesome`

### Cursor
Navigate to **Settings** → **Cursor Settings** → **MCP** → **Add new global MCP server**:
```json
{
  "mcpServers": {
    "context-awesome": {
      "url": "[https://gateway.mcp.corespeed.io/mcp-gateway/context-awesome](https://gateway.mcp.corespeed.io/mcp-gateway/context-awesome)"
    }
  }
}

```

### Claude Code

Run the following command in your terminal:

```bash
claude mcp add --transport http context-awesome [https://gateway.mcp.corespeed.io/mcp-gateway/context-awesome](https://gateway.mcp.corespeed.io/mcp-gateway/context-awesome)

```

### VS Code

Add the following to your MCP settings:

```json
"mcp": {
  "servers": {
    "context-awesome": {
      "type": "http",
      "url": "[https://gateway.mcp.corespeed.io/mcp-gateway/context-awesome](https://gateway.mcp.corespeed.io/mcp-gateway/context-awesome)"
    }
  }
}

```

### Claude Desktop

Go to **Settings** → **Connectors** → **Add Custom Connector**:

* **Name:** Context Awesome
* **URL:** `https://gateway.mcp.corespeed.io/mcp-gateway/context-awesome`

---

## 🛠 Available MCP Tools

* **`find_awesome_section`**: Discovers sections and categories across awesome lists matching your search query.
* *Parameters:* `query`, `confidence`, `limit`


* **`get_awesome_items`**: Retrieves items from a specific list or section with token limiting for optimal context usage.
* *Parameters:* `listId`, `section`, `tokens`, `offset`



---

## 💡 Example Queries

* "Find the best machine learning resources for Python"
* "What are the best resources for authoring technical books?"
* "Show me testing tools from awesome-rust"
* "Get React component libraries from awesome lists"
* "Find database ORMs in Go awesome lists"

## ✨ Features

* **Vast Coverage:** Search across 8,500+ curated awesome lists.
* **Curated Content:** Access over 1 million community-vetted resources.
* **Plug & Play:** Direct integration with Claude, Cursor, and VS Code.
* **Efficient:** Token-optimized responses designed for LLM context windows.

---

*Built with the Model Context Protocol (MCP) SDK. Data powered by the global GitHub community.*
