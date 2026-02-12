# Connectors

This plugin uses **connector placeholders** (`~~connector name`) to reference external tool categories. Each placeholder maps to one or more MCP servers that can fulfill that role.

## Connector Map

| Category | Placeholder | Included Servers | Other Options |
|----------|-------------|-----------------|---------------|
| Knowledge base | `~~knowledge base` | Notion | Confluence, Coda |
| Chat | `~~chat` | Slack | Microsoft Teams |
| Repository | `~~repository` | GitHub | GitLab, Bitbucket |
| Project tracker | `~~project tracker` | Linear | Asana, Jira |

## How Connectors Work

Commands reference connectors by placeholder name. When a connector is available, the command uses it to pull context automatically. When unavailable, the command falls back to asking the user for context conversationally.

### Examples

**`/retro` with connectors:**
- `~~project tracker` (Linear) — pulls completed tickets, velocity, burndown
- `~~chat` (Slack) — scans for notable discussions and decisions
- `~~repository` (GitHub) — pulls merged PRs and deployment history

**`/deep-research` with connectors:**
- `~~knowledge base` (Notion) — searches internal docs before external sources

**`/debug` with connectors:**
- `~~repository` (GitHub) — suggests specific code changes, uses git history for bisection

## Adding New Connectors

To add a new MCP server, update `.mcp.json` with the server configuration:

```json
{
  "mcpServers": {
    "server-name": { "type": "http", "url": "https://mcp.example.com/mcp" }
  }
}
```

Then update this file to map the new server to the appropriate connector category.
