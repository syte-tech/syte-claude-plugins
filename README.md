# syte Claude Code Plugins

Official Claude Code plugins for the syte team.

## Installation

### 1. Add the marketplace

```
/plugin marketplace add syte-tech/syte-claude-plugins
```

### 2. Install the tickets plugin

```
/plugin install syte-tickets@syte-marketplace
```

## Available Skills

| Skill | Command | Description | Required Tools |
|-------|---------|-------------|----------------|
| Frontend Ticket | `/syte-tickets:fe-ticket` | Create frontend implementation tickets with Figma integration | Notion MCP, Figma MCP (optional) |
| Backend Ticket | `/syte-tickets:be-ticket` | Create backend/API tickets with schema templates | Notion MCP |
| AI Ticket | `/syte-tickets:ai-ticket` | Create AI/ML team tickets with metrics tracking | Notion MCP |
| Data Ticket | `/syte-tickets:data-ticket` | Create data pipeline tickets with validation sections | Notion MCP |

## Prerequisites

- **Claude Code** with Notion MCP configured
- **Access** to the syte Notion workspace
- **Figma MCP** (optional) - for automatic design analysis in frontend tickets

## Usage Examples

### Create a Frontend Ticket

```
/syte-tickets:fe-ticket
```

Claude will guide you through:
1. Ticket title and description
2. Figma URL (optional - auto-generates acceptance criteria from design)
3. User story
4. Existing code references
5. Epic linking
6. Review and create

### Create a Backend Ticket

```
/syte-tickets:be-ticket
```

Claude will guide you through:
1. Ticket type (Feature/Bug/Improvement)
2. Title and description
3. Epic linking
4. Acceptance criteria (Database, API, Response format)
5. Related code patterns
6. Out of scope items

### Create an AI Ticket

```
/syte-tickets:ai-ticket
```

Claude will guide you through:
1. Ticket type (Feature/Bug/Improvement/Model Training)
2. Model/system involved
3. Existing implementation state
4. Acceptance criteria
5. Evaluation metrics and targets
6. Training data requirements

### Create a Data Ticket

```
/syte-tickets:data-ticket
```

Claude will guide you through:
1. Ticket type (Feature/Bug/Improvement/Data Quality)
2. Data sources involved
3. Existing pipelines
4. Acceptance criteria
5. Validation and quality checks

## Tool Restrictions

Each skill has `allowed-tools` configured to limit which tools Claude can use:

| Skill | Allowed Tools |
|-------|---------------|
| `fe-ticket` | `mcp__plugin_Notion_notion__*`, `mcp__plugin_figma_figma__*`, `mcp__claude-in-chrome__*` |
| `be-ticket` | `mcp__plugin_Notion_notion__*` |
| `ai-ticket` | `mcp__plugin_Notion_notion__*` |
| `data-ticket` | `mcp__plugin_Notion_notion__*` |

## Notes

- All tickets are created in the syte Notion Tasks database
- **Labels must be added manually** in Notion after creation (API limitation)
- Skills use the Notion MCP for database operations
- Frontend tickets can use Figma MCP for design analysis

## Updating

To get the latest version:

```
/plugin marketplace update
/plugin update syte-tickets@syte-marketplace
```

## Contributing

To add new skills or modify existing ones:

1. Clone this repository
2. Add/edit skills in the `skills/` directory
3. Test locally with `claude --plugin-dir ./syte-claude-plugins`
4. Submit a PR

## License

Internal syte use only.
