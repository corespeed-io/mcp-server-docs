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

## Resources

- **GitHub Repository:** https://github.com/neondatabase/mcp-server-neon
- **Official Documentation:** https://neon.com/docs/ai/neon-mcp-server
- **Remote MCP Server:** https://mcp.neon.tech/

## License

MIT
