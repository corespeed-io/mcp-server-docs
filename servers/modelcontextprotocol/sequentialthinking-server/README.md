# Sequential Thinking MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@modelcontextprotocol/sequentialthinking-server": {
      "url": "https://remote.mcpservers.org/sequentialthinking/mcp"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=sequential-thinking&config=eyJ1cmwiOiJodHRwczovL3JlbW90ZS5tY3BzZXJ2ZXJzLm9yZy9zZXF1ZW50aWFsdGhpbmtpbmcvbWNwIn0=)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=sequential-thinking&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fremote.mcpservers.org%2Fsequentialthinking%2Fmcp%22%7D) |

An MCP server implementation that provides a tool for dynamic and reflective problem-solving through a structured thinking process.

## Overview

The Sequential Thinking MCP Server facilitates a detailed, step-by-step thinking process for problem-solving and analysis. It enables:

- Breaking down complex problems into manageable steps
- Revising and refining thoughts as understanding develops
- Branching into alternative reasoning paths
- Dynamically adjusting the total number of thoughts needed
- Generating and verifying solution hypotheses

## Tool: sequential_thinking

This tool facilitates detailed, step-by-step problem-solving through the following inputs:

### Required Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `thought` | string | The current thinking step |
| `nextThoughtNeeded` | boolean | Whether another thought step is required |
| `thoughtNumber` | integer | Current thought number |
| `totalThoughts` | integer | Estimated total thoughts needed |

### Optional Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `isRevision` | boolean | Indicates whether this revises previous thinking |
| `revisesThought` | integer | Which thought is being reconsidered |
| `branchFromThought` | integer | Branching point thought number |
| `branchId` | string | Branch identifier |
| `needsMoreThoughts` | boolean | If more thoughts are needed |

## Ideal Use Cases

The tool is well-suited for scenarios involving:

- Complex problem decomposition
- Planning with revision flexibility
- Analysis requiring course correction
- Tasks with initially unclear scope
- Multi-step context maintenance
- Filtering irrelevant information

## License

This MCP server is licensed under the MIT License. This means you are free to use, modify, and distribute the software, subject to the terms and conditions of the MIT License.

## Links

- [GitHub Repository](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking)
- [NPM Package](https://www.npmjs.com/package/@modelcontextprotocol/server-sequential-thinking)
