---
name: release-changelog
description: Generate a user-friendly changelog between version tags and save to Notion. Use when asked to "create release notes", "changelog for version", or "what's in this release".
allowed-tools:
  - Bash
  - Read
  - mcp__plugin_Notion_notion__*
---

# Release Changelog

Generate a user-friendly changelog between version tags and save to Notion.

## Usage

Invoke with version range argument:
- `v3.33.0..v3.34.0` — Changes between two specific tags
- `v3.34.0` — Changes from previous tag to v3.34.0
- `next` or `unreleased` — Changes from latest tag to HEAD (preview of upcoming release)
- No arguments — Changes between the last two version tags

## Instructions

1. **Parse version range** from arguments:

   To find the latest tag and previous tags:
   ```bash
   git tag --sort=-version:refname | head -5
   ```

2. **Gather changes** from these repositories (relative to ~/Documents/Code/Syte/):
   - Frontend: `../syte-frontend` (or `~/Documents/Code/Syte/syte-frontend`)
   - Backend: `../syte-backend` (or `~/Documents/Code/Syte/syte-backend`)

   For each repo, run:
   ```bash
   git log <from_tag>..<to_tag> --pretty=format:"%h|%s" --merges
   ```

   Also fetch PR details with bodies using gh CLI for additional context.

3. **Filter out** (don't include in user-facing changelog):
   - Dependabot updates (chore(deps):, bump)
   - Pure version commits (just version numbers)
   - CI-only changes unless significant

4. **Categorize** each change:
   - **Improvements**: feat:, Feat/, new features, enhancements
   - **Fixes**: fix:, Fix/, bug fixes, corrections
   - **Refactoring**: refactor:, chore: (non-deps), code improvements
   - **Infrastructure**: ci:, infra:, deployment, docker, pipeline changes
   - **Security**: security fixes, vulnerability patches
   - **Documentation**: docs:, README, documentation updates

5. **Rewrite each item** into user-friendly language:
   - Use **bold** for the key feature/area name
   - Write a clear, non-technical description of the benefit
   - Focus on WHAT changed for users, not HOW it was implemented
   - **IMPORTANT**: Always write "syte" with a lowercase "s" (not "Syte")

   Example transformations:
   - "fix/profit on empty properties" → "**Profit Calculations** — Fixed errors when analyzing properties without existing buildings"
   - "feat: add flood risk filters" → "**Flood Risk Filters** — Search and filter properties by flood risk probability and water depth"
   - "Upgrade dependencies" → (skip or summarize as "Various dependency updates for stability")

6. **If Notion links found** in PR bodies, fetch the page to get:
   - User story (for better context)
   - Acceptance criteria summary
   Use this to enhance the description.

7. **Get the release date** from the git tag (use DD.MM.YYYY format):
   ```bash
   git show <tag> --pretty=format:"%ad" --date=format:"%d.%m.%Y" -s
   ```

8. **Output format** (Notion-flavored Markdown):

   For released versions:
   ```markdown
   ## vX.X.X (DD.MM.YYYY)

   ### Improvements
   - **Feature Name** — User-friendly description of the benefit

   ### Fixes
   - **Area Fixed** — What was wrong and how it's better now

   ### Refactoring
   - **Component** — Brief description (only if user-impacting)

   ### Infrastructure
   - **Change** — Description (only include significant changes)
   ```

   For `next`/`unreleased` (preview):
   ```markdown
   ## Next Release (Unreleased)
   *Changes since vX.X.X*

   ### Improvements
   ...
   ```

   Only include categories that have entries. Skip empty categories.

9. **Save to Notion**: After generating the changelog, append it to the Changelog page:
   - Page URL: https://www.notion.so/syte-real-estate/Changelog-2c8aa4ba950780489030e253be9c4258
   - Page ID: 2c8aa4ba950780489030e253be9c4258
   - Insert new version at the TOP of the page (newest first)
   - Use the notion-update-page MCP tool with insert_content_after command (after the title)
   - **Note**: Do NOT save `next`/`unreleased` changelogs to Notion — these are preview only

10. **Confirm** with user before writing to Notion. Show the draft first.

## Output

After generating, show:
- Version range covered
- Number of changes by category
- Full formatted changelog for review
- Prompt for confirmation before saving to Notion
