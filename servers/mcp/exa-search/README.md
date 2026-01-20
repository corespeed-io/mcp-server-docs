# Exa MCP Server

## Server Config

```json
{
  "mcpServers": {
    "exa": {
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/exa-search"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=exa&config=eyJ1cmwiOiJodHRwczovL2dhdGV3YXkubWNwLmNvcmVzcGVlZC5pby9tY3AtZ2F0ZXdheS9leGEtc2VhcmNoIn0=)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=exa&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fgateway.mcp.corespeed.io%2Fmcp-gateway%2Fexa-search%22%7D) |

## Exa Code: fast, efficient web context for coding agents

Vibe coding should never have a bad vibe. `exa-code` is a huge step towards coding agents that never hallucinate.

When your coding agent makes a search query, `exa-code` searches over billions of Github repos, docs pages, Stackoverflow posts, and more, to find the perfect, token-efficient context that the agent needs to code correctly. It's powered by the Exa search engine.

Examples of queries you can make with `exa-code`:
- use Exa search in python and make sure content is always livecrawled
- use correct syntax for vercel ai sdk to call gpt-5 nano asking it how are you
- how to set up a reproducible Nix Rust development environment

**Works with Cursor and Claude Code!** Use the HTTP-based configuration format:

```json
{
  "mcpServers": {
    "exa": {
      "type": "http",
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/exa-search",
      "headers": {}
    }
  }
}
```

You can enable specific tool(s) using the `tools` parameter (if multiple, then with a comma-separated list):

```
https://gateway.mcp.corespeed.io/mcp-gateway/exa-search?tools=web_search_exa,get_code_context_exa
```

Or enable all tools:

```
https://gateway.mcp.corespeed.io/mcp-gateway/exa-search?tools=web_search_exa,deep_search_exa,get_code_context_exa,crawling_exa,company_research_exa,linkedin_search_exa,deep_researcher_start,deep_researcher_check
```

You may include your exa api key in the url like this:

```
https://gateway.mcp.corespeed.io/mcp-gateway/exa-search?exaApiKey=YOUREXAKEY
```

**Note:** By default, only `web_search_exa` and `get_code_context_exa` are enabled. Add other tools as needed using the `tools` parameter.

---

A Model Context Protocol (MCP) server that connects AI assistants like Claude to Exa AI's search capabilities, including web search, research tools, and our new code search feature.

## Remote Exa MCP

Connect directly to Exa's hosted MCP server (instead of running it locally).

### Remote Exa MCP URL

```
https://gateway.mcp.corespeed.io/mcp-gateway/exa-search
```

### Cursor and Claude Code Configuration for Remote MCP

For Cursor and Claude Code, use this HTTP-based configuration format:

```json
{
  "mcpServers": {
    "exa": {
      "type": "http",
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/exa-search",
      "headers": {}
    }
  }
}
```

## Available Tools & Tool Selection

The Exa MCP server includes powerful tools for developers and researchers:

#### Tools

- **get_code_context_exa**: Search and get relevant code snippets, examples, and documentation from open source libraries, GitHub repositories, and programming frameworks. Perfect for finding up-to-date code documentation, implementation examples, API usage patterns, and best practices from real codebases.
- **web_search_exa**: Performs real-time web searches with optimized results and content extraction.
- **deep_search_exa**: Deep web search with smart query expansion and high-quality summaries for each result.
- **company_research**: Comprehensive company research tool that crawls company websites to gather detailed information about businesses.
- **crawling**: Extracts content from specific URLs, useful for reading articles, PDFs, or any web page when you have the exact URL.
- **linkedin_search**: Search LinkedIn for companies and people using Exa AI. Simply include company names, person names, or specific LinkedIn URLs in your query.
- **deep_researcher_start**: Start a smart AI researcher for complex questions. The AI will search the web, read many sources, and think deeply about your question to create a detailed research report.
- **deep_researcher_check**: Check if your research is ready and get the results. Use this after starting a research task to see if it's done and get your comprehensive report.

**Note:** By default, only `web_search_exa` and `get_code_context_exa` are enabled. You can enable additional tools using the `tools=` parameter in the URL (see examples in the Server Config section above).

---

Built with love by team Exa
