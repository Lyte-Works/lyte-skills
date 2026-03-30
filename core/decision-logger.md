<!-- reconstructed -->
---
name: "decision-logger"
description: "Structured decision recording — capture decisions with context, reasoning, alternatives, and outcomes"
workers: ["knowledge-manager"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Decision Logger

## When to Use
- A significant decision has been made (strategy, architecture, hiring, process)
- Team is debating a decision and needs structured evaluation
- Onboarding someone who needs to understand past decisions
- Reviewing past decisions to learn and improve

## Workflow

### Step 1: Decision Record Template
```
# Decision: [Clear, descriptive title]

**Date**: [When the decision was made]
**Decision maker**: [Who made the final call]
**Status**: Proposed / Accepted / Superseded / Deprecated

## Context
[What situation prompted this decision? What problem were we solving?]

## Decision
[What did we decide? State it clearly in 1-2 sentences.]

## Alternatives Considered
| Alternative | Pros | Cons | Why Not |
|------------|------|------|---------|
| [Option A] | | | |
| [Option B] | | | |
| [Do nothing] | | | |

## Reasoning
[Why did we choose this option over the alternatives?]

## Consequences
- [Expected positive outcome]
- [Expected risk or trade-off]
- [What this commits us to]

## Review Date
[When should we revisit this decision?]
```

### Step 2: When to Log
Log decisions that:
- Affect multiple people or teams
- Are hard to reverse
- Involve significant investment (time, money, resources)
- Will be questioned later by people not in the room
- Set a precedent for future decisions

Do NOT log:
- Routine operational choices
- Decisions that are easily reversible
- Personal preferences that do not affect others

### Step 3: Decision Database
Create a Notion database "Decision Log" with properties:
- Title
- Date
- Decision maker
- Status (Proposed, Accepted, Superseded, Deprecated)
- Category (Strategy, Engineering, Operations, People, Finance)
- Review date
- Related decisions (relation to other entries)

### Step 4: Review Process
- Set review dates for significant decisions
- At review time: is the decision still valid? Did the expected outcomes materialize?
- If circumstances changed: update status to Superseded and create a new decision record

### Step 5: Use the Log
- **Onboarding**: New team members read recent decision records to understand why things are the way they are
- **Debate**: When re-debating a past decision, reference the original record first
- **Learning**: Quarterly review of decision outcomes to improve future decision-making

## Stack Context
- **Notion**: Decision log database in Notion. Linked from project pages and meeting notes.
- **GitHub**: For engineering decisions, use ADRs (Architecture Decision Records) in the repo AND log in Notion for cross-team visibility.

## Quality Gate
- [ ] Decision record follows the template
- [ ] At least 2 alternatives considered (including "do nothing")
- [ ] Reasoning clearly explains why this option was chosen
- [ ] Consequences documented (positive and negative)
- [ ] Review date set
- [ ] Added to the Notion decision log database

## Anti-Patterns
- **Logging everything** — decision fatigue for documentation. Only log significant decisions.
- **No alternatives** — a decision record with one option is not a decision, it is a declaration.
- **No consequences** — every decision has trade-offs. Document them.
- **Write and forget** — decision records need review dates. Unreviewed decisions become stale assumptions.
- **Hindsight editing** — do not edit past decisions to look prescient. Add a "Retrospective" section instead.

## Related Skills
- `core/vault-cleanup` — organizing the decision log
- `strategy/company-os` — decision framework
- `engineering/senior-architect` — ADRs for technical decisions
- `advisory/ceo-advisor` — strategic decision-making
