# Globalping MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@jsdelivr/globalping-mcp-server": {
      "url": "https://mcp.globalping.dev/sse",
      "headers": {
        "Authorization": "Bearer <GLOBALPING_TOKEN>"
      }
    }
  }
}
```

> **Note:** Replace `<GLOBALPING_TOKEN>` with your Globalping API token for higher rate limits. Get one from [globalping.io](https://globalping.io). The server also supports OAuth authentication.

<p align="center">
  <img src="https://raw.githubusercontent.com/jsdelivr/globalping-media/refs/heads/master/logo/full_colored_dark.svg" alt="Globalping Logo" width="180"/>
</p>

<p align="center">
  <b>Enable AI models to interact with a global network measurement platform through natural language. Give network access to any LLM.</b>
</p>

<p align="center">
  <a href="https://github.com/modelcontextprotocol/modelcontextprotocol">
    <img src="https://img.shields.io/badge/MCP-compatible-brightgreen.svg" alt="MCP Compatible">
  </a>
</p>

## What is Globalping?

[Globalping](https://globalping.io) is a free, public API providing access to a globally distributed network of probes for monitoring, debugging, and benchmarking internet infrastructure. Users can execute network tests (ping, traceroute, DNS, MTR, HTTP) from thousands of worldwide locations.

## What is the Globalping MCP Server?

The Globalping MCP Server implements the [Model Context Protocol (MCP)](https://modelcontextprotocol.io), allowing AI models like OpenAI's GPT and Anthropic's Claude to interact with Globalping's capabilities through natural language.

It supports OAuth and API token authentication, providing secure access and higher rate limits.

### Key Features

- Global Network Access: Run measurements from thousands of probes worldwide
- AI-Friendly Interface: LLMs easily parse data and execute measurements
- Comprehensive Measurements: Support for ping, traceroute, DNS, MTR, and HTTP tests
- Smart Context Handling: Provides detailed parameter descriptions for intelligent measurement selection
- Comparative Analysis: Compare network performance between different targets
- Authentication Support: OAuth or API token authentication with higher rate limits

## Installation

The remote MCP server is available at:
- Streamable HTTP transport: `https://mcp.globalping.dev/mcp`
- SSE transport: `https://mcp.globalping.dev/sse`

### Anthropic Claude API

1. Go to [console.anthropic.com](https://console.anthropic.com/)
2. Navigate to Assistants section
3. Create or edit an Assistant
4. In Tools section, select "Add custom tool"
5. Enter details:
   - Tool Name: `Globalping`
   - Description: `Run network tests from locations worldwide`
   - Tool URL: `https://mcp.globalping.dev/mcp` (Streamable HTTP) or `https://mcp.globalping.dev/sse` (SSE)

### Cursor

1. Open Cursor settings
2. Navigate to Tools & MCP tab
3. Click "+ New MCP server"
4. Add configuration:

Streamable HTTP:
```json
{
    "mcpServers": {
        "globalping": {
            "url": "https://mcp.globalping.dev/mcp"
        }
    }
}
```

5. Save and restart Cursor

## Authentication

The server supports two authentication methods:
- **OAuth Authentication**: Automatically handled by the server
- **API Token Authentication**: Manual token configuration via Authorization header

Both provide higher rate limits and priority access.

### Using Globalping API Token

The server automatically detects API tokens in the Authorization header.

### Getting Your API Token

1. Visit [dash.globalping.io](https://dash.globalping.io)
2. Sign in to your account
3. Navigate to Tokens to generate a new API token

### Configuration with Authentication

Streamable HTTP:
```json
{
    "mcpServers": {
        "globalping": {
            "url": "https://mcp.globalping.dev/mcp",
            "headers": {
                "Authorization": "Bearer YOUR_GLOBALPING_API_TOKEN"
            }
        }
    }
}
```

## Connecting AI Assistants

Use the MCP server with any MCP-compatible AI assistant, including:
- Claude Desktop
- Anthropic Assistants
- Cursor
- Windsurf
- Custom MCP protocol implementations

## Available Tools

- `ping` - Perform a ping test to a target
- `traceroute` - Perform a traceroute test to a target
- `dns` - Perform a DNS lookup for a domain
- `mtr` - Perform an MTR (My Traceroute) test to a target
- `http` - Perform an HTTP request to a URL
- `locations` - List all available Globalping probe locations
- `limits` - Show current rate limits
- `getMeasurement` - Retrieve a previously run measurement by ID
- `compareLocations` - Guide on running comparison measurements
- `help` - Show help message with available tools documentation

## Usage Examples

Natural language interactions through MCP-compatible clients:

```
Ping google.com from 3 locations in Europe
```

```
Run a traceroute to github.com from Japan and compare with traceroute from the US
```

```
Check the DNS resolution of example.com using Google DNS (8.8.8.8)
```

```
Is jsdelivr.com reachable from China? Test with both ping and HTTP
```

```
What's the average response time for cloudflare.com across different continents?
```

## Location Specification

Locations can be specified using the "magic" field, supporting various formats:

- Continent codes: "EU", "NA", "AS", etc.
- Country codes: "US", "DE", "JP", etc.
- City names: "London", "Tokyo", "New York", etc.
- Network names: "Cloudflare", "Google", etc.
- ASN numbers: "AS13335", "AS15169", etc.
- Cloud provider regions: "aws-us-east-1", "gcp-us-central1", etc.

Combine with plus signs for specific targeting: "London+UK", "Cloudflare+US", etc.

