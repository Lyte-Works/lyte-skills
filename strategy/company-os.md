<!-- reconstructed -->
---
name: "company-os"
description: "Operating system for company decisions — mission, vision, values, and decision-making frameworks"
workers: ["business-strategist"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Company OS

## When to Use
- New company or startup defining its operating principles
- Client has no documented mission, vision, or values
- Team is making inconsistent decisions due to lack of shared framework
- Scaling from founder-led to team-led decision-making
- Annual or quarterly strategic planning

## Workflow

### Step 1: Define Mission
One sentence answering: What do we do, for whom, and why does it matter?
- Must be specific enough that it excludes things you do NOT do
- Test: can a new employee use this to decide whether a project is in scope?

### Step 2: Define Vision
One sentence answering: What does the world look like if we succeed at our mission?
- 3-5 year time horizon
- Should be ambitious but credible

### Step 3: Define Values (3-5 max)
Each value must be:
- **Actionable** — you can point to a specific behavior that demonstrates it
- **Distinctive** — not every company would claim it (eliminate "integrity," "excellence," "innovation")
- **Testable** — you can evaluate a decision against it

Format each value as:
> **[Value Name]**: [One-sentence definition]. Example: [Specific behavior that demonstrates this value].

### Step 4: Build the Decision Framework
Create a simple framework the team uses when facing decisions:

1. **Does this serve our mission?** (if no, stop)
2. **Does this align with our values?** (if it violates any, stop)
3. **Does this move us toward our vision?** (if not, deprioritize)
4. **What is the cost of inaction?** (if low, it can wait)
5. **Who is the decision-maker?** (one person, not a committee)

### Step 5: Define Operating Rhythms
| Rhythm | Frequency | Purpose | Participants |
|--------|-----------|---------|-------------|
| Daily standup | Daily | Blockers and priorities | Team |
| Weekly review | Weekly | Progress against goals | Team leads |
| Monthly metrics | Monthly | KPI review and course correction | Leadership |
| Quarterly planning | Quarterly | Goal setting and resource allocation | All |
| Annual strategy | Annually | Mission/vision review, long-term planning | Leadership + board |

### Step 6: Document in Notion
Create a "Company OS" page as the root of the client's strategic documentation:
- Mission, Vision, Values
- Decision Framework
- Operating Rhythms
- Link to OKRs or goals (if applicable)

## Stack Context
- **Notion**: The Company OS is a Notion page that serves as the root document for all strategic work. Every other strategy document links back to it.
- **GitHub**: If the team is technical, consider mirroring mission/vision/values in a `COMPANY.md` at the repo root so developers see it daily.
- **Vercel**: No direct integration, but the Company OS informs what gets built and deployed.

## Quality Gate
- [ ] Mission is one sentence and excludes things the company does NOT do
- [ ] Vision is ambitious but credible with a time horizon
- [ ] Values are actionable, distinctive, and testable (3-5 max)
- [ ] Decision framework is documented and usable by anyone on the team
- [ ] Operating rhythms defined with frequency, purpose, and participants
- [ ] Documented in Notion as a living document

## Anti-Patterns
- **Generic values** — "integrity" and "excellence" are not values, they are table stakes. If every company would claim it, it is not distinctive.
- **Mission by committee** — mission statements written by committee are bland. One person drafts, the team reacts.
- **Document and forget** — a Company OS only works if it is referenced in actual decisions. Link to it from meeting agendas and decision docs.
- **Too many values** — 3-5 values are memorable. 10 values are wallpaper.
- **No operating rhythms** — values without rhythms are aspirational. Rhythms make them operational.

## Related Skills
- `strategy/positioning` — positioning is the external expression of internal clarity
- `advisory/ceo-advisor` — strategic leadership framing
- `core/decision-logger` — logging decisions against the Company OS framework
- `core/scrum-master` — operating rhythms at the sprint level
