---
name: data-ticket
description: Create a data team ticket in Notion. Use when creating a "data ticket", "pipeline ticket", "ETL ticket", or "data quality ticket".
allowed-tools:
  - mcp__plugin_Notion_notion__*
---

# Data Team Implementation Ticket

Create a structured data team ticket in Notion with pipeline/ETL-focused sections.

## Workflow

Gather the following information through conversation:

### 1. Type
Ask: "What type of ticket is this?"
- Feature
- Bug
- Improvement
- Data Quality

### 2. Title & Description
Ask: "What's the ticket title and a brief description of what needs to be done?"

### 3. Data Sources Involved
Ask: "What data sources are involved in this work?"
- List databases, APIs, files, etc.

### 4. Existing Pipelines
Ask: "Are there existing pipelines related to this? If yes, describe the current state."
- Pipeline names, table references
- If pipelines exist, describe what needs to change

### 5. Epic (Optional)
Ask: "Should this be linked to an Epic? If yes, which one?"
- Search for epics in Notion if user provides a name

### 6. Acceptance Criteria
Ask: "What are the acceptance criteria? List the requirements by data/pipeline area."

### 7. Out of Scope
Ask: "Is there anything explicitly out of scope for this ticket?"

## Creating the Ticket

Use the Notion MCP tools to create the ticket:

### Database Info
- **Data source ID**: `255aa4ba-9507-8116-8685-000bee37406c`

### Properties
- `Issue name`: The ticket title
- `Status`: "Todo"
- `Epic`: Relation to parent epic (if provided)

### Content Template

```markdown
## Acceptance criteria
### 1. {Data/Pipeline area}
- {Requirements}

## Current state
{If existing pipelines:}
- Pipeline: `{name}` - {description}
- Tables: `{schema.table}` - {description}
**What needs to change:**
- {Changes}

{If no existing pipelines:}
No existing implementation.

## Data sources
- {Source 1}: {description}
- {Source 2}: {description}

## Validation & quality checks
- {Check 1}
- {Check 2}

## Out of scope
{List items or "None specified"}
```

## After Creation

1. Provide the Notion URL to the user
2. **Important**: Remind the user to add Labels manually in Notion:
   - **Data Team**
   - **{Type}** (Feature/Bug/Improvement/Data Quality)

The Labels property has API formatting issues, so labels must be added manually.
