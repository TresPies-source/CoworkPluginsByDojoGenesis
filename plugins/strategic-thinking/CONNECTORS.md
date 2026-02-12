# Connectors

External service integrations for the strategic-thinking plugin. Each connector maps to an MCP server defined in `.mcp.json`.

---

## Connector Categories

| Category | Placeholder | Included Server | Other Options |
|---|---|---|---|
| Chat | `~~chat` | Slack | Microsoft Teams |
| Knowledge Base | `~~knowledge base` | Notion | Confluence, Coda |
| Project Tracker | `~~project tracker` | Linear | Asana, Jira, ClickUp |
| Design | `~~design` | Figma | Sketch, Miro |

---

## How Connectors Are Used

### Chat (`~~chat`)

**Used by:** `/scout`, `/strategic-workflow`

- Share strategic decision documents with team channels
- Gather asynchronous feedback on scouted routes
- Post positioning briefs for stakeholder review

**Included:** Slack via `https://mcp.slack.com/mcp`

### Knowledge Base (`~~knowledge base`)

**Used by:** `/scout`, `/position`, `/strategic-workflow`

- Search for prior strategic documents, decision records, or retrospectives
- Store strategic decision documents and positioning briefs
- Cross-reference current tensions with historical decisions

**Included:** Notion via `https://mcp.notion.com/mcp`

### Project Tracker (`~~project tracker`)

**Used by:** `/strategic-workflow`, `/surface-strategy`

- Map strategic decisions to existing work items, epics, and tickets
- Ground strategy in current project state and constraints
- Create follow-up tasks from strategic next steps

**Included:** Linear via `https://mcp.linear.app/mcp`

### Design (`~~design`)

**Used by:** `/surface-strategy`, `/strategic-workflow`

- Reference existing design files and prototypes during surface strategy
- Align surface strategy with current design direction
- Identify handoff patterns in existing design systems

**Included:** Figma via `https://mcp.figma.com/mcp`

---

## Connector Behavior

When a command references a connector (e.g., `~~knowledge base`):

1. **If connected:** The command uses the connector's capabilities as described above
2. **If not connected:** The command skips that integration step and continues with local-only operations

No command requires a connector to function. All commands work with local files as the primary interface. Connectors enhance the workflow but are never mandatory.

---

## Adding Alternative Connectors

To swap an included server for an alternative:

1. Update `.mcp.json` with the new server URL
2. The connector placeholder (e.g., `~~project tracker`) remains the same
3. Commands automatically use whichever server is configured

**Example:** Replacing Linear with Jira:

```json
{
  "mcpServers": {
    "jira": { "type": "http", "url": "https://mcp.atlassian.com/mcp" }
  }
}
```

The `~~project tracker` placeholder in commands will then use Jira instead of Linear.
