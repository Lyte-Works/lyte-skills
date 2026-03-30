<!-- reconstructed -->
---
name: "product-manager"
description: "Full PM workflow — user stories, feature prioritization, specs, roadmaps, and stakeholder communication"
workers: ["product-manager"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Product Manager

## When to Use
- Defining what to build next
- Writing user stories and acceptance criteria
- Prioritizing a feature backlog
- Creating product specs for engineering
- Communicating product decisions to stakeholders

## Workflow

### Step 1: Problem Definition
Before any feature work, document:
- **Problem statement**: What problem are we solving? For whom?
- **Evidence**: What data or customer feedback supports this problem?
- **Impact**: What happens if we do not solve it?
- **Scope**: What is in scope and explicitly out of scope?

### Step 2: User Stories
Write user stories in this format:
> As a [persona], I want to [action] so that [outcome].

**Acceptance criteria** for each story:
- Given [context], when [action], then [expected result]
- Include edge cases and error states
- Specify what "done" looks like

### Step 3: Prioritization
Use a simple prioritization framework:

| Feature | Impact (1-5) | Effort (1-5) | Confidence (1-5) | Score |
|---------|-------------|-------------|-------------------|-------|
| | | | | Impact x Confidence / Effort |

Sort by score. The top items go into the next sprint.

**ICE Score** = Impact x Confidence / Effort

Alternative: RICE (Reach x Impact x Confidence / Effort) when you have reach data.

### Step 4: Product Spec
For each feature entering development, create a spec:

```
# Feature: [Name]

## Problem
[One paragraph]

## Solution
[One paragraph describing the approach]

## User Stories
[List of user stories with acceptance criteria]

## Design
[Link to mockups/wireframes or description of UI]

## Technical Notes
[Any technical constraints or dependencies the engineering team should know]

## Metrics
[How will we measure success?]

## Out of Scope
[What this feature explicitly does NOT include]
```

### Step 5: Handoff to Engineering
- Create the spec in Notion
- Link user stories to the spec
- Review with the engineering worker before sprint planning
- Ensure acceptance criteria are clear enough for test writing

### Step 6: Measure and Learn
After the feature ships:
- Track the defined success metrics in Vercel Analytics
- Gather user feedback (support tickets, reviews, direct feedback)
- Document learnings in Notion
- Decide: iterate, expand, or move on

## Stack Context
- **Notion**: Product specs, user stories, roadmaps, and backlogs all live in Notion. Use a Notion database for the backlog with properties for priority, status, sprint, and assigned worker.
- **GitHub**: User stories translate into GitHub Issues. Link Notion specs to GitHub Issues for traceability.
- **Next.js / Vercel**: Features are implemented in the Next.js app and deployed via Vercel. Preview deployments allow stakeholder review before merging to main.
- **Vercel Analytics**: Success metrics tracked post-launch.
- **Supabase**: If the feature involves data, the PM spec should note data requirements so the backend worker can design the schema.

## Quality Gate
- [ ] Problem statement is specific and evidence-backed
- [ ] User stories follow the "As a / I want / So that" format
- [ ] Acceptance criteria are testable (given/when/then)
- [ ] Prioritization uses a consistent framework with scores
- [ ] Product spec includes success metrics and out-of-scope section
- [ ] Spec reviewed with engineering before sprint planning

## Anti-Patterns
- **Solution-first thinking** — starting with "let's build X" instead of "what problem are we solving"
- **Vague acceptance criteria** — "it should work well" is not testable. Be specific.
- **No prioritization framework** — deciding what to build based on who is loudest is not product management
- **Specs without metrics** — if you cannot measure success, you cannot learn
- **Scope creep** — features grow silently. The out-of-scope section prevents this.

## Related Skills
- `strategy/senior-pm` — strategic layer: roadmaps and stakeholder alignment
- `strategy/agile-product-owner` — sprint-level execution
- `strategy/product-analytics` — measuring product performance
- `strategy/ux-researcher` — user research informing product decisions
- `core/scrum-master` — sprint ceremonies and process
