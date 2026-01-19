---
name: project-feature-planner
description: Brainstorming and planning assistant for new project ideas. Use when user wants to plan a project, brainstorm features, refine an idea, explore project concepts, discuss app ideas, or get help scoping a product.
---

# Project Feature Planner

## When to Use

- User shares a project idea and wants to develop it further
- User asks to brainstorm features for an app or product
- User wants help refining or scoping a project concept
- User asks about potential competitors or market landscape
- User wants to identify MVP features vs nice-to-haves
- User is exploring what to build next
- User says "I have an idea for..." or "I want to build..."
- User asks for help planning a product or application

## Overview

This skill guides collaborative brainstorming sessions to help users transform rough project ideas into well-defined, actionable plans. The process involves understanding the concept, asking clarifying questions, researching the competitive landscape, suggesting features, and organizing everything into a clear roadmap.

## Instructions

### Phase 1: Understanding the Core Idea

#### 1.1 Initial Concept Extraction

When the user shares their project idea, identify:
- **Core problem**: What problem does this solve?
- **Target users**: Who would use this?
- **Value proposition**: What's the unique benefit?
- **Domain/category**: What space does this operate in?

#### 1.2 Ask Clarifying Questions

Don't assume - ask targeted questions to understand the vision. Pick 3-5 most relevant questions from:

**Problem & Users**
- "What specific pain point are you trying to solve?"
- "Who do you see as your primary users? Can you describe them?"
- "How do people currently solve this problem without your solution?"
- "What would make someone choose this over existing solutions?"

**Scope & Vision**
- "Is this a personal project, potential startup, or something else?"
- "What platforms are you targeting (web, mobile, desktop)?"
- "Do you have a preference for the tech stack?"
- "What's your timeline or constraints?"

**Features & Functionality**
- "What's the one thing this absolutely must do well?"
- "Are there any features you've already envisioned?"
- "What would a successful first version look like to you?"

Wait for user responses before proceeding. This is a conversation, not a monologue.

### Phase 2: Competitive Research

#### 2.1 Market Landscape Search

Use web search to research the competitive landscape. Include the current year in searches for recent results.

**Required Searches (5-8 minimum)**
```
"[concept] apps 2026"
"[concept] software tools"
"best [category] alternatives 2026"
"[primary feature] applications comparison"
"[concept] startup competitors"
"[target user] tools for [problem]"
"indie [concept] apps"
"[concept] open source projects"
```

#### 2.2 Competitor Analysis

For each relevant competitor found, note:
- Name and brief description
- Key features
- Pricing model (free, freemium, subscription, one-time)
- Target audience
- Strengths and weaknesses
- What users complain about (search reviews if needed)

#### 2.3 Market Gap Identification

Based on research, identify:
- Underserved user segments
- Missing features across competitors
- Common user complaints with existing solutions
- Pricing gaps (too expensive, no free tier, etc.)
- UX/simplicity opportunities

Present findings to user conversationally and discuss positioning.

### Phase 3: Feature Brainstorming

#### 3.1 Core Feature Generation

Based on the concept and competitive research, brainstorm features in categories:

**Essential (Must-Have)**
- Features that define the core value proposition
- Without these, the product doesn't make sense
- Typically 3-5 features

**Important (Should-Have)**
- Features that significantly improve the experience
- Expected by users but not deal-breakers
- Typically 5-10 features

**Nice-to-Have (Could-Have)**
- Features that would delight users
- Competitive differentiators
- Can be added post-launch

**Future Vision (Won't-Have for MVP)**
- Advanced features for later versions
- Features that require scale to make sense
- Integration or platform expansion ideas

#### 3.2 Feature Discussion Prompts

Suggest features and ask for feedback:
- "Based on [competitor], users seem to want [feature]. Would that fit your vision?"
- "A feature like [suggestion] could differentiate you from [competitor]. Thoughts?"
- "I notice existing solutions lack [gap]. Would addressing this be valuable?"
- "What if users could [capability]? Would that align with your goals?"

#### 3.3 Unique Value Identification

Help the user identify what makes their approach unique:
- Different target audience?
- Simpler/more focused solution?
- Better pricing model?
- Unique feature combination?
- Superior UX approach?
- Different platform or ecosystem?

### Phase 4: User Stories & Use Cases

#### 4.1 Define User Personas

Create 2-3 brief user personas:
```
**[Persona Name]**
- Background: [Who they are]
- Goal: [What they want to achieve]
- Pain point: [Current frustration]
- How they'd use the product: [Key use case]
```

#### 4.2 Map Key User Journeys

For each core feature, outline:
1. User's starting point
2. Actions they take
3. Expected outcome
4. Success criteria

### Phase 5: MVP Definition

#### 5.1 Scope the Minimum Viable Product

Work with the user to define what's in v1:
- List only the essential features
- Define "done" for each feature
- Identify technical dependencies
- Estimate relative complexity (simple/medium/complex)

#### 5.2 MVP Validation Questions

Ask the user:
- "If you could only ship 3 features, which would they be?"
- "What's the minimum needed for someone to find this useful?"
- "Which features can wait until you have user feedback?"

### Phase 6: Output Deliverables

#### 6.1 Project Brief Document

Compile everything into a structured document:

```markdown
# [Project Name] - Project Brief

## Overview
[2-3 sentence description of what this is]

## Problem Statement
[What problem this solves and for whom]

## Target Users
[Primary user personas]

## Competitive Landscape
| Competitor | Strengths | Weaknesses | Our Differentiation |
|------------|-----------|------------|---------------------|
| [Name]     | [...]     | [...]      | [...]               |

## Unique Value Proposition
[What makes this different/better]

## Feature Roadmap

### MVP (Version 1.0)
- [ ] Feature 1 - [brief description]
- [ ] Feature 2 - [brief description]
- [ ] Feature 3 - [brief description]

### Version 1.1+
- [ ] Feature 4 - [brief description]
- [ ] Feature 5 - [brief description]

### Future Vision
- Feature ideas for later consideration

## User Stories
[Key user stories for MVP features]

## Technical Considerations
[Platform, stack preferences, key technical decisions]

## Open Questions
[Items that need further research or decisions]

## Next Steps
1. [Immediate action item]
2. [Second priority]
3. [Third priority]
```

#### 6.2 Save or Share

Offer to:
- Save the brief to a docs folder
- Create GitHub issues for features
- Generate a more detailed technical spec
- Continue refining any section

## Conversation Guidelines

### Be Collaborative, Not Prescriptive

- Ask more than you tell
- Present options, let user decide
- Build on user's ideas, don't replace them
- Say "What if..." rather than "You should..."

### Keep Momentum

- Don't overwhelm with too many questions at once
- Summarize progress periodically
- Offer to dive deeper or move on
- Respect the user's time and energy

### Stay Practical

- Ground suggestions in competitive reality
- Consider technical feasibility
- Balance ambition with achievability
- Focus on user value, not feature count

### Encourage Iteration

- First pass doesn't have to be perfect
- Suggest revisiting decisions after more research
- MVP can evolve based on feedback
- Planning is ongoing, not one-time

## Example Session

**User**: "I want to build a habit tracking app"

**Agent Response**:
"Great idea - habit tracking is a space with a lot of interest. Let me ask a few questions to understand your vision better:

1. What makes you want to build this? Is there something missing from existing habit trackers you've tried?
2. Who do you see using this - productivity enthusiasts, people with specific health goals, or a broader audience?
3. Are you thinking mobile-first, web app, or both?

While you think about those, I'll research the current landscape of habit tracking apps to see what's out there."

[Execute competitive research searches]

**After user responds**: Continue with feature discussion, MVP scoping, etc.

## Best Practices

### Do

- Start with understanding, not solutions
- Research competitors before suggesting features
- Tie features back to user problems
- Help prioritize ruthlessly for MVP
- Document decisions and rationale
- Ask about constraints (time, budget, skills)
- Celebrate the user's creativity and initiative

### Don't

- Overwhelm with too many features at once
- Skip competitive research
- Push technologies or approaches without context
- Assume you know what the user wants
- Dismiss simple ideas - simplicity is often valuable
- Forget to document the session output
- Rush through phases just to complete them

## Integration with Other Skills

This skill works well with:
- **deep-research**: For more thorough competitive analysis
- **create-documentation**: To save the project brief
- **create-github-issue**: To create issues for MVP features
