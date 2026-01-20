# Semgrep MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@semgrep/mcp": {
      "url": "https://mcp.semgrep.ai/sse"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=semgrep&config=eyJ1cmwiOiJodHRwczovL21jcC5zZW1ncmVwLmFpL3NzZSJ9)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=semgrep&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.semgrep.ai%2Fsse%22%7D) |

> **Note:** This repository has been deprecated. The Semgrep MCP server has been relocated to the [main Semgrep repository](https://github.com/semgrep/semgrep/tree/develop/cli/src/semgrep/mcp), and further updates will be made via the official `semgrep` binary.

A Model Context Protocol (MCP) server for using Semgrep to scan code for security vulnerabilities.

## Overview

Model Context Protocol (MCP) is a standardized API for LLMs, Agents, and IDEs like Cursor, VS Code, Windsurf, or anything that supports MCP, to get specialized help, get context, and harness the power of tools.

Semgrep is a fast, deterministic static analysis tool that semantically understands many languages and comes with over 5,000 rules.

The Semgrep MCP Server integrates static code analysis with the Model Context Protocol, enabling LLMs and IDEs to scan AI-generated code for security vulnerabilities using Semgrep Code, Supply Chain, and Secrets.

## Quick Start

### Python Package

```bash
uvx semgrep-mcp
```

### Docker

```bash
docker run -i --rm ghcr.io/semgrep/mcp -t stdio
```

## Requirements

- Python 3.10 or later
- Semgrep installation (via Homebrew or Pip)
- Active Semgrep account (for cloud features)

## Available Tools

The MCP server provides the following tools:

| Tool | Description |
|------|-------------|
| `security_check` | Scan code for security vulnerabilities |
| `semgrep_scan` | Scan code files with a given config string |
| `semgrep_scan_with_custom_rule` | Scan using custom Semgrep rules |
| `get_abstract_syntax_tree` | Output the AST of code |
| `semgrep_findings` | Fetch findings from the Semgrep AppSec Platform API |
| `supported_languages` | Return the list of languages Semgrep supports |
| `semgrep_rule_schema` | Get the Semgrep rule schema |

## Transport Protocols

The Semgrep MCP server supports three transport protocols:

1. **stdio** - Standard input/output streams (default)
2. **Streamable HTTP** - JSON RPC over HTTP POST (recommended for networked clients)
3. **SSE** - Server-sent events (legacy protocol)

For streamable-http and sse transports, the server starts an HTTP server on port 8000.

## IDE Configuration

### Cursor

Add the following to your `~/.cursor/mcp.json` (global) or `.cursor/mcp.json` (project-specific) configuration file:

```json
{
  "mcpServers": {
    "semgrep": {
      "command": "uvx",
      "args": ["semgrep-mcp"]
    }
  }
}
```

### VS Code with Copilot

Configure VS Code to use the Semgrep MCP server through your IDE settings. Refer to the VS Code MCP documentation for setup instructions.

### Windsurf

Add the Semgrep MCP configuration to your Windsurf settings following the platform's MCP integration guide.

### Claude Desktop

Add the following to your Claude Desktop configuration:

```json
{
  "mcpServers": {
    "semgrep": {
      "command": "uvx",
      "args": ["semgrep-mcp"]
    }
  }
}
```

### Claude Code

1. Launch Claude: `claude`
2. Add marketplace: `/plugin marketplace add semgrep/mcp-marketplace`
3. Install plugin: `/plugin install semgrep-plugin@semgrep`
4. Setup: `/semgrep-plugin:setup_semgrep_plugin`

### Remote Server (Streamable HTTP)

For streamable HTTP connections, you can configure:

```json
{
  "mcpServers": {
    "semgrep": {
      "type": "streamable-http",
      "url": "https://mcp.semgrep.ai/mcp"
    }
  }
}
```

## Authentication

For cloud platform features (like `semgrep_findings`), authenticate with Semgrep:

```bash
semgrep login && semgrep install-semgrep-pro
```

Set the `SEMGREP_APP_TOKEN` environment variable for automated environments.

## Resources

- **Official Documentation**: https://semgrep.dev/docs/mcp
- **GitHub Repository**: https://github.com/semgrep/mcp
- **Main Semgrep Repository**: https://github.com/semgrep/semgrep
- **PyPI Package**: https://pypi.org/project/semgrep-mcp/
- **Docker Image**: ghcr.io/semgrep/mcp

## Community

This beta project is under active development. The team welcomes feedback, bug reports, feature requests, and code contributions. Join the `#mcp` channel in the Semgrep community Slack workspace.

## License

See the [GitHub repository](https://github.com/semgrep/mcp) for license information.
