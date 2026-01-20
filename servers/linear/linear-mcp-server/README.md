# Linear MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@linear/linear-mcp-server": {
      "url": "https://mcp.linear.app/sse"
    }
  }
}
```

A Model Context Protocol (MCP) server that provides a standardized interface for AI models and agents to securely access and interact with Linear data.

## Overview

Linear's official MCP server enables AI assistants to search, create, and update Linear issues, projects, and comments. The server is centrally hosted and managed by Linear, following the authenticated remote MCP specification.

## Features

The Linear MCP server provides tools for:

- **Issues**: Find, create, and update issues with customizable properties (title, description, team, assignee, priority, labels, status)
- **Projects**: List, retrieve, create, and update projects
- **Comments**: List and create comments on issues
- **Teams**: List and retrieve team information
- **Users**: List and retrieve user details
- **Documents**: List, retrieve, create, and update documents
- **Cycles**: Retrieve cycle information for teams
- **Labels**: List and manage issue and project labels

## Authentication

The MCP server supports multiple authentication methods:

- **OAuth 2.1 with dynamic client registration** (primary method)
- **Direct token authentication** via `Authorization: Bearer <token>` header
- Supports API keys, OAuth tokens, and app user authentication
- No interactive authentication needed when using tokens directly

## Endpoints

| Transport | URL |
|-----------|-----|
| HTTP (Streamable) | `https://mcp.linear.app/mcp` |
| SSE (Server-Sent Events) | `https://mcp.linear.app/sse` |

## Setup Instructions

### Claude Desktop (Free/Pro)

Add the following to your Claude Desktop configuration file (`~/Library/Application Support/Claude/claude_desktop_config.json` on macOS):

```json
{
  "mcpServers": {
    "@linear/linear-mcp-server": {
      "url": "https://mcp.linear.app/sse"
    }
  }
}
```

### Claude Code

Run the following command:

```bash
claude mcp add --transport http linear-server https://mcp.linear.app/mcp
```

### Visual Studio Code

Add to your VS Code MCP configuration:

```json
{
  "mcpServers": {
    "@linear/linear-mcp-server": {
      "url": "https://mcp.linear.app/sse"
    }
  }
}
```

### Cursor

One-click installation is available via Cursor's MCP tools directory or dedicated deeplink.

### Windsurf / Zed / Other MCP Clients

Use the same configuration pattern:

```json
{
  "mcpServers": {
    "@linear/linear-mcp-server": {
      "url": "https://mcp.linear.app/sse"
    }
  }
}
```

### OpenAI Codex

```bash
codex mcp add linear --url https://mcp.linear.app/mcp
```

## Available Tools

### Issue Management

- `list_issues` - List issues with flexible filtering (team, assignee, status, labels, priority, cycle, project)
- `get_issue` - Retrieve detailed information about a specific issue including attachments and git branch name
- `create_issue` - Create new issues with customizable properties
- `update_issue` - Update existing issues (title, description, status, assignee, priority, labels, etc.)

### Comments

- `list_comments` - List comments for a specific issue
- `create_comment` - Add comments to issues with markdown support

### Projects

- `list_projects` - List projects with filtering options
- `get_project` - Retrieve project details
- `create_project` - Create new projects
- `update_project` - Update existing projects

### Teams

- `list_teams` - List teams in the workspace
- `get_team` - Retrieve team details

### Users

- `list_users` - List users in the workspace
- `get_user` - Retrieve user details (supports "me" for current user)

### Documents

- `list_documents` - List documents in the workspace
- `get_document` - Retrieve document by ID or slug
- `create_document` - Create new documents
- `update_document` - Update existing documents

### Cycles

- `list_cycles` - Retrieve cycles for a team (current, previous, next, or all)

### Labels

- `list_issue_labels` - List available issue labels
- `create_issue_label` - Create new issue labels
- `list_issue_statuses` - List available issue statuses for a team
- `list_project_labels` - List available project labels

### Documentation

- `search_documentation` - Search Linear's documentation for features and usage information

## Example Usage

### Find high-priority issues assigned to you

Ask your AI assistant: "Show me my high-priority Linear issues"

### Create a bug report

Ask your AI assistant: "Create a Linear issue for a bug where the login button is not responding on mobile devices"

### Update issue status

Ask your AI assistant: "Move issue LIN-123 to In Progress"

### Search for issues

Ask your AI assistant: "Find all issues in the Backend team that are blocked"

## Troubleshooting

### Clear Authentication Cache

If you experience authentication issues, clear the MCP authentication cache:

```bash
rm -rf ~/.mcp-auth
```

### WSL Users

Windows Subsystem for Linux users should use the SSE endpoint with the `--transport sse-only` flag:

```bash
claude mcp add --transport sse-only linear-server https://mcp.linear.app/sse
```

## Resources

- [Official Linear MCP Documentation](https://linear.app/docs/mcp)
- [Linear API Documentation](https://developers.linear.app/docs)
- [Model Context Protocol Specification](https://modelcontextprotocol.io)

## License

The Linear MCP server is provided and maintained by Linear. Usage is subject to Linear's terms of service.

---

**Note**: This documentation covers Linear's official MCP server. Community-built alternatives exist but are deprecated in favor of the official implementation.
