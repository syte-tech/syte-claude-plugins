---
name: update-changelog
description: Update the CHANGELOG.md file with recent commits from main branch in Linear-inspired format. Use when asked to "update changelog", "add to changelog", or "document recent changes".
allowed-tools:
  - Bash
  - Read
  - Edit
---

# Update Changelog

Update the CHANGELOG.md file with recent commits from the main branch in Linear-inspired format.

## Instructions

1. **Read the current CHANGELOG.md** to find the most recent date entry

2. **Fetch commits since that date** using:
   ```bash
   git log main --since="[LAST_DATE]" --format="%h|%s|%ai|%an"
   ```

3. **Analyze and group commits**:
   - Group related commits by feature/theme
   - Identify commit types from prefixes (feat:, fix:, refactor:, test:, etc.)
   - Merge similar commits into coherent entries

4. **Format in Linear style**:
   - Use reverse chronological order (newest first)
   - Create date headers (e.g., "## November 15, 2025")
   - Add feature-focused section titles (e.g., "### Custom Data Import Feature")
   - Start each section with brief user-facing description
   - Add horizontal dividers (---) between dates

5. **Categorize changes**:
   - **Improvements**: New features and enhancements (feat: commits)
   - **Fixes**: Bug fixes and corrections (fix: commits)
   - **Refactoring**: Code improvements (refactor: commits)
   - **Tests**: Test additions (test: commits)
   - **Infrastructure**: Build, CI/CD, tooling (chore:, ci:, build: commits)
   - **Security**: Security fixes (security:, sec: commits)
   - **Documentation**: Documentation updates (docs: commits)

6. **Writing style**:
   - Focus on USER VALUE first, technical details second
   - Use active voice (e.g., "Add" not "Added")
   - **Bold** key features and important words
   - Be concise but descriptive
   - Example: "**Custom Data Import**: Import custom columns (e.g., selling prices) via Excel template"

7. **Update CHANGELOG.md**:
   - Insert new entries at the TOP (after the "# Changelog" header and intro line)
   - Keep the Legend section at the bottom
   - Maintain existing formatting

8. **Verify**:
   - Dates are in correct order (newest to oldest)
   - All categories used appropriately
   - User-focused language throughout
   - No duplicate entries

## Example Entry Format

```markdown
## November 15, 2025

### Feature Title

Brief description of what users can now do with this feature.

**Improvements**
- **Bold Key Feature**: Description focusing on user value
- Another improvement with relevant technical details

**Fixes**
- Bug fix description
- Another fix

**Tests**
- Test coverage additions

---
```

## Output

After updating, show:
- Summary of commits processed
- Date range covered
- Number of entries added
- Preview of the top 3 new entries
