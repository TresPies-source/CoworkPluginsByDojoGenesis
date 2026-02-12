# Connectors

External service integrations for the system-health plugin. Each connector maps to an MCP server defined in `.mcp.json`.

---

## Connector Categories

| Category | Placeholder | Included Server | Other Options |
|---|---|---|---|
| Repository | `~~repository` | GitHub | GitLab, Bitbucket |
| Project Tracker | `~~project tracker` | Linear | Asana, Jira, ClickUp |
| Knowledge Base | `~~knowledge base` | Notion | Confluence |

---

## How Connectors Are Used

### Repository (`~~repository`)

**Used by:** `/health-audit`, `/map-system`, `/audit-docs`, `/sync-repo`

- Clone and read repository contents for health audits
- Analyze repository structure for behavioral architecture mapping
- Cross-reference documentation against actual code
- Extract context and tech stack information

**Included:** GitHub via `https://api.githubcopilot.com/mcp/`

### Project Tracker (`~~project tracker`)

**Used by:** `/health-audit`, `/status-report`

- Create tickets directly from audit findings
- Pull sprint progress and active workstreams for status reports
- Track health improvement trends across sprints

**Included:** Linear via `https://mcp.linear.app/mcp`

### Knowledge Base (`~~knowledge base`)

**Used by:** `/audit-docs`, `/status-report`

- Cross-reference documentation stored in external knowledge bases
- Publish status reports to shared knowledge bases
- Search for existing architecture decisions and design documents

**Included:** Notion via `https://mcp.notion.com/mcp`

---

## Connector Behavior

When a command references a connector (e.g., `~~repository`):

1. **If connected:** The command uses the connector's capabilities as described above
2. **If not connected:** The command skips that integration step and continues with local-only operations

No command requires a connector to function. All commands work with local files as the primary interface. Connectors enhance the workflow but are never mandatory.

---

## Adding Alternative Connectors

To swap an included server for an alternative:

1. Update `.mcp.json` with the new server URL
2. The connector placeholder (e.g., `~~repository`) remains the same
3. Commands automatically use whichever server is configured

**Example:** Replacing Linear with Jira:

```json
{
  "mcpServers": {
    "jira": { "type": "http", "url": "https://mcp.atlassian.com/jira/mcp" }
  }
}
```

The `~~project tracker` placeholder in commands will then use Jira instead of Linear.
