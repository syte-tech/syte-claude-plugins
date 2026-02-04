---
name: be-ticket
description: Create a backend implementation ticket in Notion. Use when creating a "backend ticket", "BE ticket", "API ticket", or "service ticket".
allowed-tools:
  - mcp__plugin_Notion_notion__*
---

# Backend Implementation Ticket

Create a structured backend implementation ticket in Notion with API/service-focused sections.

## Workflow

Gather the following information through conversation:

### 1. Type
Ask: "What type of ticket is this?"
- Feature
- Bug
- Improvement

### 2. Title & Description
Ask: "What's the ticket title and a brief description of what needs to be done?"
- If a Notion feature ticket URL is provided, fetch it to understand requirements

### 3. Epic (Optional)
Ask: "Should this be linked to an Epic? If yes, which one?"
- Search for epics in Notion if user provides a name

### 4. Acceptance Criteria
Work with the user to define acceptance criteria, structured by area:
- **Database Schema**: Table structure, columns, indexes (if applicable)
- **API Endpoints**: HTTP method, path, auth/permissions, query params, request body
- **Response Object**: JSON example of the response format
- **Data Format**: Complex data structures or formats (if applicable)

Use `- [ ]` checkboxes for individual actionable items within each section.

### 5. Related Code
Ask: "Are there existing files or patterns to follow?"
- List relevant file paths in the codebase
- Note what needs to change or what patterns to follow

### 6. Out of Scope
Ask: "Is there anything explicitly out of scope for this ticket?"

## Creating the Ticket

Use the Notion MCP tools to create the ticket:

### Database Info
- **Data source ID**: `255aa4ba-9507-8116-8685-000bee37406c`

### Properties
- `Issue name`: The ticket title
- `Status`: "Todo"
- `Epic`: Relation to parent epic URL (if provided)

### Content Template

```markdown
## User Story
As a **{user type}**, I want to {action}, because {benefit}.

## Acceptance Criteria
### 1. Database Schema
```sql
{table_name}
  {column}: {type} (constraints)
  ...

Indexes:
  - {index_columns}
```

### 2. API Endpoints
**{METHOD}** `{path}`
- Auth: Requires `{permission}` permission
- Query: `{param1}`, `{param2}` (if applicable)
- Body: `{description}` (if applicable)
- Returns: {description}

### 3. Response Object
```json
{
  "field": "example_value",
  ...
}
```

### 4. {Additional sections as needed}
- [ ] {Actionable item 1}
- [ ] {Actionable item 2}

## Current State
{If existing code:}
Related files:
- `path/to/file.py` - {description}

{If no existing code:}
No existing implementation.

Pattern to follow: `{path/to/similar/implementation}`

## Out of Scope
- {Item 1}
- {Item 2}

▶## Implementation Details
{Optional technical notes, considerations, or implementation hints}

## Notes
- {Link to related frontend ticket if applicable}
- {Any other relevant context}
```

## After Creation

1. Provide the Notion URL to the user
2. **Important**: Remind the user to add Labels manually in Notion:
   - **Backend**
   - **App Team**
   - **{Type}** (Feature/Bug/Improvement)

The Labels property has API formatting issues, so labels must be added manually.
