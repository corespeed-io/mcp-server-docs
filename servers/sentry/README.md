# sentry-mcp

## Server Config

```json
{
  "mcpServers": {
    "@getsentry/sentry-mcp": {
      "url": "https://mcp.sentry.dev/mcp"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=sentry&config=eyJ1cmwiOiJodHRwczovL21jcC5zZW50cnkuZGV2L21jcCJ9)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=sentry&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.sentry.dev%2Fmcp%22%7D) |

An MCP (Model Context Protocol) server for interacting with Sentry via LLMs.

**Repository:** https://github.com/getsentry/sentry-mcp

**Production URL:** https://mcp.sentry.dev

## Overview

Sentry's MCP service is designed for human-in-the-loop coding agents. The tool selection prioritizes developer workflows and debugging use cases rather than general-purpose Sentry functionality.

This remote MCP server acts as middleware to the Sentry API, optimized for coding assistants like Cursor, Claude Code, and similar development tools.

### Key Features

- Remote hosted (preferred) or local STDIO mode
- OAuth support for authentication using your existing Sentry organization
- Streamable HTTP with graceful SSE fallback
- 16+ tool calls and prompts for comprehensive Sentry context
- Seer integration for AI-powered root cause analysis

## Getting Started

Visit the production deployment at **https://mcp.sentry.dev** for complete documentation.

### Client Configuration

**Claude Code:**

From your CLI enter:
```bash
claude mcp add --transport http sentry https://mcp.sentry.dev/mcp
```

Then access Claude Code with `claude`. Once in, you'll be prompted to authenticate with OAuth to Sentry.

**Codex:**

From your CLI, enter:
```bash
codex mcp add sentry -- npx -y mcp-remote@latest https://mcp.sentry.dev/mcp
```

**Cursor:**

Available via Cursor → Settings → Cursor Settings → MCP following the prompts to configure Sentry MCP. Cursor 1.0+ includes enhanced MCP support with OAuth and Streamable HTTP.

### Stdio vs Remote

The repository supports a stdio transport for easier adaptation to self-hosted Sentry installations.

**Important Note:** The AI-powered search tools (`search_events` and `search_issues`) require an OpenAI API key. These tools translate natural language queries into Sentry's query syntax. All other tools function normally without it.

To use stdio transport, create a Sentry User Auth Token with these scopes:
- `org:read`
- `project:read`
- `project:write`
- `team:read`
- `team:write`
- `event:write`

Launch with:
```bash
npx @sentry/mcp-server@latest --access-token=sentry-user-token
```

For self-hosted deployments, add `--host=sentry.example.com`.

**Environment variables:**
```
SENTRY_ACCESS_TOKEN=
SENTRY_HOST=              # Optional, for self-hosted
OPENAI_API_KEY=           # Required for AI search tools
```

### MCP Inspector

Test the service using the included MCP Inspector:
```bash
pnpm inspector
```

Connect to `http://localhost:5173` and authenticate. On localhost, use `http://localhost:6274` if OAuth flow issues occur.

## Local Development

### Setup Steps

1. **Create environment files:**
   ```bash
   make setup-env
   ```

2. **Create OAuth App in Sentry** (Settings → API → Applications):
   - Homepage URL: `http://localhost:5173`
   - Authorized Redirect URIs: `http://localhost:5173/oauth/callback`
   - Note Client ID and generate Client Secret

3. **Configure credentials:**
   - Add `OPENAI_API_KEY` to root `.env`
   - Add to `packages/mcp-cloudflare/.env`:
     - `SENTRY_CLIENT_ID=your_development_client_id`
     - `SENTRY_CLIENT_SECRET=your_development_client_secret`
     - `COOKIE_SECRET=my-super-secret-cookie`

4. **Start development server:**
   ```bash
   pnpm dev
   ```

### Verify

Run the server locally at `http://localhost:5173`, then enter `http://localhost:5173/mcp` in Inspector and connect. After authentication, you can list available tools.

### Tests

**Unit tests:**
```bash
pnpm test
```

**Evaluations** (requires `.env` in project root with `OPENAI_API_KEY`):
```bash
pnpm eval
```

**Manual testing:**
```bash
# Test with local dev server
pnpm -w run cli "who am I?"

# Test agent mode
pnpm -w run cli --agent "who am I?"

# Test against production
pnpm -w run cli --mcp-host=https://mcp.sentry.dev "query"

# Test stdio mode
pnpm -w run cli --access-token=TOKEN "query"
```

The CLI defaults to `http://localhost:5173`. Override with `--mcp-host` or set `MCP_URL` environment variable.

**Comprehensive testing playbooks:**
- **Stdio testing:** See `docs/testing-stdio.md` for IDEs, MCP Inspector
- **Remote testing:** See `docs/testing-remote.md` for OAuth, web UI, CLI client

## Seer Integration

The Sentry MCP Server provides seamless integration with Seer, Sentry's AI agent:
- Trigger Seer Analysis for automated root cause analysis
- Get AI-generated fix recommendations
- Monitor fix status

## Development Notes

### Automated Code Review

This repository uses automated code review tools to identify potential issues. These should be treated as helpful suggestions for discussion, not blocking requirements for merging PRs. Human code review remains essential.

### Contributor Documentation

See `CLAUDE.md` (also `AGENTS.md`) for contributor workflows and complete documentation index. The `docs/` folder contains per-topic guides and tool-integrated markdown files.

## Related Resources

- [Sentry MCP Documentation](https://docs.sentry.io/product/sentry-mcp/)
- [MCP Monitoring/Observability](https://docs.sentry.io/product/insights/ai/mcp/)
- [Python SDK MCP Integration](https://docs.sentry.io/platforms/python/integrations/mcp/)
- [Sentry MCP STDIO (legacy)](https://github.com/getsentry/sentry-mcp-stdio)

## License

See the repository for license information.
