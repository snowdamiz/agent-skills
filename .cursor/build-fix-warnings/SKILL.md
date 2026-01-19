---
name: build-fix-warnings
description: Build the project and systematically fix warnings and errors. Use when user asks to build and fix, check for warnings, fix build errors, clean up warnings, run lint checks, or ensure code quality.
---

# Build and Fix Warnings

## When to Use

- User asks to build the project and fix warnings/errors
- User asks to check for build warnings across the codebase
- User asks to fix TypeScript, ESLint, Rust, or language-specific warnings
- User asks to run lint or quality checks
- User asks to clean up the codebase
- User wants to ensure the project compiles/builds cleanly

## Operating System Detection

**IMPORTANT**: Before executing commands, check the user's OS from the system information provided in the conversation context. Look for the `OS Version` field:
- If it contains `darwin` → **macOS** (use bash/zsh syntax)
- If it contains `windows` or `win32` → **Windows** (use PowerShell syntax)
- If it contains `linux` → **Linux** (use bash syntax)

## Instructions

### Phase 1: Discover Project Structure

Before running any builds, understand the project by examining:

#### 1.1 Check for Package Managers and Build Tools

Search for these files to determine the tech stack:

| File | Indicates | Typical Commands |
|------|-----------|------------------|
| `package.json` | Node.js/JavaScript/TypeScript | `npm run build`, `npm run lint`, `yarn build` |
| `Cargo.toml` | Rust | `cargo build`, `cargo clippy` |
| `mix.exs` | Elixir | `mix compile`, `mix compile --warnings-as-errors` |
| `pyproject.toml` / `setup.py` | Python | `ruff check .`, `mypy .`, `flake8` |
| `go.mod` | Go | `go build ./...`, `go vet ./...` |
| `pom.xml` / `build.gradle` | Java | `mvn compile`, `gradle build` |
| `Makefile` | Various | `make`, `make lint`, `make check` |

#### 1.2 Read package.json Scripts (for JS/TS projects)

If a `package.json` exists, read it to find available scripts:

```bash
cat package.json | grep -A 50 '"scripts"'
```

Look for scripts named: `build`, `lint`, `typecheck`, `check`, `test`, `compile`

#### 1.3 Identify Monorepo Structure

Check if the project is a monorepo by looking for:
- Multiple `package.json` files in subdirectories
- `workspaces` field in root `package.json`
- `lerna.json`, `pnpm-workspace.yaml`, or `turbo.json`
- Multiple `Cargo.toml` files (Rust workspace)

### Phase 2: Run Build/Check Commands

Based on the discovered project structure, run appropriate commands.

#### 2.1 JavaScript/TypeScript Projects

**TypeScript checking:**
```bash
# If using tsc directly
npx tsc --noEmit

# If using vue-tsc (Vue projects)
npx vue-tsc --noEmit

# Check package.json for custom script
npm run typecheck  # or yarn typecheck
```

**Linting:**
```bash
# ESLint
npx eslint . --ext .js,.jsx,.ts,.tsx,.vue

# Or use project's lint script
npm run lint
```

#### 2.2 Rust Projects

```bash
# Basic compilation
cargo build

# Clippy for warnings and lints
cargo clippy

# Stricter checking
cargo clippy -- -D warnings
```

#### 2.3 Elixir Projects

```bash
# Basic compile
mix compile

# Treat warnings as errors
mix compile --warnings-as-errors

# Run formatter check
mix format --check-formatted
```

#### 2.4 Python Projects

```bash
# Ruff (fast linter)
ruff check .

# MyPy (type checking)
mypy .

# Flake8
flake8 .

# Pylint
pylint **/*.py
```

#### 2.5 Go Projects

```bash
# Build all packages
go build ./...

# Static analysis
go vet ./...

# Stricter linting
golangci-lint run
```

### Phase 3: Parse and Categorize Issues

After running builds, organize issues by:

1. **Severity**: Errors first, then warnings
2. **Location**: Group by file or module
3. **Type**: Compile errors, lint warnings, type errors, style issues

Create a summary like:

```
## Build Results Summary

### Errors (Must Fix)
- [ ] 2 TypeScript errors in src/utils/
- [ ] 1 compile error in lib/auth.ex

### Warnings (Should Fix)
- [ ] 5 unused variable warnings
- [ ] 3 ESLint warnings (no-unused-vars)
- [ ] 8 Clippy suggestions
```

### Phase 4: Systematically Fix Issues

Work through issues in this order:

1. **Errors first** - These block compilation
2. **Warnings by file** - Fix one file at a time
3. **Re-verify after fixes** - Run build again to confirm

#### Common Fix Patterns

**TypeScript/JavaScript:**

| Issue | Fix |
|-------|-----|
| Unused variable | Remove or prefix with `_` |
| Missing type | Add explicit type annotation |
| Possibly undefined | Add null check or optional chaining |
| Type mismatch | Correct the type or add proper cast |
| Missing import | Add the import statement |

**ESLint:**

| Issue | Fix |
|-------|-----|
| `no-unused-vars` | Remove or prefix with `_` |
| `react-hooks/exhaustive-deps` | Add missing dependencies to array |
| `@typescript-eslint/no-explicit-any` | Replace `any` with proper type |
| Formatting issues | Run `npm run format` or `npx prettier --write` |

**Rust/Clippy:**

| Issue | Fix |
|-------|-----|
| Unused variable | Prefix with `_` |
| Unused import | Remove from `use` statement |
| `clippy::needless_return` | Remove explicit `return` |
| `clippy::redundant_clone` | Remove unnecessary `.clone()` |
| Dead code | Add `#[allow(dead_code)]` or remove |

**Elixir:**

| Issue | Fix |
|-------|-----|
| Unused variable | Prefix with `_` (e.g., `_unused`) |
| Unused alias | Remove the alias |
| Deprecated function | Use the recommended replacement |
| Missing return | Add explicit return or pattern match |

**Python:**

| Issue | Fix |
|-------|-----|
| Unused import | Remove the import |
| Undefined variable | Define or import it |
| Type error | Add type hints or fix the types |
| Line too long | Break into multiple lines |

### Phase 5: Verify Fixes

After fixing all issues, re-run the build/check commands to verify:

1. All errors are resolved
2. Warning count has decreased or reached zero
3. No new issues were introduced

Report final status:
- Number of issues fixed
- Any remaining issues that need manual attention
- Files modified

## Best Practices

### Do

- Discover the project's build system before running commands
- Fix errors before warnings
- Work on one file/module at a time
- Re-run builds after each batch of fixes
- Preserve existing functionality - don't change behavior while fixing warnings
- Use `_` prefix for intentionally unused variables rather than deleting them

### Don't

- Assume a specific project structure - always discover first
- Suppress warnings without understanding them
- Change logic to fix type errors - only fix the types
- Delete code that appears unused without checking for dynamic usage
- Combine warning fixes with feature changes

## Example Session

User: "Build the project and fix any warnings"

1. **Discover**: Check for `package.json`, `Cargo.toml`, etc.
2. **Read scripts**: Find `npm run build`, `npm run lint` available
3. **Run builds**: Execute build and lint commands
4. **Collect output**: "Found 2 errors, 15 warnings"
5. **Create todo list**: Group issues by severity and file
6. **Fix errors first**: Resolve blocking issues
7. **Fix warnings**: Work through remaining warnings
8. **Verify**: Re-run builds to confirm
9. **Report**: "Fixed 17 issues. Project now builds cleanly."

## Handling Special Cases

### Large Number of Warnings

If there are 50+ warnings:
1. Focus on one directory/module at a time
2. Batch similar warning types together
3. Consider using auto-fix where available (`eslint --fix`, `cargo clippy --fix`)

### Intermittent or Environment Issues

Some warnings may be environment-specific:
- Missing environment variables
- Database connection warnings
- Path resolution issues

Note these separately and don't attempt to "fix" configuration issues.

### Breaking Changes

If a fix would require a breaking change:
1. Document the issue
2. Ask the user before proceeding
3. Consider adding a TODO comment instead

## Auto-Fix Commands Reference

Many tools support automatic fixing:

```bash
# ESLint auto-fix
npx eslint . --fix

# Prettier formatting
npx prettier --write .

# Rust Clippy auto-fix
cargo clippy --fix

# Python Ruff auto-fix
ruff check . --fix

# Go imports
goimports -w .
```

Always review auto-fixed changes before committing.
