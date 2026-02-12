# Connectors

External service integrations for the skill-forge plugin. Each connector maps to an MCP server defined in `.mcp.json`.

---

## Connector Categories

| Category | Placeholder | Included Server | Other Options |
|---|---|---|---|
| Repository | `~~repository` | GitHub | GitLab, Bitbucket |
| Knowledge Base | `~~knowledge base` | Notion | Confluence, Coda |

---

## How Connectors Are Used

### Repository (`~~repository`)

**Used by:** `/create-skill`, `/maintain-skills`, `/audit-skills`

- Commit new skills to version-controlled repositories
- Track skill changes and version history
- Store audit reports and maintenance logs alongside skills

**Included:** GitHub via `https://api.githubcopilot.com/mcp/`

### Knowledge Base (`~~knowledge base`)

**Used by:** `/process-to-skill`, `/audit-skills`

- Search for existing process documentation before creating new skills
- Store skill documentation and process examples in a shared, searchable knowledge base
- Cross-reference skills with project documentation

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

**Example:** Replacing GitHub with GitLab:

```json
{
  "mcpServers": {
    "gitlab": { "type": "http", "url": "https://mcp.gitlab.com/mcp" }
  }
}
```

The `~~repository` placeholder in commands will then use GitLab instead of GitHub.
