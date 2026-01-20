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
