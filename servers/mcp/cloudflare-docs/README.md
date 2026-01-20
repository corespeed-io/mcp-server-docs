# Cloudflare MCP Server

## Server Config

```json
{
  "mcpServers": {
    "cloudflare-docs": {
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/cloudflare-docs"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=cloudflare-docs&config=eyJ1cmwiOiJodHRwczovL2dhdGV3YXkubWNwLmNvcmVzcGVlZC5pby9tY3AtZ2F0ZXdheS9jbG91ZGZsYXJlLWRvY3MifQ==)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=cloudflare-docs&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fgateway.mcp.corespeed.io%2Fmcp-gateway%2Fcloudflare-docs%22%7D) |

Model Context Protocol (MCP) is a new, standardized protocol for managing context between large language models (LLMs) and external systems. This repository contains several MCP servers enabling connections to Cloudflare services from MCP clients like Cursor or Claude.

These servers allow your MCP Client to read account configurations, process information, make suggestions, and execute changes across Cloudflare's services including application development, security, and performance tools.

The servers support both `streamable-http` transport via `/mcp` and `sse` transport (deprecated) via `/sse`.

## Included Servers

| Server Name | Description | Server URL |
|---|---|---|
| **Documentation server** | Get up to date reference information on Cloudflare | `https://gateway.mcp.corespeed.io/mcp-gateway/cloudflare-docs` |
| **Workers Bindings server** | Build Workers applications with storage, AI, and compute primitives | `https://bindings.mcp.cloudflare.com/mcp` |
| **Workers Builds server** | Get insights and manage your Cloudflare Workers Builds | `https://builds.mcp.cloudflare.com/mcp` |
| **Observability server** | Debug and get insight into your application's logs and analytics | `https://observability.mcp.cloudflare.com/mcp` |
| **Radar server** | Get global Internet traffic insights, trends, URL scans, and utilities | `https://radar.mcp.cloudflare.com/mcp` |
| **Container server** | Spin up a sandbox development environment | `https://containers.mcp.cloudflare.com/mcp` |
| **Browser rendering server** | Fetch web pages, convert them to markdown and take screenshots | `https://browser.mcp.cloudflare.com/mcp` |
| **Logpush server** | Get quick summaries for Logpush job health | `https://logs.mcp.cloudflare.com/mcp` |
| **AI Gateway server** | Search your logs, get details about the prompts and responses | `https://ai-gateway.mcp.cloudflare.com/mcp` |
| **AutoRAG server** | List and search documents on your AutoRAGs | `https://autorag.mcp.cloudflare.com/mcp` |
| **Audit Logs server** | Query audit logs and generate reports for review | `https://auditlogs.mcp.cloudflare.com/mcp` |
| **DNS Analytics server** | Optimize DNS performance and debug issues based on current set up | `https://dns-analytics.mcp.cloudflare.com/mcp` |
| **Digital Experience Monitoring server** | Get quick insight on critical applications for your organization | `https://dex.mcp.cloudflare.com/mcp` |
| **Cloudflare One CASB server** | Quickly identify any security misconfigurations for SaaS applications | `https://casb.mcp.cloudflare.com/mcp` |
| **GraphQL server** | Get analytics data using Cloudflare's GraphQL API | `https://graphql.mcp.cloudflare.com/mcp` |

## Access the Remote MCP Server from Any MCP Client

If your MCP client supports remote servers natively, specify the server URL directly in its interface (e.g., Cloudflare AI Playground).

## Using Cloudflare's MCP Servers from the OpenAI Responses API

To use these servers with OpenAI's responses API, you will need to provide an API token with required scopes. Create a token in your Cloudflare dashboard with appropriate permissions for your desired server.

## Need Access to More Cloudflare Tools?

The repository continues expanding functionality. File feedback, bugs, or feature requests by opening an issue on the repository.

## Troubleshooting

**"Claude's response was interrupted..."**

This occurs when Claude reaches context-length limits, commonly with servers triggering multiple chained tool calls (such as observability).

To reduce this issue:
- Be specific and keep queries concise
- Break multi-tool requests into smaller separate calls

## Paid Features

Some features require a paid Cloudflare Workers plan. Ensure your account has necessary subscription levels.

## Contributing

For local development and contribution details, see CONTRIBUTING.md.

---

**Source:** [cloudflare/mcp-server-cloudflare](https://github.com/cloudflare/mcp-server-cloudflare)

**Official Documentation:** [Cloudflare Agents - Model Context Protocol](https://developers.cloudflare.com/agents/model-context-protocol/)
