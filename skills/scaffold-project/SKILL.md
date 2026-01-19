---
name: scaffold-project
description: Initialize a new project using official CLI scaffolding tools and install required dependencies. Does NOT implement features, layouts, or styles - only sets up the project foundation.
---

# Scaffold Project

## When to Use

- User asks to scaffold, create, or initialize a new project
- User wants to set up a project foundation with a specific framework
- User says "set up a new project", "create project structure", "initialize codebase"

## When NOT to Use

- User wants to implement features, layouts, or UI components
- User wants to add styles, themes, or design systems
- User already has a scaffolded project and wants to add functionality

## Scope

This skill **ONLY** handles:
- Running official CLI scaffolding commands
- Installing additional required dependencies
- Basic configuration adjustments (only if explicitly needed)

**This skill does NOT:**
- Implement layouts, pages, or components
- Add styles, themes, or CSS
- Create business logic or features
- Write application code beyond what the CLI generates

## Instructions

### Step 1: Gather Requirements

Determine from the user's request:
- Project type (web app, API, CLI tool, library, mobile app, etc.)
- Framework/stack preference
- Language (TypeScript, JavaScript, Python, etc.)
- Package manager preference (npm, pnpm, yarn, bun)

If critical information is missing, ask. Otherwise, proceed with reasonable defaults and note assumptions.

### Step 2: Look Up Official Scaffolding Command

**ALWAYS use official CLI scaffolding tools** - never manually create project files from scratch.

Use web search to find the current official scaffolding command:
```
"[framework] create new project CLI 2026"
"[framework] official starter command"
"[framework] getting started documentation"
```

Most modern frameworks provide CLI tools like:
- `npm create [tool]@latest`
- `npx create-[framework]@latest`
- `npx [framework]-cli new`

The official documentation will have the correct, up-to-date command and available options.

### Step 3: Execute Scaffolding

1. **Check OS** from system information for command compatibility
2. **Run the CLI command** with appropriate flags based on user requirements
3. **Follow interactive prompts** or use non-interactive flags when available
4. **Navigate into the project directory**

### Step 4: Install Additional Dependencies (If Needed)

If the user needs packages beyond what the CLI provides:
1. Look up the package to verify the correct install command
2. Install only what is explicitly needed - not "just in case" packages

### Step 5: Verify and Hand Off

1. **Verify** the dev server starts: `npm run dev` (or equivalent)
2. **Summarize** what was created and next steps

```
✓ Project scaffolded: [project-name]

Created with: [CLI tool]
Framework: [framework]

Next steps:
1. cd [project-name]
2. npm run dev

Ready for feature implementation.
```

## Rules

### Do

- Always use official CLI scaffolding tools
- Look up current documentation for correct commands
- Use `@latest` to get current versions
- Let CLI tools handle project structure and config
- Verify the dev server starts

### Don't

- Manually write package.json, tsconfig.json, etc. from scratch
- Create component files, layouts, or pages
- Add styles, themes, or CSS
- Implement any features or business logic
- Install packages that aren't immediately needed
- Restructure what the CLI generated

## Handoff

This skill **ends** when the scaffolded project's dev server runs successfully.

Hand off to other skills or manual implementation for:
- Pages and layouts
- UI components
- Features and business logic
- Styling and theming
