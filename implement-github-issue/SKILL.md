---
name: implement-github-issue
description: Fetch a GitHub issue, analyze requirements, and create a comprehensive implementation plan. Asks user for confirmation before executing. Use when user provides a GitHub issue URL/link and asks to implement, fix, solve, or work on it.
---

# Implement GitHub Issue

## When to Use

- User provides a GitHub issue URL and asks to implement/fix it
- User says "implement issue #123" or "fix this issue: [URL]"
- User asks to work on, solve, or address a GitHub issue
- User pastes an issue link and asks what needs to be done
- User requests a plan for implementing a GitHub issue

## Critical Workflow

**IMPORTANT**: This skill follows a two-phase approach:

1. **Phase A (Automatic)**: Analyze issue → Gather context → Research → Create comprehensive plan
2. **Phase B (User-Initiated)**: Only implement AFTER user reviews and approves the plan

**NEVER start implementation without explicit user confirmation.**

## Prerequisites

- The `gh` CLI must be installed and authenticated
- Current directory must be within a git repository
- WebSearch tool available for external research
- Read access to the GitHub repository

## Operating System Detection

**IMPORTANT**: Before executing shell commands, check the user's OS from the system information provided in the conversation context. Look for the `OS Version` field:
- If it contains `darwin` → **macOS** (use bash/zsh syntax)
- If it contains `windows` or `win32` → **Windows** (use PowerShell syntax)
- If it contains `linux` → **Linux** (use bash syntax)

## Instructions

### Phase 1: Issue Analysis

#### 1.1 Parse the Issue URL

Extract the issue information from the URL. Supported formats:
- `https://github.com/owner/repo/issues/123`
- `owner/repo#123`
- `#123` (assumes current repo)

#### 1.2 Fetch Issue Details

Use the `gh` CLI to retrieve full issue information:

```bash
# Get issue details in JSON format
gh issue view <issue-number> --json title,body,labels,assignees,state,comments

# For issues from a specific repo
gh issue view <issue-number> --repo owner/repo --json title,body,labels,assignees,state,comments
```

#### 1.3 Extract Requirements

From the issue, identify:
- **Type**: Bug fix, feature request, enhancement, refactor, documentation
- **Priority**: Based on labels (critical, high, medium, low)
- **Scope**: Affected components, files, or systems
- **Acceptance Criteria**: What defines "done"
- **Constraints**: Breaking changes, backward compatibility, performance requirements
- **Related Issues**: Any linked or referenced issues

### Phase 2: Project Context Gathering

#### 2.1 Review Project Documentation

Read relevant documentation to understand the project structure:

1. **Read `AGENTS.md`** (or equivalent) for:
   - Architecture overview
   - Technology stack
   - Development patterns
   - Common workflows

2. **Check existing docs** in `/docs` folder for:
   - Feature documentation
   - API references
   - Implementation guides

#### 2.2 Search for Related Code

Use codebase search tools to find relevant code:

**Semantic Search** for understanding:
```
- "How does [feature mentioned in issue] work?"
- "Where is [component] implemented?"
- "What patterns are used for [concept]?"
```

**Grep** for exact matches:
- Search for function/class names mentioned in the issue
- Find related error messages or strings
- Locate configuration values

**Glob** for file discovery:
- Find files with relevant names
- Locate test files for affected components

#### 2.3 Analyze Dependencies

Check if the issue involves:
- External libraries (check package.json, Cargo.toml, mix.exs)
- Database schema (check migrations)
- API contracts (check route definitions)
- State management (check stores)

### Phase 3: Research (If Needed)

#### 3.1 When to Research

Perform web research if the issue involves:
- Technologies or patterns not currently in the codebase
- Third-party API integrations
- Best practices for specific implementations
- Security considerations
- Performance optimization techniques

#### 3.2 Research Execution

Follow the deep-research skill pattern:

1. Include current year in search queries
2. Search at least 5-10 relevant sources:
   - Official documentation
   - Best practices guides
   - Stack Overflow discussions
   - GitHub examples
3. Document findings relevant to the implementation

### Phase 4: Create Implementation Plan

#### 4.1 Generate Plan ID

Create a unique plan identifier:
```
{snake_case_title}_{8_char_hash}.plan.md
```

Example: `fix_timeline_crash_a1b2c3d4.plan.md`

#### 4.2 Plan Document Structure

Create a comprehensive plan file in `.cursor/plans/` that serves as:
- A detailed analysis document for user review
- An implementation roadmap once approved
- A record of what was done and why

Use this structure:

```markdown
---
name: [Human-readable title from issue]
overview: [1-2 sentence summary of what will be implemented]
github_issue: [Full issue URL]
issue_type: [bug|feature|enhancement|refactor|docs]
todos:
  - id: [kebab-case-id]
    content: [Task description]
    status: pending
  - id: [another-task]
    content: [Task description]
    status: pending
---

# [Issue Title]

## Issue Summary

**GitHub Issue**: [#number](URL)
**Type**: [Bug Fix / Feature / Enhancement / etc.]
**Labels**: [list of labels]

### Description
[Summarized description from the issue body]

### Acceptance Criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

## Analysis

### Affected Components
| Component | File Path | Changes Needed |
|-----------|-----------|----------------|
| [Name] | [path/to/file.ext] | [Brief description] |

### Root Cause Analysis (for bugs)
[Explanation of why the bug occurs, with code references]

### Approach (for features)
[High-level design decisions and rationale]

### Dependencies
- [Any external dependencies needed]
- [Related issues or PRs]

## Implementation Plan

### Step 1: [First Major Step]

**Files to modify:**
- `path/to/file1.ext` - [What changes]
- `path/to/file2.ext` - [What changes]

**Code Changes:**
```[language]
// Pseudocode or actual code snippets showing the changes
```

**Verification:**
- How to test this step

### Step 2: [Second Major Step]
[Continue pattern...]

### Step 3: [Continue as needed...]

## Testing Strategy

### Manual Testing
1. [Test case 1]
2. [Test case 2]

### Automated Tests (if applicable)
- [ ] Add unit test for [component]
- [ ] Update integration test for [feature]

## Rollback Plan (for significant changes)

If issues arise:
1. [Rollback step 1]
2. [Rollback step 2]

## Research Notes (if applicable)

### Sources Consulted
- [Source 1](URL) - [Key insight]
- [Source 2](URL) - [Key insight]

### Alternative Approaches Considered
1. **[Approach 1]** - [Why not chosen]
2. **[Approach 2]** - [Why not chosen]
```

### Phase 5: Present Plan and Request Confirmation

#### 5.1 Summarize the Plan

After creating the plan document, present a summary to the user:

1. **Plan location**: Link to the `.cursor/plans/` file
2. **Issue overview**: Brief description of what will be implemented
3. **Scope summary**: Number of files affected, complexity assessment
4. **Key changes**: Bullet list of major modifications
5. **Estimated todos**: List of implementation steps

#### 5.2 Ask for Confirmation

**ALWAYS** ask the user before proceeding with implementation:

```
The implementation plan has been created at `.cursor/plans/[filename].plan.md`.

**Summary:**
- [Brief overview]
- [X files to modify]
- [Y new files to create (if any)]

**Key Changes:**
1. [Change 1]
2. [Change 2]
3. [Change 3]

Would you like me to proceed with the implementation, or would you prefer to review the plan first?
```

**Wait for user response before continuing.**

#### 5.3 Handle User Response

- **"Yes" / "Proceed" / "Implement"** → Continue to Phase 6
- **"No" / "Wait" / "Let me review"** → Stop and let user review the plan
- **User requests changes** → Update the plan accordingly, then re-confirm
- **User asks questions** → Answer questions about the plan

---

## Phase 6: Implementation (User-Initiated Only)

**IMPORTANT**: Only proceed to this phase after explicit user confirmation.

#### 6.1 Execute the Plan

Work through the implementation plan systematically:

1. **Start with the first todo item**
2. **Make focused changes** - One logical change at a time
3. **Verify each step** - Run relevant tests or manual checks
4. **Update todo status** - Mark items as completed

#### 6.2 Code Quality Checks

After each significant change:
- Run `ReadLints` to check for new linter errors
- Fix any introduced issues
- Ensure code follows project conventions (check AGENTS.md)

#### 6.3 Update the Plan

As you implement:
- Mark completed todos in the plan frontmatter
- Note any deviations or discoveries
- Update affected files list if it changes

### Phase 7: Completion

#### 7.1 Final Verification

Before marking complete:
1. All acceptance criteria met
2. No linter errors introduced
3. Related tests pass (if applicable)
4. Code follows project conventions

#### 7.2 Summary

Provide a completion summary to the user:
- What was implemented
- Key files changed
- Any notes or follow-up items
- Link to the plan document for reference

## Best Practices

### Do

- Read the ENTIRE issue including comments before planning
- Cross-reference with existing code patterns in the project
- Break large issues into small, testable increments
- Document assumptions made during implementation
- Check for existing similar implementations to follow patterns
- Use other skills when helpful (deep-research, build-fix-warnings, etc.)
- **ALWAYS ask for user confirmation before implementing**
- Present a clear, concise summary of the plan before asking to proceed

### Don't

- Start coding before fully understanding the issue
- Ignore issue comments - they often contain crucial context
- Make changes outside the scope of the issue without noting it
- Skip the planning phase for complex issues
- Implement without considering edge cases mentioned in the issue
- **NEVER start implementation without explicit user approval**
- Don't assume user wants to proceed - always ask

## Error Handling

### Issue Not Found

If `gh issue view` fails:
1. Verify the issue number/URL is correct
2. Check repository access permissions
3. Ensure `gh` CLI is authenticated (`gh auth status`)

### Insufficient Context

If the issue lacks detail:
1. Note specific questions in the plan
2. Ask user for clarification before implementing
3. Document assumptions clearly

### Blocked Dependencies

If the issue depends on other work:
1. Note the blocking items in the plan
2. Implement what's possible
3. Create todos for blocked items

## Examples

### Example 1: Bug Fix Issue

User: "Fix this issue: https://github.com/owner/repo/issues/456"

**Phase 1**: Fetch issue
```bash
gh issue view 456 --json title,body,labels,comments
```
→ Issue: "Timeline crashes when dragging segments quickly"

**Phase 2**: Search codebase
- Find Timeline.vue implementation
- Search for drag handling code
- Check existing error handling

**Phase 4**: Create plan at `.cursor/plans/timeline_drag_crash_f7e8a9b0.plan.md`

**Phase 5**: Present plan and ask:
```
The implementation plan has been created at `.cursor/plans/timeline_drag_crash_f7e8a9b0.plan.md`.

**Summary:**
- Bug fix for Timeline.vue drag handling
- 1 file to modify (Timeline.vue)

**Key Changes:**
1. Add debouncing to drag handler (300ms threshold)
2. Add collision detection guard to prevent invalid states
3. Add error boundary for graceful failure

Would you like me to proceed with the implementation?
```

**User**: "Yes, go ahead"

**Phase 6**: Implement the approved plan

### Example 2: Feature Request

User: "Implement #789"

**Phase 1**: Fetch issue
```bash
gh issue view 789 --json title,body,labels,comments
```
→ Issue: "Add dark mode support to settings"

**Phase 2-3**: Search codebase for theme handling, research Tailwind dark mode patterns

**Phase 4**: Create comprehensive plan with:
- Theme toggle component design
- CSS variable strategy
- State persistence approach

**Phase 5**: Present plan and ask:
```
The implementation plan has been created at `.cursor/plans/dark_mode_settings_c4d5e6f7.plan.md`.

**Summary:**
- New dark mode feature for settings
- 5 files to modify, 1 new file to create

**Key Changes:**
1. Create ThemeToggle.vue component
2. Add CSS variables for theme colors
3. Integrate with Pinia store for persistence
4. Update Settings.vue to include toggle

Would you like me to proceed with the implementation, or review the plan first?
```

**User**: "Let me review the plan first"

→ Stop and wait for user to review

### Example 3: Issue with Research Needed

User: "Work on https://github.com/owner/repo/issues/101"

Issue involves WebSocket reconnection improvements - a pattern not currently in the codebase.

**Phase 3**: Deep research
- Search "WebSocket reconnection best practices 2026"
- Review Phoenix channels reconnection patterns
- Document findings in plan

**Phase 4**: Plan includes research notes and chosen approach rationale

**Phase 5**: Present plan with research summary:
```
The implementation plan has been created at `.cursor/plans/websocket_reconnection_a1b2c3d4.plan.md`.

**Summary:**
- WebSocket reconnection improvements
- 2 files to modify

**Research Findings:**
- Exponential backoff is the recommended pattern
- Phoenix channels have built-in reconnection we can leverage

**Key Changes:**
1. Configure Phoenix socket with exponential backoff
2. Add connection state indicator to UI
3. Add manual reconnect button

Would you like me to proceed with the implementation?
```

## Related Skills

This skill works well with:
- **deep-research**: For issues requiring external knowledge
- **build-fix-warnings**: After implementation, clean up any warnings
- **git-commit-push**: To commit the implemented changes
- **create-documentation**: To document significant features after implementation
