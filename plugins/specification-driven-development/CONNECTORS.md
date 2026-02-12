# Connectors

This plugin uses placeholder tokens (`~~connector name`) in command workflows to indicate where external data sources are needed. When a connector is available, the workflow automatically leverages it for richer context.

## Connector Reference

| Category | Placeholder | Included Servers | Other Options |
|----------|-------------|-----------------|---------------|
| Repository | `~~repository` | GitHub | GitLab, Bitbucket |
| Project tracker | `~~project tracker` | Linear, Atlassian | Asana, ClickUp |
| Knowledge base | `~~knowledge base` | Notion | Confluence, Coda |

## How Connectors Work

- **When connected:** The workflow automatically queries the connector for relevant context (codebase structure, tickets, prior specs).
- **When not connected:** The workflow falls back to asking the user for the equivalent information manually.
- **No connector is required.** Every command works without any connectors — they just produce richer output when connectors are available.

## Configuring Connectors

MCP server connections are defined in `.mcp.json` at the plugin root. Each server uses HTTP transport to connect to the provider's MCP endpoint. Refer to each provider's documentation for authentication setup.
