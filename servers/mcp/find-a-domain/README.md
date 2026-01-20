# Find-A-Domain MCP Server

## Server Config

```json
{
  "mcpServers": {
    "find-a-domain": {
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/find-a-domain"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=find-a-domain&config=eyJ1cmwiOiJodHRwczovL2dhdGV3YXkubWNwLmNvcmVzcGVlZC5pby9tY3AtZ2F0ZXdheS9maW5kLWEtZG9tYWluIn0=)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=find-a-domain&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fgateway.mcp.corespeed.io%2Fmcp-gateway%2Ffind-a-domain%22%7D) |

A Model Context Protocol (MCP) server that provides domain availability checking and WHOIS lookup tools. This remote MCP server enables AI assistants to verify domain availability across 1444+ top-level domains (TLDs) in real-time.

## Overview

| Property | Value |
|----------|-------|
| **Server Name** | findadomain-api |
| **Version** | 1.0.0 |
| **Protocol** | Model Context Protocol (MCP) |
| **Transport** | HTTP-based (Streamable HTTP) |
| **Endpoint** | `https://gateway.mcp.corespeed.io/mcp-gateway/find-a-domain` |
| **Authentication** | Open (no authentication required) |
| **Category** | Productivity |

## Features

- Real-time domain availability verification across all major TLDs
- Support for 1444+ top-level domains including:
  - **Generic TLDs**: .com, .org, .net, .info, .xyz, .tech, .app, .cloud, and more
  - **Country Code TLDs**: Over 200 country-specific extensions (.uk, .de, .jp, .au, .ca, etc.)
  - **Internationalized TLDs**: Non-Latin script domains (Arabic, Chinese, Cyrillic, etc.)
  - **Sponsored TLDs**: .aero, .coop, .museum, .gov, .mil, and specialized extensions
- WHOIS lookup verification
- Seamless AI assistant integration
- Clean API design with structured responses

## Available Tools

### 1. check_domain

Verify domain availability for specific TLDs.

**Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name` | string | Yes | Domain identifier without extension (e.g., "example") |
| `tld` | string | Yes | Top-level domain extension (e.g., "com", "org", "net") |
| `whois` | boolean | No | Enable WHOIS lookup verification |

**Example Request:**

```json
{
  "name": "example",
  "tld": "com",
  "whois": true
}
```

### 2. list_tlds

Retrieve all supported top-level domains.

**Parameters:** None required

**Example Response:**

```json
{
  "tlds": ["com", "net", "org", "..."],
  "count": 1444
}
```

## Configuration

### Claude Desktop (via UI)

Since Find-A-Domain is a remote MCP server, you can add it directly through the Claude Desktop UI:

1. Open Claude Desktop and navigate to **Settings**
2. Click on **Connectors** in the sidebar
3. Scroll to the bottom and click **Add custom connector**
4. Enter the remote MCP server URL: `https://gateway.mcp.corespeed.io/mcp-gateway/find-a-domain`
5. Click **Add** to connect

### Claude Desktop (via config file)

For Claude Desktop with HTTP/Streamable HTTP support, add to your configuration file:

**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "find-a-domain": {
      "type": "http",
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/find-a-domain"
    }
  }
}
```

### Using mcp-remote (for clients without native HTTP support)

For MCP clients that don't natively support remote servers, you can use the `mcp-remote` package:

```json
{
  "mcpServers": {
    "find-a-domain": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://gateway.mcp.corespeed.io/mcp-gateway/find-a-domain"
      ]
    }
  }
}
```

## Use Cases

### For Entrepreneurs & Startups
- **Brand Protection**: Check domain availability across multiple TLDs simultaneously
- **Market Research**: Identify available domains in target markets
- **Business Planning**: Secure domain names during ideation phase

### For Developers & Agencies
- **Client Services**: Offer domain checking as part of web development services
- **Project Planning**: Verify domain availability before project kickoff
- **Domain Strategy**: Help clients choose optimal domain extensions

### For Digital Marketers
- **Campaign Planning**: Secure campaign-specific domains
- **Brand Expansion**: Check domain availability across different regions
- **SEO Strategy**: Identify keyword-rich available domains

### For Domain Investors
- **Investment Research**: Identify valuable available domains
- **Portfolio Expansion**: Check availability of premium domains
- **Market Analysis**: Track domain availability trends

## Usage Examples

Once configured, you can ask your AI assistant questions like:

- "Check if mydomain.com is available"
- "Is example available as a .io or .dev domain?"
- "What TLDs are available for the name 'startup'?"
- "Get WHOIS information for example.org"
- "List all supported top-level domains"

## Why Choose Find-A-Domain MCP Server?

- **Specialized Focus**: Dedicated domain checking functionality
- **Comprehensive Coverage**: 1444+ TLD support
- **Real-time Results**: Instant domain availability status
- **Easy Integration**: Standard MCP protocol compatibility
- **Reliable Service**: Hosted at optimized infrastructure
- **Developer-Friendly**: Clean API design and documentation

## Resources

- **Official Website**: [https://findadomain.dev](https://findadomain.dev)
- **MCP Documentation**: [https://findadomain.dev/mcp](https://findadomain.dev/mcp)
- **Remote MCP Listing**: [https://www.remote-mcp.com/servers/find-a-domain](https://www.remote-mcp.com/servers/find-a-domain)
- **API Endpoint**: `https://gateway.mcp.corespeed.io/mcp-gateway/find-a-domain`
- **Support**: support@findadomain.dev

## Related MCP Servers

If you need additional domain-related functionality, consider these alternative MCP servers:

- [mcp-domain-availability](https://github.com/imprvhub/mcp-domain-availability) - Claude Desktop domain checker with 50+ TLDs support
- [Instant Domain Search MCP](https://instantdomainsearch.com/mcp) - Real-time domain search with AI-powered suggestions
- [domain-checker-mcp-server](https://github.com/ajot/domain-checker-mcp-server) - WHOIS and DNS resolution based checking
- [GoDaddy MCP Server](https://developer.godaddy.com/mcp) - Official GoDaddy domain search integration

## License

Please refer to the official Find-A-Domain website for licensing and terms of service information.
