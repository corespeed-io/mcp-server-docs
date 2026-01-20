# Hugging Face MCP Server

## Server Config

```json
{
  "mcpServers": {
    "huggingface": {
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/hugging-face"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=huggingface&config=eyJ1cmwiOiJodHRwczovL2dhdGV3YXkubWNwLmNvcmVzcGVlZC5pby9tY3AtZ2F0ZXdheS9odWdnaW5nLWZhY2UifQ==)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=huggingface&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fgateway.mcp.corespeed.io%2Fmcp-gateway%2Fhugging-face%22%7D) |

The Hugging Face MCP (Model Context Protocol) Server connects your MCP-compatible AI assistant (for example Codex, Cursor, VS Code extensions, Zed, ChatGPT or Claude Desktop) directly to the Hugging Face Hub. Once connected, your assistant can search and explore Hub resources and use community tools, all from within your editor, chat or CLI.

## What you can do

- Search and explore Hub resources: models, datasets, Spaces, and papers.
- Run community tools via MCP-compatible Gradio apps hosted on [Spaces](https://hf.co/spaces).
- Bring results back into your assistant with metadata, links, and context.

## Get started

1. **Open your MCP settings**: visit https://huggingface.co/settings/mcp while logged in.

2. **Pick your client**: select your MCP-compatible client (for example Cursor, VS Code, Zed, Claude Desktop). The page shows client-specific instructions and a ready-to-copy configuration snippet.

3. **Paste and restart**: copy the snippet into your client's MCP configuration, save, and restart/reload the client. You should see "Hugging Face" (or similar) listed as a connected MCP server in your client.

> **Tip**: The settings page generates the exact configuration your client expects. Use it rather than writing config by hand.

## Installation Methods

### Claude Desktop/claude.ai

Add the Hugging Face connector via settings or use the direct installation link at https://claude.ai/settings/connectors

### Claude Code

```bash
claude mcp add hf-mcp-server -t http https://gateway.mcp.corespeed.io/mcp-gateway/hugging-face?login
```

### Gemini CLI

```bash
gemini mcp add -t http huggingface https://gateway.mcp.corespeed.io/mcp-gateway/hugging-face?login
```

### VSCode & Cursor

Direct installation available through respective galleries, or manual configuration with authentication headers.

## Local Development

### Quick Start

```bash
npx @llmindset/hf-mcp-server          # STDIO mode
npx @llmindset/hf-mcp-server-http     # HTTP mode
npx @llmindset/hf-mcp-server-json     # JSON mode
```

### Docker

```bash
docker run --rm -p 3000:3000 ghcr.io/evalstate/hf-mcp-server:latest
```

## Supported Transports

- **STDIO**: Standard input/output mode
- **SSE**: Server-Sent Events (deprecated but available)
- **StreamableHTTP**: HTTP streaming mode
- **StreamableHTTPJson**: Stateless JSON mode

The web application and HTTP transports default to Port 3000, with SSE available at `/sse` and MCP at `/mcp`.

## Using the server

After connecting, ask your assistant to use the Hugging Face tools. Example prompts:

- "Search Hugging Face models for Qwen 3 Quantizations."
- "Find a Space that can transcribe audio files."
- "Show datasets about weather time-series."
- "Create a 1024 x 1024 image of a cat ghibli style."

Your assistant will call MCP tools exposed by the Hugging Face MCP Server (including Spaces) and return results (titles, owners, downloads, links, and so on). You can then open the resource on the Hub or continue iterating in the same chat.

## Add community tools (Spaces)

You can extend your setup with MCP-compatible Gradio spaces built by the community:

- Explore Spaces with MCP support [here](https://huggingface.co/spaces?filter=mcp-server).
- Add the relevant space in your MCP settings on Hugging Face [here](https://huggingface.co/settings/mcp).

Gradio MCP apps expose their functions as tools (with arguments and descriptions) so your assistant can call them directly. Please, restart or refresh your client so it picks up new tools you add.

Check out our dedicated guide for Spaces as MCP server [here](https://huggingface.co/docs/hub/spaces-mcp-servers#add-an-existing-space-to-your-mcp-tools).

## Environment Variables

- `TRANSPORT`: Transport type selection
- `DEFAULT_HF_TOKEN`: Authentication (development only)
- `HF_API_TIMEOUT`: API request timeout (default 12.5s)
- `MCP_STRICT_COMPLIANCE`: JSON mode validation
- `SEARCH_ENABLES_FETCH`: Auto-enable fetch with search

> **Tip**: Append `?no_image_content=true` to disable image content blocks from Gradio servers.

## Build & Development

The project uses `pnpm` for package management (v10.12.3 via Corepack).

**Commands**:
- `pnpm install` - Install dependencies
- `pnpm build` - Compile packages
- `pnpm dev` - Watch mode with HMR

## Learn more

- **Settings and client setup**: https://huggingface.co/settings/mcp
- **Changelog announcement**: https://huggingface.co/changelog/hf-mcp-server
- **Hugging Face MCP Server**: https://gateway.mcp.corespeed.io/mcp-gateway/hugging-face
- **Build your own MCP Server with Gradio Spaces**: https://www.gradio.app/guides/building-mcp-server-with-gradio
- **GitHub Repository**: https://github.com/huggingface/hf-mcp-server
- **Official Documentation**: https://huggingface.co/docs/hub/en/hf-mcp-server
