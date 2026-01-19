---
name: scaffold-project
description: Scaffold a new project structure from context like text descriptions, design files, requirements documents, or example code. Use when user wants to create, initialize, bootstrap, or set up a new project with the latest compatible package versions.
---

# Scaffold Project

## When to Use

- User asks to scaffold, create, or initialize a new project
- User provides project requirements, descriptions, or specifications and wants to generate the structure
- User shares design files, mockups, or architecture diagrams and wants to build the project
- User has text describing what they want to build
- User wants to bootstrap a project with latest package versions
- User says "set up a new project", "create project structure", "initialize codebase"
- User provides a spec, PRD, or feature list and wants the project created
- User wants to convert requirements into a working project skeleton

## Overview

This skill transforms contextual information (text descriptions, files, specifications, mockups, etc.) into a complete, well-structured project scaffold with:
- Appropriate directory structure
- Configuration files with latest compatible package versions
- Boilerplate code following best practices
- README with setup instructions

## Instructions

### Phase 1: Context Gathering & Analysis

#### 1.1 Identify Available Context

Examine what the user has provided:

**Text-based context:**
- Project description or requirements
- Feature lists or user stories
- Technical specifications or PRDs
- Chat history describing the project

**File-based context:**
- Design files or mockups (images, Figma exports)
- Architecture diagrams
- Existing code snippets or examples
- Configuration files from similar projects
- API specifications (OpenAPI, GraphQL schemas)

**Implicit context:**
- Current workspace structure
- Existing package.json or configuration files
- README files describing the intended project

#### 1.2 Extract Project Requirements

From the gathered context, identify:

| Aspect | Questions to Answer |
|--------|---------------------|
| **Type** | Web app, API, CLI tool, library, mobile app, full-stack? |
| **Stack** | Frontend framework, backend language, database? |
| **Features** | Core functionality needed? |
| **Platform** | Node.js, Python, Go, Rust, etc.? |
| **Tooling** | Build tools, linters, formatters, testing? |
| **Deployment** | Docker, serverless, traditional hosting? |

#### 1.3 Ask Clarifying Questions (If Needed)

If critical information is missing, ask targeted questions:

```
- "What's the primary tech stack you want to use?"
- "Should this be a monorepo or single project?"
- "Do you need authentication/database/API integration?"
- "Any specific frameworks or libraries you prefer?"
- "What's your target deployment environment?"
```

**IMPORTANT**: Only ask questions if truly necessary. If reasonable defaults can be inferred from context, proceed with those and note your assumptions.

### Phase 2: Technology & Package Research

#### 2.1 Determine Tech Stack

Based on context, select appropriate technologies:

**Frontend Web:**
- Framework: React, Vue, Svelte, Next.js, Nuxt, SvelteKit, Astro
- Styling: Tailwind CSS, CSS Modules, styled-components, Sass
- State: Zustand, Jotai, Redux Toolkit, Pinia

**Backend/API:**
- Node.js: Express, Fastify, Hono, Nest.js
- Python: FastAPI, Flask, Django
- Go: Gin, Echo, Fiber
- Rust: Axum, Actix

**Full-Stack:**
- Next.js, Nuxt, SvelteKit, Remix, Astro
- T3 Stack (Next.js + tRPC + Prisma + Tailwind)

**Database:**
- SQL: PostgreSQL, MySQL, SQLite
- NoSQL: MongoDB, Redis
- ORMs: Prisma, Drizzle, TypeORM, SQLAlchemy

#### 2.2 Research Latest Compatible Versions

**CRITICAL**: Use web search to find current stable versions. Do NOT guess version numbers.

**Required Searches:**
```
"[framework] latest version 2026"
"[package] npm latest stable"
"[library] current release"
"[framework] recommended dependencies 2026"
"[stack] starter template packages"
```

**For each core package, verify:**
- Latest stable version number
- Peer dependency requirements
- Known compatibility issues with other chosen packages
- Minimum Node/Python/runtime version required

#### 2.3 Create Dependency Manifest

Document the packages and versions to use:

```
Core Dependencies:
- [package]@[version] - [purpose]
- [package]@[version] - [purpose]

Dev Dependencies:
- [package]@[version] - [purpose]
- [package]@[version] - [purpose]

Peer/Runtime Requirements:
- Node.js >= [version]
- [other requirements]
```

### Phase 3: Project Structure Design

#### 3.1 Directory Structure Templates

Select and customize based on project type:

**React/Next.js Frontend:**
```
project-name/
├── src/
│   ├── app/                 # Next.js App Router (or pages/)
│   ├── components/
│   │   ├── ui/              # Reusable UI components
│   │   └── features/        # Feature-specific components
│   ├── hooks/               # Custom React hooks
│   ├── lib/                 # Utility functions
│   ├── styles/              # Global styles
│   └── types/               # TypeScript types
├── public/                  # Static assets
├── .env.example             # Environment template
├── package.json
├── tsconfig.json
├── tailwind.config.ts       # If using Tailwind
├── next.config.ts           # Framework config
└── README.md
```

**Node.js API/Backend:**
```
project-name/
├── src/
│   ├── routes/              # API route handlers
│   ├── controllers/         # Business logic
│   ├── services/            # External service integrations
│   ├── models/              # Data models/schemas
│   ├── middleware/          # Express/Fastify middleware
│   ├── utils/               # Helper functions
│   ├── config/              # Configuration management
│   └── index.ts             # Entry point
├── tests/                   # Test files
├── prisma/                  # If using Prisma
│   └── schema.prisma
├── .env.example
├── package.json
├── tsconfig.json
├── Dockerfile               # If containerized
└── README.md
```

**Python API (FastAPI):**
```
project-name/
├── app/
│   ├── api/
│   │   └── routes/          # API endpoints
│   ├── core/                # Config, security
│   ├── models/              # Pydantic/SQLAlchemy models
│   ├── services/            # Business logic
│   └── main.py              # Entry point
├── tests/
├── alembic/                 # If using migrations
├── .env.example
├── pyproject.toml           # Or requirements.txt
├── Dockerfile
└── README.md
```

**Full-Stack Monorepo:**
```
project-name/
├── apps/
│   ├── web/                 # Frontend application
│   └── api/                 # Backend API
├── packages/
│   ├── ui/                  # Shared UI components
│   ├── config/              # Shared configs
│   └── types/               # Shared TypeScript types
├── package.json             # Root package.json
├── turbo.json               # If using Turborepo
├── pnpm-workspace.yaml      # If using pnpm
└── README.md
```

#### 3.2 Customize Structure

Adapt the template based on:
- Features extracted from context
- Scale/complexity of the project
- Team preferences (if mentioned)
- Deployment requirements

### Phase 4: Scaffold Generation

#### 4.1 Operating System Detection

**IMPORTANT**: Check the user's OS from system information:
- `darwin` → **macOS** (use bash/zsh)
- `windows` or `win32` → **Windows** (use PowerShell)
- `linux` → **Linux** (use bash)

#### 4.2 Create Directory Structure

**macOS/Linux:**
```bash
mkdir -p project-name/{src/{components,hooks,lib,types},public}
```

**Windows PowerShell:**
```powershell
New-Item -ItemType Directory -Force -Path "project-name/src/components","project-name/src/hooks","project-name/src/lib"
```

#### 4.3 Generate Configuration Files

Create each configuration file with researched versions:

**package.json** (example for Next.js):
```json
{
  "name": "project-name",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "type-check": "tsc --noEmit"
  },
  "dependencies": {
    "next": "^[LATEST_VERSION]",
    "react": "^[LATEST_VERSION]",
    "react-dom": "^[LATEST_VERSION]"
  },
  "devDependencies": {
    "@types/node": "^[LATEST_VERSION]",
    "@types/react": "^[LATEST_VERSION]",
    "typescript": "^[LATEST_VERSION]",
    "eslint": "^[LATEST_VERSION]",
    "eslint-config-next": "^[LATEST_VERSION]"
  }
}
```

**tsconfig.json** (example):
```json
{
  "compilerOptions": {
    "target": "ES2022",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "paths": {
      "@/*": ["./src/*"]
    }
  },
  "include": ["**/*.ts", "**/*.tsx"],
  "exclude": ["node_modules"]
}
```

#### 4.4 Create Boilerplate Files

Generate starter files based on the project type:

**Entry points**: main.ts, index.ts, App.tsx, etc.
**Components**: Basic UI components if frontend
**Routes**: API route stubs if backend
**Types**: Common type definitions
**Utils**: Common utility functions

#### 4.5 Environment Configuration

Create `.env.example` with documented variables:
```
# Database
DATABASE_URL=

# Authentication (if applicable)
AUTH_SECRET=

# API Keys (if applicable)
API_KEY=

# App Configuration
NODE_ENV=development
PORT=3000
```

### Phase 5: Documentation & Setup

#### 5.1 Generate README.md

Include:

```markdown
# Project Name

Brief description of what this project does.

## Tech Stack

- [Framework] - [version]
- [Library] - [version]
- [Tool] - [version]

## Prerequisites

- Node.js >= [version]
- [Other requirements]

## Getting Started

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   # or
   pnpm install
   ```
3. Copy environment variables:
   ```bash
   cp .env.example .env
   ```
4. Start the development server:
   ```bash
   npm run dev
   ```

## Project Structure

```
[Include abbreviated structure]
```

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run lint` - Run linter
- `npm run test` - Run tests

## Configuration

[Document key configuration options]

## Deployment

[Basic deployment instructions]
```

#### 5.2 Additional Documentation (If Complex)

For larger projects, create:
- `CONTRIBUTING.md` - Contribution guidelines
- `docs/` folder with architecture documentation
- API documentation stubs

### Phase 6: Validation & Handoff

#### 6.1 Verify Structure

After scaffolding, verify:
- [ ] All directories created successfully
- [ ] package.json has valid JSON syntax
- [ ] TypeScript config is valid (if applicable)
- [ ] No placeholder version numbers remain
- [ ] README accurately reflects the project

#### 6.2 Install Dependencies

Offer to run dependency installation:
```bash
npm install
# or
pnpm install
# or
yarn install
```

#### 6.3 Test the Scaffold

Run basic validation:
- `npm run lint` (if linting configured)
- `npm run type-check` (if TypeScript)
- `npm run dev` (verify dev server starts)

#### 6.4 Summary Output

Present a summary to the user:

```
✓ Project scaffolded: [project-name]

Structure created:
- [X] directories
- [Y] configuration files
- [Z] boilerplate files

Key packages (latest stable versions):
- [package]@[version]
- [package]@[version]

Next steps:
1. cd [project-name]
2. npm install
3. cp .env.example .env
4. npm run dev

Notes:
- [Any assumptions made]
- [Any recommended next steps]
```

## Version Research Guidelines

### Always Research Versions

**NEVER** hardcode or guess version numbers. Always:

1. Search for the latest stable version
2. Verify compatibility between packages
3. Check for recent breaking changes
4. Note minimum runtime requirements

### Version Pinning Strategy

Use appropriate version ranges:
- **Caret (^)**: For most packages - allows minor/patch updates
- **Tilde (~)**: For packages with unstable minor releases
- **Exact**: Only for packages with known compatibility issues

### Compatibility Checks

Before finalizing versions, verify:
- Framework ↔ Plugin compatibility
- TypeScript ↔ @types package alignment
- Peer dependency requirements
- Node.js/runtime version requirements

## Best Practices

### Do

- Research current package versions before scaffolding
- Use TypeScript by default for JavaScript projects
- Include linting and formatting configuration
- Create comprehensive .env.example files
- Add .gitignore with appropriate patterns
- Structure for scalability even in small projects
- Document assumptions in README
- Use modern tooling (ES modules, modern bundlers)

### Don't

- Guess or hardcode package versions
- Create overly complex structures for simple projects
- Skip environment variable documentation
- Forget to include a README
- Use deprecated packages or patterns
- Over-engineer the initial scaffold

## Common Project Templates

### Minimal React + Vite

```
Packages: vite, react, react-dom, typescript, @vitejs/plugin-react
Structure: src/{components,hooks,lib}, public, index.html
```

### Next.js Full-Stack

```
Packages: next, react, react-dom, typescript, tailwindcss, prisma
Structure: src/{app,components,lib}, prisma, public
```

### Express API

```
Packages: express, typescript, zod, cors, helmet
Structure: src/{routes,controllers,middleware,utils}
```

### FastAPI Python

```
Packages: fastapi, uvicorn, pydantic, sqlalchemy
Structure: app/{api,core,models,services}
```

## Integration with Other Skills

This skill works well with:
- **project-feature-planner**: Plan features before scaffolding
- **create-documentation**: Generate additional docs after scaffold
- **deep-research**: Research best practices for specific stacks
- **ui-planner**: Design UI components before creating structure
