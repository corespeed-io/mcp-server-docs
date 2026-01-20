# Peek Remote MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@mcp/peek-com": {
      "url": "https://gateway.mcp.corespeed.io/mcp-gateway/peek-com"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=peek-com&config=eyJ1cmwiOiJodHRwczovL2dhdGV3YXkubWNwLmNvcmVzcGVlZC5pby9tY3AtZ2F0ZXdheS9wZWVrLWNvbSJ9)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=peek-com&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fgateway.mcp.corespeed.io%2Fmcp-gateway%2Fpeek-com%22%7D) |

The Travel Industry's First Remote MCP Server for AI Assistants.

The **Peek Remote MCP Server** is a free service that makes your AI assistant smarter by giving it access to thousands of travel experiences with real-time availability and pricing. It allows AI models to go beyond static training data to provide up-to-date descriptions, seasonal availability, and current booking options for a better trip-planning experience.

## 🚀 Connection URL

To connect your AI assistant, use the following endpoint:
`https://gateway.mcp.corespeed.io/mcp-gateway/peek-com`

---

## 🛠 Setup Instructions

### ChatGPT (OpenAI)
1. Open **ChatGPT** and go to **Settings** → **Beta Features**.
2. Enable **"Model Context Protocol (MCP)"**.
3. Add the server URL: `https://gateway.mcp.corespeed.io/mcp-gateway/peek-com`
4. Start asking ChatGPT to help plan your trips!

*Note: MCP support in ChatGPT is currently in beta and may require a ChatGPT Plus subscription.*

### Claude (Anthropic)
1. Open the **Claude Desktop app** and go to **Settings**.
2. Navigate to the **"Developer"** or **"MCP Servers"** section.
3. Add the new server: `https://gateway.mcp.corespeed.io/mcp-gateway/peek-com`
4. **Restart** Claude Desktop to activate the connection.
5. Start asking Claude to help plan your trips!

*Note: MCP support requires the Claude Desktop app. Remote MCP servers may require a Claude Pro subscription.*

---

## 💡 Example Prompts

Once connected, you can ask your AI assistant sophisticated questions such as:

* "What are the best family-friendly activities for this weekend in the larger Seattle area?"
* "Help me find 3-4 activities I can do over the course of 6 hours that are within 2 miles of each other in downtown San Francisco."
* "Create a table comparing and contrasting 5 food tours in Rome, including duration, price, and what's included."
* "I have $200 and 4 hours in Tokyo. Find me the most unique cultural experiences that fit my budget and time constraints."
* "What are the pros and cons of different whale watching tours in Monterey Bay? Include pricing, duration, and success rates."

---

## 🤖 Supported AI Assistants

| Assistant | Remote MCP Support? | How to Connect |
| :--- | :--- | :--- |
| **Claude (Anthropic)** | Yes | Add "Custom Connectors" (remote MCP servers) in Claude on web/desktop. |
| **ChatGPT (OpenAI)** | Yes | Via Custom Connectors / Deep Research in ChatGPT, and via the OpenAI API. |
| **Gemini (Google)** | Partial | Gemini CLI and SDKs can connect to remote MCP servers (OAuth, SSE/HTTP). |
| **Microsoft Copilot** | Partial | Copilot Studio can add MCP tools; VS Code and Visual Studio support MCP clients. |
| **Perplexity** | Coming Soon | Local MCP in the Mac app is live; remote MCP is rolling out to paid users soon. |
| **xAI Grok** | No | No official client support yet (community wrappers only). |

---

## 🔒 Privacy First

Peek's MCP Server is designed with privacy in mind:
* **Zero personal data collection:** The server does not collect or store any personal information shared with your AI assistant.
* **Focused Data:** It is strictly designed to answer requests regarding experience listings, availability, and pricing in an AI-friendly format.

## 📖 About MCP

**MCP (Model Context Protocol)** is an industry-standard protocol originally introduced by Anthropic in November 2024. It allows AI assistants to securely connect to external data sources and tools, providing them with real-time "context" to deliver more accurate and useful responses.

---

© 2026 Peek Travel Inc. All rights reserved.