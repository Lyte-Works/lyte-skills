<!-- reconstructed -->
---
name: "daily-briefing"
description: "Build ongoing market intelligence briefings synthesizing news, competitor moves, and industry signals"
workers: ["research-analyst"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Daily Briefing

## When to Use
- Client needs ongoing market awareness (not a one-time report)
- Industry is fast-moving and competitive landscape shifts frequently
- Client leadership wants a concise daily or weekly intelligence summary
- After completing a 30-day market research program, to maintain awareness

## Workflow

### Step 1: Define Briefing Scope
Work with the client to define:
- **Competitors to track** (3-5 max for a daily briefing)
- **Keywords and topics** (5-10 terms that define the market)
- **News sources** (industry publications, blogs, social accounts)
- **Frequency**: daily (for fast markets) or weekly (for most businesses)

### Step 2: Set Up Signal Sources
Establish monitoring for:
- **Competitor websites**: product pages, pricing pages, blog (check weekly for changes)
- **Competitor social**: LinkedIn company pages, Twitter/X accounts
- **Industry news**: Subscribe to relevant newsletters, RSS feeds
- **Community signals**: Reddit, Slack groups, forums (weekly scan)
- **Search trends**: Monitor keyword ranking changes

### Step 3: Briefing Template
Each briefing follows this structure:

```
# [Client Name] — Market Briefing — [Date]

## Top Signal
[The single most important thing to know today. One paragraph.]

## Competitor Moves
- [Competitor A]: [What they did and why it matters]
- [Competitor B]: [What they did and why it matters]

## Industry News
- [Headline]: [One-sentence summary + link]
- [Headline]: [One-sentence summary + link]

## Community Signals
- [Key discussion or trend from Reddit/forums/communities]

## Recommendation
[One actionable thing the client should consider based on today's signals]

---
*Sources: [links]*
```

### Step 4: Deliver
- Create the briefing as a Notion page in a "Market Intelligence" section
- For daily briefings, create a new entry each day in a Notion database
- For weekly briefings, create a new entry each Monday
- Optional: send a summary via email using Resend

### Step 5: Monthly Synthesis
At the end of each month, create a "Monthly Intelligence Summary" that:
- Highlights the top 5 signals from the month
- Identifies emerging trends
- Updates the competitive landscape if anything has shifted
- Recommends strategic adjustments

## Stack Context
- **Notion**: Briefings are entries in a Notion database with properties for date, priority, and status. Monthly summaries are separate pages that link to individual briefings.
- **Resend**: If the client wants email delivery, send briefing summaries via a Next.js API route connected to Resend.
- **Next.js**: If building a client-facing intelligence dashboard, create a simple page that pulls from the Notion API or Supabase.

## Quality Gate
- [ ] Briefing scope defined with specific competitors, keywords, and sources
- [ ] Template used consistently for every briefing
- [ ] Each briefing includes at least one actionable recommendation
- [ ] Sources are linked (not just claims)
- [ ] Monthly synthesis completed and shared with client
- [ ] Briefings delivered on schedule

## Anti-Patterns
- **Information overload** — a briefing that is 5 pages long is not a briefing, it is a report. Keep it scannable.
- **No "so what"** — news without interpretation is just noise. Always include a recommendation.
- **Tracking too many competitors** — 3-5 is the limit for a useful daily briefing. More creates noise.
- **Stale sources** — review and update signal sources monthly. Sources go inactive, new ones emerge.
- **Missing context** — always explain why a signal matters to the specific client, not why it is interesting in general.

## Related Skills
- `strategy/market-research-30day` — the initial research that feeds into ongoing briefings
- `strategy/competitive-teardown` — deep dives triggered by briefing signals
- `strategy/reddit-insights` — community signal mining for briefing content
- `communications/newsletter` — similar format skills for external-facing content
