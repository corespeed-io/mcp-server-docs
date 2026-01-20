# Neon MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@neondatabase-labs/mcp-server-neon": {
      "url": "https://mcp.neon.tech/sse"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=neon&config=eyJ1cmwiOiJodHRwczovL21jcC5uZW9uLnRlY2gvc3NlIn0=)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=neon&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.neon.tech%2Fsse%22%7D) |

The **Neon MCP Server** is an open-source tool enabling natural language interaction with Neon Postgres databases. It implements the Model Context Protocol (MCP), a standardized protocol bridging LLMs and external systems.

## Key Features

- Natural language database management
- Simplified operations without direct SQL or API calls
- Accessibility for non-technical users
- Database migration support via Neon's branching

## Setup Options

### Option 1: Remote Hosted MCP Server (Preview)

Connect via OAuth without local installation:

```json
{
  "mcpServers": {
    "@neondatabase-labs/mcp-server-neon": {
      "url": "https://mcp.neon.tech/sse"
    }
  }
}
```

**Quick Setup Alternative:**
```bash
npx neonctl@latest init
```

**Manual API Key Setup:**
```json
{
  "mcpServers": {
    "Neon": {
      "url": "https://mcp.neon.tech/mcp",
      "headers": {
        "Authorization": "Bearer <$NEON_API_KEY>"
      }
    }
  }
}
```

### Option 2: Local MCP Server

```json
{
  "mcpServers": {
    "neon": {
      "command": "npx",
      "args": ["-y", "@neondatabase/mcp-server-neon", "start", "<YOUR_NEON_API_KEY>"]
    }
  }
}
```

## Read-Only Mode

Enable restricted access by unchecking "Full access" during OAuth or adding:

```json
{
  "headers": {
    "x-read-only": "true"
  }
}
```

**Available Tools in Read-Only Mode:** `list_projects`, `describe_project`, `run_sql`, `get_database_tables`, `list_slow_queries`, `search`, `fetch`, `load_resource`

## Supported Tools

### Project Management
- `list_projects` / `list_shared_projects` / `describe_project`
- `create_project` / `delete_project`
- `list_organizations`

### Branch Management
- `create_branch` / `delete_branch` / `describe_branch`
- `list_branch_computes`
- `compare_database_schema` / `reset_from_parent`

### SQL Operations
- `run_sql` / `run_sql_transaction`
- `get_database_tables` / `describe_table_schema`
- `get_connection_string`

### Migrations & Optimization
- `prepare_database_migration` / `complete_database_migration`
- `list_slow_queries` / `explain_sql_statement`
- `prepare_query_tuning` / `complete_query_tuning`

### Other
- `provision_neon_auth` / `search` / `fetch` / `load_resource`

## Troubleshooting

**Windows Command Prompt:**
```json
{
  "command": "cmd",
  "args": ["/c", "npx", "-y", "@neondatabase/mcp-server-neon", "start", "<KEY>"]
}
```

**Windows WSL:**
```json
{
  "command": "wsl",
  "args": ["npx", "-y", "@neondatabase/mcp-server-neon", "start", "<KEY>"]
}
```

## Development

Built with Bun. Uses Next.js for the remote server and publishes to npm as `@neondatabase/mcp-server-neon`.

**Local Commands:**
```bash
cd landing && bun install
bun run dev
bun run build:cli
bun run start:cli $NEON_API_KEY
bun run lint && bun run typecheck
```

## Resources

- **GitHub Repository:** https://github.com/neondatabase/mcp-server-neon
- **Official Documentation:** https://neon.com/docs/ai/neon-mcp-server
- **Remote MCP Server:** https://mcp.neon.tech/

## License

MIT
