# sentry-mcp

## Server Config

```json
{
  "mcpServers": {
    "@getsentry/sentry-mcp": {
      "url": "https://mcp.sentry.dev/mcp"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=sentry&config=eyJ1cmwiOiJodHRwczovL21jcC5zZW50cnkuZGV2L21jcCJ9)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=sentry&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.sentry.dev%2Fmcp%22%7D) |

An MCP (Model Context Protocol) server for interacting with Sentry via LLMs.

**Repository:** https://github.com/getsentry/sentry-mcp

**Production URL:** https://mcp.sentry.dev

## Overview

Sentry's MCP service is designed for human-in-the-loop coding agents. The tool selection prioritizes developer workflows and debugging use cases rather than general-purpose Sentry functionality.

This remote MCP server acts as middleware to the Sentry API, optimized for coding assistants like Cursor, Claude Code, and similar development tools.

### Key Features

- OAuth support for authentication using your existing Sentry organization
- Streamable HTTP with graceful SSE fallback
- 16+ tool calls and prompts for comprehensive Sentry context
- Seer integration for AI-powered root cause analysis

## Getting Started

Visit the production deployment at **https://mcp.sentry.dev** for complete documentation.

### Client Configuration

**Claude Code:**

From your CLI enter:
```bash
claude mcp add --transport http sentry https://mcp.sentry.dev/mcp
```

Then access Claude Code with `claude`. Once in, you'll be prompted to authenticate with OAuth to Sentry.

**Codex:**

From your CLI, enter:
```bash
codex mcp add sentry -- npx -y mcp-remote@latest https://mcp.sentry.dev/mcp
```

**Cursor:**

Available via Cursor → Settings → Cursor Settings → MCP following the prompts to configure Sentry MCP. Cursor 1.0+ includes enhanced MCP support with OAuth and Streamable HTTP.

## Seer Integration

The Sentry MCP Server provides seamless integration with Seer, Sentry's AI agent:
- Trigger Seer Analysis for automated root cause analysis
- Get AI-generated fix recommendations
- Monitor fix status

## Related Resources

- [Sentry MCP Documentation](https://docs.sentry.io/product/sentry-mcp/)
- [MCP Monitoring/Observability](https://docs.sentry.io/product/insights/ai/mcp/)
- [Python SDK MCP Integration](https://docs.sentry.io/platforms/python/integrations/mcp/)
- [Sentry MCP STDIO (legacy)](https://github.com/getsentry/sentry-mcp-stdio)

## License

See the repository for license information.
