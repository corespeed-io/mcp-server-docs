# Astro Docs MCP Server

## Server Config

```json
{
  "mcpServers": {
    "astro-docs": {
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/astro-docs"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=astro-docs&config=eyJ1cmwiOiJodHRwczovL2dhdGV3YXkubWNwLmNvcmVzcGVlZC5pby9tY3AtZ2F0ZXdheS9hc3Ryby1kb2NzIn0=)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=astro-docs&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fgateway.mcp.corespeed.io%2Fmcp-gateway%2Fastro-docs%22%7D) |

This is the Model Context Protocol (MCP) server for the Astro documentation, allowing AI tools such as Cursor, VS Code, Claude, ChatGPT, and Windsurf to access the latest Astro docs.

MCP is a standardized way to connect language models to external tools, data, and APIs. This server allows LLMs to access the Astro documentation in a structured way, enabling them to answer questions about Astro's features, APIs, and best practices. This allows tools to use up-to-date and accurate documentation when generating code, answering questions, or providing assistance.

## Usage

The Astro Docs MCP server is a remote server that doesn't require anything to be installed locally. You need to add the following settings to your MCP-compatible tool:

- Name: `Astro Docs`
- URL: `https://gateway.mcp.corespeed.io/mcp-gateway/astro-docs`
- Transport: `http`

> [!NOTE]
> This server uses the new _streamable HTTP_ transport. Some tools only support _SSE_ transport for remote servers, which is not compatible with this server. If your tool does not support streamable HTTP, you will need to use a local proxy. See the Windsurf section below for details.

Each tool has its own way of adding MCP servers, so here are instructions for some popular tools:

### Cursor

GitHub doesn't support Cursor deep links, so open the link below in your browser to install the MCP server in Cursor:

```
cursor://anysphere.cursor-deeplink/mcp/install?name=Astro%20docs&config=eyJ1cmwiOiJodHRwczovL21jcC5kb2NzLmFzdHJvLmJ1aWxkL21jcCJ9
```

[More info on MCP in Cursor](https://docs.cursor.com/context/mcp)

### Claude.ai / Claude Desktop

- Visit [Claude.ai connector settings](https://claude.ai/settings/connectors)
- Scroll down and click "Add custom connector"
- Enter the following details:
  - **Name**: Astro Docs
  - **Remote MCP server URL**: https://gateway.mcp.corespeed.io/mcp-gateway/astro-docs

[More info on MCP in Claude.ai](https://support.anthropic.com/en/articles/10168395-setting-up-integrations-on-claude-ai#h_cda40ecb32)

### Claude Code

Run the following command in your terminal to add the MCP server:

```sh
claude mcp add --transport http "Astro docs" https://gateway.mcp.corespeed.io/mcp-gateway/astro-docs
```

[More info on MCP in Claude Code](https://docs.anthropic.com/en/docs/claude-code/mcp)

### VS Code

GitHub doesn't support VS Code deep links, so open the link below in your browser to install the MCP server in VS Code:

```
vscode:mcp/install?%7B%22name%22%3A%22Astro%20docs%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.docs.astro.build%2Fmcp%22%7D
```

[More info on MCP in VS Code](https://code.visualstudio.com/docs/copilot/chat/mcp-servers#_add-an-mcp-server)

### ChatGPT

As of July 2025, ChatGPT only supports MCP servers (which it calls Custom Connectors) for Pro, Team and Enterprise users. The steps to add a cutom connector are complicated. See [the OpenAI documentation](https://platform.openai.com/docs/mcp#test-and-connect-your-mcp-server) for details.