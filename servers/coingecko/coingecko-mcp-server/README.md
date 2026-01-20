# CoinGecko MCP Server

## Server Config

```json
{
  "mcpServers": {
    "@coingecko/coingecko-mcp-server": {
      "url": "https://mcp.api.coingecko.com/mcp"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=coingecko&config=eyJ1cmwiOiJodHRwczovL21jcC5hcGkuY29pbmdlY2tvLmNvbS9tY3AifQ==)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=coingecko&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.api.coingecko.com%2Fmcp%22%7D) |

The official CoinGecko MCP Server enables AI models and applications to access cryptocurrency market data through the Model Context Protocol (MCP) standard. It provides real-time pricing, onchain analytics, market trends, and historical data for over 15,000 cryptocurrencies.

> **Note:** This server is currently in Beta.

## Key Capabilities

- **Real-time market data**: Access aggregated prices, market cap, and trading volumes for 15,000+ coins across 1,000+ exchanges
- **Onchain analytics**: Query DEX price and liquidity data for 8M+ tokens across 200+ networks via GeckoTerminal
- **Market insights**: Trending coins, new listings, gainers/losers, and NFT collections
- **Rich metadata**: Project descriptions, logos, social links, and security information
- **Historical analysis**: Price charts, market data, and OHLCV candlestick data
- **Category exploration**: Filter cryptocurrencies by sectors (DeFi, Layer 1, AI agents, etc.)

## Connection Options

### 1. Remote Server (Public, Keyless)

No authentication required; suitable for testing with shared rate limits.

**Endpoints:**
- HTTP Streaming: `https://mcp.api.coingecko.com/mcp`
- SSE: `https://mcp.api.coingecko.com/sse`

### 2. Remote Server (Authenticated)

Uses your CoinGecko API key for higher, reliable rate limits.

**Endpoints:**
- HTTP Streaming: `https://mcp.pro-api.coingecko.com/mcp`
- SSE: `https://mcp.pro-api.coingecko.com/sse`

## Available Tools

The CoinGecko MCP Server provides **76+ tools** across six major categories:

1. **Real-time Pricing** - Current prices, market caps, and trading volumes
2. **Market Analytics** - Rankings, trends, and statistical analysis
3. **Historical Data** - Price charts, OHLCV data, and trend analysis
4. **Search & Discovery** - Cryptocurrency and emerging project discovery
5. **NFT Analytics** - Floor prices, volumes, and marketplace statistics
6. **DeFi & On-chain** - Pools, liquidity data, and multi-chain information

## API Tier Comparison

| Feature | Demo | Pro |
|---------|------|-----|
| Rate Limit | 30 calls/min | 500+ calls/min |
| Monthly Credits | 10,000 | 500,000+ |
| Historical Data | 1 year | 2013 to present |
| Tool Access | Limited | Full (76+ tools) |

## Tool Discovery Modes

- **Static (default)**: The AI receives a complete list of tools upfront. Faster for specific, known tasks.
- **Dynamic**: The AI queries the server for tools by keyword search. More flexible but potentially slower.

## Example Queries

**Simple:**
- "What is Bitcoin's current price in USD?"
- "Which are the top 3 trending coins right now?"

**Advanced:**
- "Show me the top 10 cryptocurrencies by market cap with 24-hour changes"
- "Generate a 30-day Ethereum price chart with volume data"

**Creative:**
- "Build a crypto personality quiz using CoinGecko data"
- "Compare the performance of DeFi tokens over the last month"

## Data Freshness

Data is updated in real-time directly from CoinGecko's live API. Price data is typically updated every few minutes, while market data refresh rates vary by endpoint.

## Documentation Links

- **Official Documentation**: https://docs.coingecko.com/docs/mcp-server
- **API Reference**: https://docs.coingecko.com/reference/mcp-server
- **MCP Server Endpoint**: https://mcp.api.coingecko.com/
- **npm Package**: https://www.npmjs.com/package/@coingecko/coingecko-mcp
- **Learn More**: https://www.coingecko.com/learn/ai-crypto-research-mcp

## Community Implementations

While the official CoinGecko MCP Server is recommended, several community implementations exist:

- [crazyrabbitLTC/mcp-coingecko-server](https://github.com/crazyrabbitLTC/mcp-coingecko-server) - Anthropic MCP server with OpenAI function compatibility
- [BlindVibeDev/CoinGeckoMCP](https://github.com/BlindVibeDev/CoinGeckoMCP) - Node.js Express server with Pro/Free API support
- [GaplyDev01/coingecko-mcp-server](https://github.com/GaplyDev01/coingecko-mcp-server) - Simplified interface to CoinGecko API
- [mason-aug/mcp-server-coingecko](https://github.com/mason-aug/mcp-server-coingecko) - MCP server with Zod parameter validation
- [Hott-J/coingecko-mcp-server](https://github.com/Hott-J/coingecko-mcp-server) - MCP Server for CoinGecko Cryptocurrency API

## Support

For feedback or support, contact the CoinGecko team through their official documentation or feedback forms.
