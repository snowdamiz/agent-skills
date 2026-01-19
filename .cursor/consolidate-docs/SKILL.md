---
name: consolidate-docs
description: Search project for all MD files and consolidate important information into the root README.md. Use when user asks to update, consolidate, sync, or refresh project documentation.
---

# Consolidate Documentation

## When to Use
- User asks to update/consolidate/sync the README
- User wants to combine documentation
- User asks to refresh project documentation
- User asks to create a documentation index

## Scripts

This skill includes a helper script for discovering MD files with their timestamps:

```bash
node .cursor/consolidate-docs/scripts/check-md-dates.mjs [directory]
```

**Output**: JSON with all MD files sorted by modification date (newest first), including:
- `path`: Relative file path
- `modified`: Last modification timestamp (ISO format)
- `created`: Creation timestamp (ISO format)  
- `age_days`: Days since last modification
- `summary`: Quick reference to newest/oldest files

## Instructions

1. **Run the date checker script first**:
   ```bash
   node .cursor/consolidate-docs/scripts/check-md-dates.mjs .
   ```
   This provides all MD files with timestamps, pre-sorted by recency, with common exclusions filtered out (node_modules, dist, build, .git).

2. **Categorize files from script output**:
   - **Include**: Root-level markdown files, component/package READMEs, documentation folders
   - **Exclude**: Generated files, plan documents, temporary files
   - Adapt to the project's specific documentation structure

3. **Handle conflicting information** (TIME-AWARE):
   - Use the `modified` timestamp from script output to determine document age
   - ALWAYS favor information from the most recently modified document (lower `age_days`)
   - Logically combine non-conflicting details from all relevant documents
   - If a newer doc contradicts an older one, use the newer version
   - Example: If `src/README.md` (age_days: 1) says "v3.5" but root `README.md` (age_days: 7) says "v3.4", use "v3.5"

4. **Extract key information**:
   - Technology stack and dependencies (newest versions from most recent docs)
   - Development commands (prefer most recently documented workflows)
   - Architecture overview (synthesize from all docs, prioritizing recent changes)
   - Active feature summaries (1-2 sentences each from newest relevant docs)

5. **Update README.md structure**:
   - Keep or create: Overview, Quick Start, Architecture, Development sections
   - Add: Documentation Index section with links to detailed docs
   - Keep README concise (under 400 lines recommended)
   - When updating existing sections, preserve recent information over older details

6. **Do NOT**: Include implementation details, completed feature changelogs, or temporary plan documents
