<!-- reconstructed -->
---
name: "market-research-30day"
description: "30-day automated market scanning and intelligence gathering program"
workers: ["research-analyst"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# 30-Day Market Research

## When to Use
- Entering a new market with limited existing knowledge
- Client needs ongoing competitive intelligence
- Preparing for a strategic planning session
- Before a major product or positioning decision
- Market is shifting and client needs to understand the new landscape

## Workflow

### Week 1: Landscape Mapping (Days 1-7)

**Day 1-2: Define the Market**
- Write a one-sentence market definition
- List 5-10 keywords that define this market
- Identify the primary buying persona

**Day 3-4: Competitor Census**
- Identify all competitors (direct, indirect, emerging)
- Categorize: established leaders, challengers, niche players, new entrants
- Document each in a Notion table: name, URL, positioning, pricing, funding (if known)

**Day 5-7: Content Landscape**
- Identify the top 10 content sources in this market (blogs, newsletters, podcasts, YouTube channels)
- Subscribe to all competitor newsletters
- Follow key voices on LinkedIn and Twitter/X
- Set up alerts for market keywords

### Week 2: Demand Signals (Days 8-14)

**Day 8-9: Search Demand**
- Research keyword volumes for market terms
- Identify trending vs. declining terms
- Map the buyer journey through search: awareness, consideration, decision

**Day 10-11: Community Signals**
- Identify relevant Reddit subreddits, Slack communities, Discord servers, forums
- Scan the last 30 days of discussions for recurring themes, complaints, and requests
- Extract the top 10 pain points mentioned by real users

**Day 12-14: Review Mining**
- Find competitor reviews on G2, Capterra, TrustPilot, app stores
- Extract top 5 praised features and top 5 complaints per competitor
- Identify gaps: what are users asking for that nobody provides?

### Week 3: Trend Analysis (Days 15-21)

**Day 15-17: Industry Reports**
- Find relevant industry reports (even executive summaries are valuable)
- Identify market size estimates and growth rates
- Note any macro trends affecting the market

**Day 18-19: Technology Trends**
- What technology shifts are affecting this market? (AI, automation, mobile, etc.)
- Which competitors are adopting new technology? Which are falling behind?

**Day 20-21: Regulation and Compliance**
- Are there regulatory changes on the horizon?
- How do regulations affect market entry or product design?

### Week 4: Synthesis (Days 22-30)

**Day 22-25: Build the Market Map**
Create a visual market map (2x2 or similar) plotting competitors on dimensions that matter to buyers.

**Day 26-28: Write the Market Brief**
A concise document covering:
1. Market definition and size
2. Key players and positioning
3. Demand signals and unmet needs
4. Technology and regulatory trends
5. Opportunities for the client
6. Recommended strategic moves (3-5 specific recommendations)

**Day 29-30: Present and Discuss**
Walk the client through the brief. Document decisions and next steps in Notion.

## Stack Context
- **Notion**: All research lives in Notion. Use a database for the competitor census (sortable, filterable). Market brief is a Notion page linked from the project hub.
- **Vercel Analytics**: After implementing strategic recommendations, use analytics to track whether the insights translated into measurable website performance changes.
- **Next.js**: If the research reveals content opportunities, coordinate with the content strategy skill to plan content that captures identified demand.

## Quality Gate
- [ ] Market definition is specific (not "the software market")
- [ ] At least 5 competitors cataloged with positioning, pricing, and strengths
- [ ] Community signals gathered from at least 2 real communities
- [ ] Review mining covers at least 3 competitors
- [ ] Market brief includes specific recommendations, not just observations
- [ ] All research documented in Notion with dates and sources

## Anti-Patterns
- **Analysis paralysis** — 30 days is the limit. Do not extend indefinitely. Make recommendations with imperfect information.
- **Secondary sources only** — industry reports are useful but biased. Complement with primary community research (Reddit, reviews, forums).
- **Ignoring small players** — new entrants and niche players often signal where the market is heading.
- **Data without interpretation** — a spreadsheet of competitors is not research. The value is in the synthesis and recommendations.
- **One-time exercise** — market research degrades quickly. Schedule quarterly refreshes of key sections.

## Related Skills
- `strategy/competitive-teardown` — deep-dive on specific competitors identified here
- `strategy/customer-research` — primary research with actual customers
- `strategy/reddit-insights` — focused community signal mining
- `strategy/daily-briefing` — ongoing market intelligence after the 30-day program
- `strategy/positioning` — market research informs positioning decisions
