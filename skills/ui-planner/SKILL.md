---
name: ui-planner
description: Create comprehensive UI implementation plans with design research. Use when user asks to plan UI, design interface, create UI mockup plan, layout design, plan frontend visuals, design system planning, or needs a production-ready UI blueprint.
---

# UI Planner

## When to Use

- User asks to plan the UI for an application or feature
- User wants to design the interface/layout before implementation
- User requests a UI mockup plan or design blueprint
- User wants to research UI patterns for similar apps
- User asks to create a design system or component plan
- User wants professional UI recommendations for their project
- User says "plan the UI", "design the interface", or "create a UI plan"
- User has context (files, descriptions) and needs a UI implementation plan

## Overview

This skill creates production-ready UI implementation plans by:
1. Gathering context from provided files, text, or conversation
2. Researching similar apps for design inspiration and patterns
3. Analyzing color schemes, themes, and UX patterns that fit the app's purpose
4. Producing a detailed, implementable UI plan with placeholder values/pages

The output enables direct UI implementation without needing a designer.

## Prerequisites

- WebSearch tool for design research
- Context about the project (provided by user or gathered from codebase)

## Instructions

### Phase 1: Context Gathering

#### 1.1 Extract Project Information

From the provided context (files, description, conversation), identify:

- **App purpose**: What does this application do?
- **Target audience**: Who will use this?
- **App category**: SaaS, e-commerce, social, productivity, dashboard, etc.
- **Core features**: What functionality needs UI?
- **Tech stack**: Framework, CSS approach, component libraries (if known)
- **Existing branding**: Any colors, logos, or brand guidelines mentioned

#### 1.2 Check Codebase Context (If Available)

Search the codebase for:
- Existing UI components or design tokens
- Current CSS/styling approach (Tailwind, CSS modules, styled-components, etc.)
- Component library in use (shadcn, Radix, MUI, etc.)
- Existing color variables or theme configuration
- Layout patterns already established

Use SemanticSearch queries like:
- "What UI components exist in this project?"
- "How is styling handled in this codebase?"
- "What design tokens or theme configuration exists?"

#### 1.3 Clarifying Questions

If critical information is missing, ask the user. Select 3-5 most relevant:

**Tech Stack (if not detected)**
- "What frontend framework are you using (React, Vue, Svelte, etc.)?"
- "What CSS approach do you prefer (Tailwind, CSS modules, etc.)?"
- "Are you using a component library (shadcn/ui, Radix, MUI, etc.)?"

**Design Preferences**
- "Do you have any existing brand colors or guidelines?"
- "What's the general aesthetic you're going for (minimal, bold, playful, corporate)?"
- "Any apps whose design you admire that I should reference?"

**Scope**
- "Which pages/views should the UI plan cover?"
- "Is this for the full app or specific features?"

**Wait for responses before proceeding to research.**

### Phase 2: Design Research

Execute comprehensive design research with minimum 8-10 searches.

#### 2.1 Competitor UI Research (3-4 searches)

```
"[app type] UI design examples 2026"
"best [app category] app interfaces"
"[competitor name] UI screenshots"
"[app type] dashboard design inspiration"
```

#### 2.2 Design Pattern Research (2-3 searches)

```
"[app type] UX patterns best practices"
"[feature type] UI design patterns"
"modern [app category] interface trends 2026"
```

#### 2.3 Color & Theme Research (2-3 searches)

```
"[app category] color schemes 2026"
"[industry] website color palettes"
"[mood/aesthetic] UI color inspiration"
"dark mode design [app type]"
```

#### 2.4 Component Pattern Research (1-2 searches)

```
"[tech stack] UI components [app type]"
"[component library] design system examples"
```

#### 2.5 Document Research Findings

Create a research summary noting:
- 3-5 competitor apps with notable UI elements
- Common design patterns observed
- Color schemes that resonate with the app's purpose
- UX patterns that work well for similar apps
- Any anti-patterns or things to avoid

### Phase 3: Design System Planning

#### 3.1 Color Palette Definition

Based on research and app purpose, define:

**Primary Colors**
- Primary: Main brand/action color
- Primary variants: Hover, active, disabled states

**Semantic Colors**
- Success: Positive actions, confirmations
- Warning: Caution states
- Error: Errors, destructive actions
- Info: Informational elements

**Neutral Colors**
- Background shades (2-3 levels)
- Surface/card backgrounds
- Border colors
- Text colors (primary, secondary, muted)

**Accent Colors (optional)**
- Secondary accent for variety
- Highlight colors for emphasis

Provide both light and dark mode variants if applicable.

#### 3.2 Typography Scale

Define the typography system:

```
Display:     48-72px  - Hero headings, landing pages
H1:          36-40px  - Page titles
H2:          28-32px  - Section headings
H3:          24px     - Subsection headings
H4:          20px     - Card titles, smaller headings
Body:        16px     - Default text
Body Small:  14px     - Secondary text, captions
Caption:     12px     - Labels, hints, metadata
```

Include font family recommendations based on app type:
- **SaaS/Professional**: Inter, Plus Jakarta Sans, DM Sans
- **Creative/Modern**: Space Grotesk, Outfit, Sora
- **Traditional/Corporate**: Source Sans Pro, Open Sans, Roboto
- **Playful/Friendly**: Nunito, Quicksand, Poppins

#### 3.3 Spacing & Layout System

Define consistent spacing scale:

```
4px  (xs)   - Tight gaps, icon padding
8px  (sm)   - Small gaps, compact elements
12px (md)   - Default element spacing
16px (lg)   - Component padding, gaps
24px (xl)   - Section spacing
32px (2xl)  - Large section gaps
48px (3xl)  - Page section spacing
64px (4xl)  - Major section breaks
```

Layout guidelines:
- Max content width
- Sidebar widths (if applicable)
- Grid column recommendations
- Responsive breakpoints

#### 3.4 Component Style Guidelines

Define styling for core components:

**Buttons**
- Border radius (sharp, rounded, pill)
- Variants (solid, outline, ghost, link)
- Sizes (sm, md, lg)
- States (hover, active, disabled, loading)

**Cards**
- Shadow levels
- Border treatment
- Padding standards
- Header/body/footer structure

**Forms**
- Input styling (borders, focus states)
- Label positioning
- Error state styling
- Helper text styling

**Navigation**
- Header height
- Navigation item styling
- Mobile menu approach

### Phase 4: Page Layout Planning

#### 4.1 Information Architecture

Map out the page structure:

```
App Structure
├── Public Pages
│   ├── Landing Page
│   ├── Pricing
│   ├── About
│   └── Auth (Login/Register)
├── Authenticated Pages
│   ├── Dashboard
│   ├── [Feature Pages]
│   └── Settings
└── Shared Components
    ├── Navigation
    ├── Footer
    └── Common UI Elements
```

#### 4.2 Page-by-Page Layout Specs

For each major page, define:

**Page Name**
```
Layout Type: [sidebar, full-width, centered, split]
Sections:
1. [Section Name]
   - Purpose: [what this section does]
   - Components: [list of UI components]
   - Layout: [grid/flex arrangement]
   - Placeholder content: [example text/data]

2. [Section Name]
   ...
```

Include wireframe descriptions or ASCII layouts when helpful:

```
┌─────────────────────────────────────────────┐
│  Logo        Nav Items           User Menu  │
├─────────────────────────────────────────────┤
│         │                                   │
│ Sidebar │      Main Content Area            │
│   Nav   │                                   │
│         │   ┌─────────┐  ┌─────────┐       │
│         │   │ Card 1  │  │ Card 2  │       │
│         │   └─────────┘  └─────────┘       │
│         │                                   │
└─────────────────────────────────────────────┘
```

#### 4.3 Responsive Behavior

Define breakpoints and layout changes:

- **Desktop (1280px+)**: Full layout with sidebar
- **Tablet (768px-1279px)**: Collapsible sidebar, adjusted grid
- **Mobile (<768px)**: Bottom nav or hamburger menu, stacked layout

### Phase 5: Component Inventory

#### 5.1 Required Components List

Categorize all needed components:

**Layout Components**
- AppShell / Layout wrapper
- Header / Navigation bar
- Sidebar (if applicable)
- Footer
- Page container

**Data Display**
- Card
- Table / Data grid
- List
- Stats / Metrics display
- Empty states
- Loading states

**Form Components**
- Input
- Select / Dropdown
- Checkbox / Radio
- Date picker
- File upload
- Form layout

**Feedback Components**
- Toast / Notification
- Alert / Banner
- Modal / Dialog
- Tooltip
- Progress indicator

**Navigation Components**
- Tabs
- Breadcrumbs
- Pagination
- Menu / Dropdown menu

#### 5.2 Component Specifications

For complex or custom components, provide detailed specs:

```
Component: [Name]
Purpose: [What it does]
Variants: [Different versions]
Props/Options:
  - [prop]: [type] - [description]
States: [hover, active, disabled, loading, error]
Accessibility: [ARIA requirements]
Example Usage: [Code snippet or description]
```

### Phase 6: Output Deliverables

#### 6.1 UI Plan Document

Compile everything into a comprehensive document:

```markdown
# UI Implementation Plan: [App Name]

**Generated**: [Date]
**Tech Stack**: [Framework, CSS approach, component library]
**App Type**: [Category]

## Executive Summary
[2-3 paragraph overview of the design direction]

## Design Research Insights
### Competitor Analysis
[Key findings from competitor research]

### Design Patterns Adopted
[Patterns chosen and why]

## Design System

### Color Palette
[Full color definitions with hex values]

### Typography
[Font families, size scale]

### Spacing & Layout
[Spacing scale, layout guidelines]

### Component Styles
[Button, card, form styling guidelines]

## Page Layouts

### [Page 1 Name]
[Detailed layout spec]

### [Page 2 Name]
[Detailed layout spec]

...

## Component Inventory
[Categorized list of all components needed]

### Component Specifications
[Detailed specs for custom components]

## Responsive Design
[Breakpoints and behavior changes]

## Implementation Notes
[Technical considerations, suggested libraries, implementation order]

## Placeholder Content
[Sample text, images, data for development]

## Accessibility Checklist
- [ ] Color contrast meets WCAG AA
- [ ] Focus states visible
- [ ] Screen reader compatible
- [ ] Keyboard navigable
- [ ] Alt text for images
```

#### 6.2 Implementation Roadmap

Suggest implementation order:

```
Phase 1: Foundation
- [ ] Set up design tokens (colors, typography, spacing)
- [ ] Configure theme provider
- [ ] Create base layout components

Phase 2: Core Components
- [ ] Build common components (Button, Card, Input, etc.)
- [ ] Create navigation components
- [ ] Build feedback components

Phase 3: Page Layouts
- [ ] Implement page shells/layouts
- [ ] Build page-specific components
- [ ] Add placeholder content

Phase 4: Polish
- [ ] Responsive adjustments
- [ ] Dark mode (if applicable)
- [ ] Animation/transitions
- [ ] Accessibility audit
```

#### 6.3 Save Options

Offer to:
- Save the UI plan to `docs/` folder
- Create a design tokens file (CSS variables, Tailwind config, etc.)
- Generate component stubs
- Create GitHub issues for implementation tasks

## Best Practices

### Do

- Research before recommending - don't invent patterns
- Match design to app purpose (playful for games, professional for B2B)
- Provide specific hex codes, pixel values, concrete details
- Include placeholder content for development
- Consider accessibility from the start
- Plan for both light and dark modes when appropriate
- Use consistent naming conventions throughout
- Provide implementation-ready specifications

### Don't

- Skip the research phase
- Use generic/vague descriptions ("make it look nice")
- Ignore the existing tech stack
- Forget responsive design considerations
- Overlook loading and error states
- Create overly complex designs that can't be implemented
- Recommend libraries without checking compatibility
- Ignore the app's purpose when choosing aesthetics

## Design by App Type Guidelines

### SaaS / Dashboard Apps
- Clean, minimal interface
- Ample whitespace
- Data-focused layouts
- Subtle shadows and borders
- Professional color schemes (blues, grays, teals)

### E-commerce
- Product-focused layouts
- Clear CTAs
- Trust indicators
- Grid-based product displays
- Warm, inviting colors

### Social / Community Apps
- Engagement-focused design
- User-generated content displays
- Interactive elements
- Vibrant, energetic colors
- Card-based content

### Content / Blog Platforms
- Typography-focused
- Readable layouts
- Clean article views
- Minimal distractions
- Neutral with accent colors

### Developer Tools
- Code-friendly fonts
- Dark mode priority
- Information-dense layouts
- Terminal-inspired elements
- Monospace accents

### Landing Pages / Marketing
- Hero sections
- Social proof areas
- Clear value propositions
- Strong CTAs
- Brand-aligned colors

## Example Session

**User**: "Here's my app idea - a habit tracking app for developers. It should have a dashboard showing streaks, weekly/monthly views, and gamification elements like achievements. I'm using Next.js with Tailwind."

**Agent Response**:

"I have good context to start planning. Let me research similar apps and design patterns for habit trackers and developer-focused tools.

[Executes 8-10 design research searches]

Based on my research, here's what I found:

**Competitor Insights:**
- Habitica uses gamification effectively with pixel art aesthetics
- Streaks app uses bold, minimal design with color-coded habits
- WakaTime (developer tool) uses dark mode with data visualizations

**Design Direction Recommendation:**
Given this is for developers, I suggest:
- Dark mode as default (with light option)
- Code-editor inspired aesthetics with monospace accents
- Data visualization focus for streaks/progress
- Achievement badges with a subtle pixel/retro gaming feel
- Clean dashboard layout similar to GitHub contribution graphs

Would you like me to proceed with creating the full UI plan with this direction, or would you prefer adjustments?"

[After confirmation, generates complete UI Plan document]

## Integration with Other Skills

This skill works well with:
- **deep-research**: For more thorough competitive analysis
- **project-feature-planner**: To align UI with feature roadmap
- **create-documentation**: To save UI plans
- **implement-github-issue**: To track UI implementation tasks
