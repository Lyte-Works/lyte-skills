<!-- reconstructed -->
---
name: "board-deck-builder"
description: "Build investor and board presentations — narrative structure, metrics, and strategic communication"
workers: ["business-strategist"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Board Deck Builder

## When to Use
- Preparing for a board meeting
- Building an investor pitch deck
- Quarterly business review presentation
- Annual strategy presentation

## Workflow

### Step 1: Board Deck Structure (10-12 slides)
1. **Title**: Company, date, meeting type
2. **Dashboard**: Key metrics at a glance (MRR, growth, churn, cash)
3. **Highlights**: Top 3 wins since last meeting
4. **Challenges**: Top 3 issues (be honest)
5. **Revenue**: MRR breakdown, trends, forecast
6. **Product**: Key milestones, roadmap progress
7. **Team**: Hires, departures, org changes
8. **Customers**: Key wins, losses, NPS
9. **Financial**: P&L summary, cash position, runway
10. **Strategic Priorities**: Next quarter focus
11. **Ask**: What you need from the board (advice, connections, capital)

### Step 2: Metrics Dashboard
| Metric | Last Quarter | This Quarter | Target | Status |
|--------|-------------|-------------|--------|--------|
| MRR | | | | |
| Growth rate | | | | |
| Churn | | | | |
| CAC | | | | |
| LTV:CAC | | | | |
| Cash / Runway | | | | |

### Step 3: Narrative Structure
The deck tells a story:
- **Where we were** (last meeting's context)
- **What happened** (results, wins, challenges)
- **Where we are** (current state, honest assessment)
- **Where we're going** (strategy, priorities, targets)
- **What we need** (specific asks)

### Step 4: Honesty Principle
- Lead with bad news, not bury it
- Explain what you are doing about challenges
- Do not spin numbers — board members see through it
- Ask for help on the hardest problems

### Step 5: Preparation
- Send the deck 48 hours before the meeting (board members read beforehand)
- Prepare for 3-5 likely questions
- Have supporting data ready (not in the deck, but accessible)
- Allocate 50% of meeting time for discussion (do not present for the full hour)

## Stack Context
- **Notion**: Deck content drafted in Notion. Metrics pulled from dashboards.
- **Stripe**: Revenue metrics for the financial slides.
- **Vercel Analytics**: Product usage metrics.
- **Supabase**: Customer data for NPS and cohort analysis.

## Quality Gate
- [ ] All 10-12 sections covered
- [ ] Metrics current and accurate
- [ ] Challenges section included (honest)
- [ ] Clear ask from the board
- [ ] Deck sent 48 hours before meeting
- [ ] Discussion questions prepared

## Anti-Patterns
- **All positive** — a deck with no challenges is not credible.
- **Data dump** — 50 slides of charts is not communication. Tell a story with the data.
- **No ask** — every board meeting should end with a specific ask.
- **Presenting the whole time** — if there is no discussion time, the board cannot add value.
- **Last-minute prep** — rushed decks have errors and miss insights. Start a week before.

## Related Skills
- `advisory/ceo-advisor` — strategic context for the deck
- `advisory/cfo-advisor` — financial slides
- `operations/saas-metrics` — metrics for the dashboard
- `strategy/positioning` — narrative framing
