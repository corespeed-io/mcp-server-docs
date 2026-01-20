# Supabase MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@supabase/supabase": {
      "url": "https://mcp.supabase.com/mcp",
      "headers": {
        "Authorization": "Bearer <SUPABASE_ACCESS_TOKEN>"
      }
    }
  }
}
```

> **Note:** Replace `<SUPABASE_ACCESS_TOKEN>` with your Supabase personal access token. Generate one at `/dashboard/account/tokens` in your Supabase dashboard. For interactive use, you can omit the headers to use OAuth authentication instead.

Connect Supabase to your AI assistants through the Model Context Protocol (MCP) standard.

**Repository**: [https://github.com/supabase-community/supabase-mcp](https://github.com/supabase-community/supabase-mcp)

**Official Documentation**: [https://supabase.com/docs/guides/getting-started/mcp](https://supabase.com/docs/guides/getting-started/mcp)

## Overview

The Supabase MCP Server enables developers to integrate their Supabase projects with AI assistants like Cursor, Claude, and Windsurf. It connects AI assistants directly with your Supabase project and allows them to perform tasks like managing tables, fetching config, and querying data.

## Setup Instructions

### Configuration

MCP clients require this basic configuration:

```json
{
  "mcpServers": {
    "@supabase/supabase": {
      "url": "https://mcp.supabase.com/mcp"
    }
  }
}
```

### Deployment Options

| Option | Endpoint | Notes |
|--------|----------|-------|
| **Cloud Hosted** | `https://mcp.supabase.com/mcp` | Standard endpoint |
| **Local Development** | `http://localhost:54321/mcp` | When using Supabase CLI (limited tool subset, no OAuth) |
| **Self-Hosted** | Requires specific configuration | For self-hosted Supabase instances |

### Authentication

Previously Supabase MCP required a personal access token (PAT), but this is no longer required. Your MCP client automatically redirects you to log in to Supabase during setup. This opens a browser window where you can log in to your Supabase account and grant access to the MCP client.

#### Manual Authentication (CI Environment)

For continuous integration workflows without browser-based OAuth:

1. Generate a personal access token at `/dashboard/account/tokens`
2. Pass token via Authorization header in MCP configuration
3. Set environment variables for `SUPABASE_ACCESS_TOKEN` and `SUPABASE_PROJECT_REF`

## Configuration Options

Three query parameters customize server behavior:

| Parameter | Purpose | Example |
|-----------|---------|---------|
| `project_ref` | Scope to specific project | `?project_ref=abc123` |
| `read_only` | Restrict to read operations | `?read_only=true` |
| `features` | Enable specific tool groups | `?features=database,docs` |

### Project Scoping

Restricting access to a single project prevents LLM access to all projects in an organization. Find your Project ID in Supabase project settings.

### Read-Only Mode

This mode prevents write operations on any of your databases by executing SQL as a read-only Postgres user. Disabled mutating tools include migrations, project management, edge function deployment, and storage configuration.

### Feature Groups

Available tool categories:
- `account` - Account and project management
- `docs` - Documentation search
- `database` - Database operations
- `debugging` - Logs and advisors
- `development` - Development utilities
- `functions` - Edge Functions
- `storage` - Storage management
- `branching` - Database branching

Default includes all except storage.

## Available Tools

### Account Management
- `list_projects` / `get_project` / `create_project`
- `pause_project` / `restore_project`
- `list_organizations` / `get_organization`
- `get_cost` / `confirm_cost`

(Unavailable when project-scoped)

### Knowledge Base
- `search_docs`: Searches official Supabase documentation

### Database Operations
- `list_tables` / `list_extensions` / `list_migrations`
- `apply_migration`: Tracks schema changes
- `execute_sql`: Executes queries

### Debugging
- `get_logs`: Access service logs
- `get_advisors`: Security and performance notices

### Development
- `get_project_url`: API endpoint information
- `get_publishable_keys`: Client-safe authentication keys
- `generate_typescript_types`: Schema-based type generation

### Edge Functions
- `list_edge_functions` / `get_edge_function`
- `deploy_edge_function`

### Branching (Paid Plans)
- `create_branch` / `list_branches` / `delete_branch`
- `merge_branch` / `reset_branch` / `rebase_branch`

### Storage (Disabled by Default)
- `list_storage_buckets` / `get_storage_config`
- `update_storage_config`

## Security Considerations

### Primary Risk: Prompt Injection

Malicious actors may embed commands within data that language models retrieve. The documented example shows a support ticket containing injected SQL instructions that could expose sensitive information if a developer queries it through the MCP interface.

### Mitigation Strategies

**Operational Practices**:
- Reserve for development environments only
- Never distribute to end users
- Maintain manual approval for tool execution

**Technical Controls**:
- Enable read-only mode for production data access
- Scope servers to individual projects
- Use database branching for isolated testing
- Limit tool availability through feature configuration

### Security Best Practices

- **Don't connect to production** - Use the MCP server with a development project, not production. LLMs are great at helping design and test applications, so leverage them in a safe environment without exposing real data.
- **Read-only mode** - If you must connect to real data, set the server to read-only mode, which executes all queries as a read-only Postgres user.
- **Project scoping** - Scope your MCP server to a specific project, limiting access to only that project's resources.

## Compatible AI Tools

The MCP Server works with popular AI tools:
- Cursor
- Claude
- Windsurf
- Visual Studio Code (CoPilot)
- Cline

More tools will be supported as they adopt the MCP standard.

## Project Information

- **License**: Apache 2.0
- **Repository**: [supabase-community/supabase-mcp](https://github.com/supabase-community/supabase-mcp)
- **Status**: Pre-1.0 (breaking changes possible between versions)

## Resources

- [Model Context Protocol](https://modelcontextprotocol.io/introduction) - Protocol specification
- [Official Setup Documentation](https://supabase.com/docs/guides/getting-started/mcp)
- [MCP Registry](https://registry.modelcontextprotocol.io/)
- [MCP Authentication Guide](https://supabase.com/docs/guides/auth/oauth-server/mcp-authentication)
- [Deploy MCP Servers](https://supabase.com/docs/guides/getting-started/byo-mcp)
- [Building MCP with mcp-lite](https://supabase.com/docs/guides/functions/examples/mcp-server-mcp-lite)
