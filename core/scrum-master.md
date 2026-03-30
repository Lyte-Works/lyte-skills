<!-- reconstructed -->
---
name: "scrum-master"
description: "Sprint ceremony facilitation — standups, planning, reviews, retrospectives, and agile process management"
workers: ["product-manager"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Scrum Master

## When to Use
- Running agile sprints for a development team
- Facilitating sprint ceremonies
- Improving team velocity and predictability
- Removing blockers and impediments
- Adapting agile practices to a small team

## Workflow

### Step 1: Sprint Setup
| Parameter | Value |
|-----------|-------|
| Sprint length | 1-2 weeks (1 week for small teams) |
| Sprint goal | One sentence describing the sprint's purpose |
| Team capacity | Account for PTO, meetings, and operational work |
| Velocity | Average story points completed in recent sprints |

### Step 2: Sprint Ceremonies

**Sprint Planning** (start of sprint):
- Review sprint goal
- Select items from prioritized backlog
- Estimate effort (story points or T-shirt sizes)
- Assign items
- Confirm: does selected work fit in sprint capacity?
- Duration: 1 hour for a 1-week sprint

**Daily Standup** (daily, 15 min max):
Each person answers:
1. What did I complete since last standup?
2. What am I working on today?
3. Any blockers?

Rules: stand up, 15 minutes max, detailed discussions happen after standup.

**Sprint Review** (end of sprint):
- Demo completed work
- Stakeholder feedback
- Accept or reject deliverables
- Duration: 30-60 minutes

**Sprint Retrospective** (end of sprint, after review):
- What went well? (keep doing)
- What could improve? (change)
- What will we commit to changing next sprint? (one action item minimum)
- Duration: 30 minutes

### Step 3: Sprint Board
Use a Notion board with columns:
- **Backlog**: Prioritized, ready for sprint
- **To Do**: Selected for this sprint
- **In Progress**: Currently being worked on
- **In Review**: PR submitted, waiting for review
- **Done**: Completed and accepted

### Step 4: Facilitation Tips
- **Protect the sprint**: No new items mid-sprint unless critical
- **Remove blockers**: If someone is stuck, help immediately
- **Enforce timebox**: Ceremonies that run long lose effectiveness
- **Focus on outcomes**: "What value did we deliver?" not "How busy were we?"
- **Keep it lightweight**: Adapt ceremonies to team size. 2-person team does not need a 2-hour planning session.

### Step 5: Metrics
| Metric | Purpose | Track |
|--------|---------|-------|
| Velocity | Predictability | Story points per sprint (average of last 3) |
| Sprint completion | Commitment reliability | % of planned items completed |
| Cycle time | Speed | Days from "In Progress" to "Done" |
| Blocker frequency | Process health | Number of blockers per sprint |

### Step 6: Adapt for Small Teams
For teams of 1-3 people:
- Sprint planning: 15-30 minutes
- Standup: async in Notion or Slack
- Review: informal demo + stakeholder check
- Retro: 15 minutes, focus on one improvement
- Board: simplified (To Do → Doing → Done)

## Stack Context
- **Notion**: Sprint board, backlog, and ceremony documentation in Notion.
- **GitHub**: Sprint items linked to GitHub Issues. PRs move items from "In Progress" to "In Review."
- **Vercel**: Preview deployments for sprint review demos.

## Quality Gate
- [ ] Sprint ceremonies scheduled and consistent
- [ ] Sprint goal defined for every sprint
- [ ] Board maintained and current
- [ ] Retrospective produces at least one action item
- [ ] Velocity tracked over 3+ sprints
- [ ] Ceremonies adapted to team size

## Anti-Patterns
- **Ceremony theater** — running standups where everyone just reads their Notion board is wasted time.
- **No retrospective** — the retro is how the team improves. Skipping it means stagnation.
- **Over-committing** — planning more than the team can deliver erodes trust and morale.
- **No sprint goal** — a sprint without a goal is just a list of tasks. The goal provides focus.
- **Heavy process for small teams** — 2 people do not need a 2-hour planning session. Scale process to team size.

## Related Skills
- `strategy/agile-product-owner` — product ownership within sprints
- `strategy/product-manager` — feature specs for the backlog
- `engineering/qa-engineer` — quality assurance for sprint deliverables
- `core/decision-logger` — logging sprint decisions
