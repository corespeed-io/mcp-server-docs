# GitHub MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@github/github-mcp-server": {
      "url": "https://api.githubcopilot.com/mcp/"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=github&config=eyJ1cmwiOiJodHRwczovL2FwaS5naXRodWJjb3BpbG90LmNvbS9tY3AvIn0=)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=github&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.githubcopilot.com%2Fmcp%2F%22%7D) |

GitHub's official Model Context Protocol (MCP) Server that connects AI tools directly to GitHub's platform. This enables AI agents, assistants, and chatbots to read repositories and code files, manage issues and PRs, analyze code, and automate workflows through natural language interactions.

> **Note**: The GitHub MCP Server was originally part of [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) but has been moved to [github/github-mcp-server](https://github.com/github/github-mcp-server) as the official repository maintained by GitHub.

## Key Capabilities

- **Repository Management**: Browse and query code, search files, analyze commits, and understand project structure across any repository you have access to.
- **Issue & PR Automation**: Create, update, and manage issues and pull requests. Let AI help triage bugs, review code changes, and maintain project boards.
- **CI/CD & Workflow Intelligence**: Monitor GitHub Actions workflow runs, analyze build failures, manage releases, and get insights into your development pipeline.
- **Code Analysis**: Examine security findings, review Dependabot alerts, understand code patterns, and get comprehensive insights into your codebase.
- **Team Collaboration**: Access discussions, manage notifications, and analyze activity.

## Installation Options

### Remote Server (Recommended)

The easiest way to use the GitHub MCP Server. Hosted by GitHub at `https://api.githubcopilot.com/mcp/`.

**Supported Clients:**
- VS Code 1.101+
- Claude Desktop
- Cursor
- Windsurf
- Other MCP-compatible hosts

**Authentication:**
- OAuth (recommended)
- GitHub Personal Access Tokens (PATs)

### NPX Deployment

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    }
  }
}
```

### Building from Source

Requires Go to be installed:

```bash
git clone https://github.com/github/github-mcp-server.git
cd github-mcp-server
go build
```

## Configuration

### Toolsets

The server uses toolsets to organize functionality. Default toolsets include: `context`, `repos`, `issues`, `pull_requests`, and `users`.

**Available Toolsets:**
- `context` - **Strongly recommended**: Tools that provide context about the current user and GitHub context
- `repos` - Repository management tools
- `issues` - Issue management tools
- `pull_requests` - Pull request operations
- `users` - GitHub User related tools
- `actions` - GitHub Actions workflows and CI/CD operations
- `code_security` - Code security related tools (GitHub Code Scanning)
- `copilot` - Copilot-related tools (Remote server only)

Enable specific toolsets via `--toolsets` flag or `GITHUB_TOOLSETS` environment variable.

### Individual Tools

Fine-grained control available through `--tools` flag for specific tool names.

### Dynamic Tool Discovery (Beta)

Instead of starting with all tools enabled, you can turn on dynamic toolset discovery. This allows the MCP host to list and enable toolsets in response to a user prompt, helping to avoid confusion from the sheer number of available tools.

> Note: This feature is not available in the Remote GitHub MCP Server.

### Read-Only Mode

Run the server in read-only mode using the `--read-only` flag. This only offers read-only tools, preventing any modifications to repositories, issues, pull requests, etc.

## Available Tools (51 Total)

### Repository & File Operations
| Tool | Description |
|------|-------------|
| `create_repository` | Initialize new GitHub repositories |
| `create_branch` | Establish new branches |
| `create_or_update_file` | Modify or add files |
| `delete_file` | Remove files from repos |
| `push_files` | Commit multiple files at once |
| `get_file_contents` | Retrieve file/directory contents |
| `fork_repository` | Fork repositories to accounts |

### Issue Management
| Tool | Description |
|------|-------------|
| `create_issue` | Generate new issues |
| `get_issue` | Retrieve specific issue details |
| `list_issues` | Display repository issues |
| `update_issue` | Modify issue properties |
| `add_issue_comment` | Post issue comments |
| `get_issue_comments` | Fetch issue comment threads |
| `assign_copilot_to_issue` | Delegate tasks to AI assistant |

### Pull Request Operations
| Tool | Description |
|------|-------------|
| `create_pull_request` | Submit new PRs |
| `get_pull_request` | Access PR information |
| `list_pull_requests` | View repository PRs |
| `update_pull_request` | Edit PR details |
| `merge_pull_request` | Combine PR changes |
| `get_pull_request_diff` | Examine code changes |
| `get_pull_request_files` | List modified files |
| `get_pull_request_status` | Monitor PR state |
| `update_pull_request_branch` | Sync with base branch |

### Pull Request Review Tools
| Tool | Description |
|------|-------------|
| `create_pending_pull_request_review` | Start review sessions |
| `add_pull_request_review_comment_to_pending_review` | Add targeted feedback |
| `create_and_submit_pull_request_review` | Complete reviews |
| `submit_pending_pull_request_review` | Finalize pending reviews |
| `delete_pending_pull_request_review` | Cancel unpublished reviews |
| `get_pull_request_reviews` | Access review history |
| `request_copilot_review` | Request automated code analysis |

### Code & Security Scanning
| Tool | Description |
|------|-------------|
| `get_code_scanning_alert` | Retrieve specific alerts |
| `list_code_scanning_alerts` | Display security findings |
| `get_secret_scanning_alert` | Access sensitive data warnings |
| `list_secret_scanning_alerts` | Review exposed credentials |

### Commit & Version Control
| Tool | Description |
|------|-------------|
| `get_commit` | View commit metadata |
| `list_commits` | Access commit history |
| `get_tag` | Retrieve tag information |
| `list_tags` | Display all tags |

### Notification Management
| Tool | Description |
|------|-------------|
| `list_notifications` | Display pending items |
| `get_notification_details` | View notification specifics |
| `dismiss_notification` | Mark notifications |
| `manage_notification_subscription` | Control alert preferences |
| `manage_repository_notification_subscription` | Repository-specific settings |
| `mark_all_notifications_read` | Batch mark operations |

### Search Capabilities
| Tool | Description |
|------|-------------|
| `search_code` | Query code across platforms |
| `search_issues` | Find related tasks |
| `search_repositories` | Locate projects |
| `search_users` | Discover contributors |

### Authentication & User
| Tool | Description |
|------|-------------|
| `get_me` | Access authenticated profile information |

## Search Query Syntax

### Code Search
- `language:javascript` - Filter by programming language
- `repo:owner/name` - Target specific repositories
- `path:app/src` - Restrict to directory paths
- `extension:js` - Search by file type

### Issues Search
- `is:issue` or `is:pr` - Distinguish between types
- `is:open` or `is:closed` - Filter by state
- `label:bug` - Find labeled issues
- `author:username` - Search by creator

### User Search
- `type:user` or `type:org` - Account categories
- `followers:>1000` - Follower count filtering
- `location:London` - Geographic targeting

## GitHub Enterprise Support

### Enterprise Cloud (ghe.com)
Use the remote server pointing to your custom domain.

### Enterprise Server
Requires local deployment with `GITHUB_HOST` environment variable set to your Enterprise Server URL.

## Security Best Practices

- Use minimum required permission scopes
- Maintain separate tokens for different environments
- Rotate tokens periodically
- Never commit tokens to version control
- Restrict file permissions on config files (`chmod 600`)

## Resources

- **Official Repository**: [github/github-mcp-server](https://github.com/github/github-mcp-server)
- **Archived Repository**: [modelcontextprotocol/servers-archived](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/github)
- **MCP Registry**: [GitHub MCP Registry](https://github.blog/ai-and-ml/generative-ai/how-to-find-install-and-manage-mcp-servers-with-the-github-mcp-registry/)
- **MCP Protocol Documentation**: [modelcontextprotocol.io](https://modelcontextprotocol.io)

## License

Licensed under the MIT License.
