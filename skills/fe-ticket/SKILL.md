---
name: fe-ticket
description: Create a frontend implementation ticket in Notion. Use when creating a "frontend ticket", "FE ticket", "UI ticket", or "component ticket".
allowed-tools:
  - mcp__plugin_Notion_notion__*
  - mcp__plugin_figma_figma__*
  - mcp__claude-in-chrome__*
---

# Frontend Implementation Ticket

Create a structured frontend implementation ticket in Notion following Syte's established format. When a Figma design is provided, analyze it to auto-generate detailed acceptance criteria.

## Workflow

### 1. Title & Brief Description
Ask: "What's the ticket title and a brief description of what needs to be built?"

### 2. Figma URL
Ask: "Is there a Figma design for this? Please share the URL."

**If Figma URL is provided, analyze the design:**

#### Extracting Figma IDs from URL
Parse the URL to extract `fileKey` and `nodeId`:
- URL format: `https://figma.com/design/:fileKey/:fileName?node-id=:nodeId`
- Example: `https://figma.com/design/abc123/MyDesign?node-id=1-2`
  - `fileKey` = `abc123`
  - `nodeId` = `1:2` (convert `-` to `:`)

#### Analyze with Figma MCP
Use the Figma MCP tools to analyze the design:

```
1. First, get design context:
   mcp__plugin_figma_figma__get_design_context
   - fileKey: extracted from URL
   - nodeId: extracted from URL
   - clientLanguages: "typescript"
   - clientFrameworks: "react"

2. Get a screenshot for visual reference:
   mcp__plugin_figma_figma__get_screenshot
   - fileKey: extracted from URL
   - nodeId: extracted from URL
```

#### Generate Acceptance Criteria from Design
Based on the Figma analysis, identify and document in Syte's detailed style:
- **Layout & Structure**: Exact positions, sections, hierarchy
- **UI Elements**: Each button, input, label with exact behavior
- **Conditional States**: Different states and when they apply
- **Interactions**: Click, hover, keyboard behaviors
- **Copy/Text**: Exact German text to display (if visible in design)
- **Responsive**: Mobile/tablet variations if shown

Present the auto-generated acceptance criteria to the user for review before proceeding.

#### Fallback: Claude in Chrome
If Figma MCP fails or returns insufficient data:
1. Use `mcp__claude-in-chrome__navigate` to open the Figma URL
2. Use `mcp__claude-in-chrome__computer` with `action: "screenshot"` to capture the design
3. Analyze the screenshot visually to generate acceptance criteria

### 3. User Story (Optional)
Ask: "Is there a user story? Format: As a [user], I want [goal], because [reason]"

### 4. Existing Code/Prototype
Ask: "Does any existing code or prototype exist? If yes, what components or files are involved?"
- Look for `.tsx`, `.ts` component files
- If code exists, note what needs to change

### 5. Epic (Optional)
Ask: "Should this be linked to an Epic? If yes, which one?"
- Search for epics in Notion if user provides a name

### 6. Review Acceptance Criteria
If generated from Figma, present the criteria for review:
"Based on the Figma design, here are the proposed acceptance criteria. Would you like to modify anything?"

If no Figma was provided, ask for details:
"What are the detailed acceptance criteria? Include UI elements, states, and interactions."

## Creating the Ticket

Use the Notion MCP tools to create the ticket:

### Database Info
- **Data source ID**: `255aa4ba-9507-8116-8685-000bee37406c`

### Properties
- `Issue name`: The ticket title
- `Status`: "Todo"
- `Epic`: Relation to parent epic (if provided)

### Content Template (Syte Format)

```markdown
▶## Discussion
	{Leave empty - inline discussion database added manually}

## Overview
{Brief description of what needs to be built}

## User Story
{If provided:}
As a **{user type}**, I want {goal}, because {reason}

{If not provided, omit this section}

## Acceptance Criteria
1. {Main UI area or component}
	1. {Detailed requirement}
	2. {Another requirement}
		1. {Sub-detail}
		2. {Sub-detail}
2. {Another main area}
	1. {Requirement with exact behavior}
	2. Possible values/states:
		1. "{State 1}" - {description and when it applies}
		2. "{State 2}" - {description}
	3. Interaction behavior:
		1. Click: {behavior}
		2. Hover: {behavior}

▶## Implementation Details
	{Technical notes if any, otherwise leave empty}

▶## QA
	{Leave empty - inline QA database added manually}

## UX design
{Figma URL as link}

## Notes:
{Empty}
```

### Acceptance Criteria Writing Style
Follow Syte's detailed format:
- Use numbered lists (1., 2., 3.) for main items
- Use nested numbered lists (1.1, 1.2) or tabs for sub-items
- Be very specific about:
  - Exact element positions ("at the top right", "below the description")
  - Conditional logic ("if X, then Y")
  - Exact German copy in quotes ("Speichern", "Abbrechen")
  - API endpoints to use if known
  - Reference other tickets with Notion mentions if relevant
- Use toggle format (▶) for collapsible sections

## After Creation

1. Provide the Notion URL to the user
2. **Important**: Remind the user to:
   - Add Labels manually in Notion: **Frontend**, **App Team**, plus type if applicable
   - Add Discussion and QA inline databases if needed
   - Assign team members
