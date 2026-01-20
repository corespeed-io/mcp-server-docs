# Square Model Context Protocol Server (Beta)

## Server Config

```json
{
  "mcpServers": {
    "@square/square-mcp-server": {
      "url": "https://mcp.squareup.com/sse"
    }
  }
}
```

### One-Click Installation

|   IDE   |                                                                                                                                                   Install                                                                                                                                                   |
| :-----: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| Cursor  |                                                [![Install MCP Server](https://cursor.com/deeplink/mcp-install-light.svg)](https://cursor.com/en/install-mcp?name=square&config=eyJ1cmwiOiJodHRwczovL21jcC5zcXVhcmV1cC5jb20vc3NlIn0=)                                                 |
| VS Code | [![Install on VS Code](https://img.shields.io/badge/Install_on-VS_Code-0098FF?style=flat-square&logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=square&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.squareup.com%2Fsse%22%7D) |

This project follows the [Model Context Protocol](https://modelcontextprotocol.com/) standard, allowing AI assistants to interact with Square's connect API.

<a href="https://glama.ai/mcp/servers/@square/square-mcp-server">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/@square/square-mcp-server/badge" alt="Square Model Context Protocol Server MCP server" />
</a>

## Remote MCP Server

Square now offers a hosted remote MCP server at:

```
https://mcp.squareup.com/sse
```

The remote MCP is recommended as it uses OAuth authentication, allowing you to log in with your Square account directly without having to create or manage access tokens manually.

## Tool Reference

The Square MCP Server provides a streamlined set of tools for interacting with Square APIs:

| Tool | Description | Primary Use |
|------|-------------|------------|
| `get_service_info` | Discover methods available for a service | Exploration and discovery |
| `get_type_info` | Get detailed parameter requirements | Request preparation |
| `make_api_request` | Execute API calls to Square | Performing operations |

## Service Catalog

Square MCP Server provides access to Square's complete [API ecosystem](https://developer.squareup.com/reference/square). Check out the [Square API Documentation](https://developer.squareup.com/docs) for detailed information about each service:

| Service | Description |
|---------|-------------|
| `applepay` | Apple Pay integration |
| `bankaccounts` | Bank account management |
| `bookingcustomattributes` | Custom attributes for bookings |
| `bookings` | Appointment booking management |
| `cards` | Payment card management |
| `cashdrawers` | Cash drawer management |
| `catalog` | Catalog management (items, categories, etc.) |
| `checkout` | Checkout and payment processing |
| `customercustomattributes` | Custom attributes for customers |
| `customergroups` | Customer grouping |
| `customersegments` | Customer segmentation |
| `customers` | Customer management |
| `devices` | Square device management |
| `disputes` | Payment dispute handling |
| `events` | Event tracking |
| `giftcardactivities` | Gift card activity tracking |
| `giftcards` | Gift card management |
| `inventory` | Inventory tracking |
| `invoices` | Invoice management |
| `labor` | Workforce management |
| `locationcustomattributes` | Custom attributes for locations |
| `locations` | Location management |
| `loyalty` | Loyalty program management |
| `merchantcustomattributes` | Custom attributes for merchants |
| `merchants` | Merchant account management |
| `oauth` | Authentication |
| `ordercustomattributes` | Custom attributes for orders |
| `orders` | Order management |
| `payments` | Payment processing |
| `payouts` | Payout management |
| `refunds` | Refund management |
| `sites` | Website integration |
| `snippets` | Square Online Code integration |
| `subscriptions` | Subscription management |
| `team` | Staff management |
| `terminal` | Square Terminal management |
| `vendors` | Supplier management |
| `webhooksubscriptions` | Event notifications |

## Usage Pattern

For optimal interaction with the Square API through MCP:

1. **Discover**: Use `get_service_info` to explore available methods
   ```
   get_service_info(service: "catalog")
   ```

2. **Understand**: Use `get_type_info` to learn parameter requirements
   ```
   get_type_info(service: "catalog", method: "list")
   ```

3. **Execute**: Use `make_api_request` to perform the operation
   ```
   make_api_request(service: "catalog", method: "list", request: {})
   ```

## Contributing

This repository is auto-generated from Square's OpenAPI Specification. While contributions are welcome, please note that changes will need to be incorporated into the generator that produces this code. Please open an issue to discuss proposed changes before submitting a pull request.
