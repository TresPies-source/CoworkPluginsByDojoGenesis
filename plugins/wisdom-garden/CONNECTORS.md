# Connectors

External service integrations for the wisdom-garden plugin. Each connector maps to an MCP server defined in `.mcp.json`.

---

## Connector Categories

| Category | Placeholder | Included Server | Other Options |
|---|---|---|---|
| Knowledge Base | `~~knowledge base` | Notion | Confluence, Obsidian, Coda |
| Chat | `~~chat` | Slack | Microsoft Teams, Discord |

---

## How Connectors Are Used

### Knowledge Base (`~~knowledge base`)

**Used by:** `/plant`, `/harvest`, `/compress`

- Search for existing seeds with similar patterns before planting new ones
- Browse and curate wisdom artifacts across the garden
- Cultivate compression artifacts in a shared, searchable knowledge base

**Included:** Notion via `https://mcp.notion.com/mcp`

### Chat (`~~chat`)

**Used by:** `/compress`, `/tend`

- Pull recent conversation threads for compression into wisdom artifacts
- Surface today's activity to pre-fill daily notes

**Included:** Slack via `https://mcp.slack.com/mcp`

---

## Connector Behavior

When a command references a connector (e.g., `~~knowledge base`):

1. **If connected:** The command uses the connector's capabilities as described above
2. **If not connected:** The command skips that integration step and continues with local-only operations

No command requires a connector to function. All commands work with local files as the primary interface. Connectors enrich the workflow but are never mandatory.

---

## Adding Alternative Connectors

To swap an included server for an alternative:

1. Update `.mcp.json` with the new server URL
2. The connector placeholder (e.g., `~~knowledge base`) remains the same
3. Commands automatically use whichever server is configured

**Example:** Replacing Notion with Confluence:

```json
{
  "mcpServers": {
    "confluence": { "type": "http", "url": "https://mcp.confluence.com/mcp" }
  }
}
```

The `~~knowledge base` placeholder in commands will then use Confluence instead of Notion.
