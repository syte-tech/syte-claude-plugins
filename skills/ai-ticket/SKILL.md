---
name: ai-ticket
description: Create an AI team ticket in Notion. Use when creating an "AI ticket", "ML ticket", "model ticket", or "computer vision ticket".
allowed-tools:
  - mcp__plugin_Notion_notion__*
---

# AI Team Implementation Ticket

Create a structured AI team ticket in Notion with model/ML-focused sections.

## Workflow

Gather the following information through conversation:

### 1. Type
Ask: "What type of ticket is this?"
- Feature
- Bug
- Improvement
- Model Training

### 2. Title & Description
Ask: "What's the ticket title and a brief description of what needs to be done?"

### 3. Model/System Involved
Ask: "What model or AI system is involved in this work?"

### 4. Existing Implementation
Ask: "Is there existing implementation related to this? If yes, describe the current state."
- Model names, pipeline references
- If implementation exists, describe what needs to change

### 5. Epic (Optional)
Ask: "Should this be linked to an Epic? If yes, which one?"
- Search for epics in Notion if user provides a name

### 6. Acceptance Criteria
Ask: "What are the acceptance criteria? List the requirements by model/system area."

### 7. Evaluation Metrics (Optional)
Ask: "Are there specific evaluation metrics and targets for this work?"
- Accuracy, precision, recall, latency, etc.

### 8. Out of Scope
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
### 1. {Model/System area}
- {Requirements}

## Current state
{If existing implementation:}
- Model: `{name}` - {description}
- Pipeline: `{name}` - {description}
**What needs to change:**
- {Changes}

{If no existing implementation:}
No existing implementation.

## Evaluation metrics
{If metrics provided:}
- {Metric 1}: target {value}
- {Metric 2}: target {value}

{If no metrics:}
No specific metrics defined.

## Training data
{If applicable: data requirements, sources}

{If not applicable:}
N/A

## Out of scope
{List items or "None specified"}
```

## After Creation

1. Provide the Notion URL to the user
2. **Important**: Remind the user to add Labels manually in Notion:
   - **AI Team**
   - **{Type}** (Feature/Bug/Improvement/Model Training)

The Labels property has API formatting issues, so labels must be added manually.
