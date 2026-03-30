<!-- reconstructed -->
---
name: "reddit-insights"
description: "Mine Reddit communities for authentic customer pain points, language, competitive intelligence, and market signals"
workers: ["research-analyst"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Reddit Insights

## When to Use
- Need unfiltered customer language for copywriting or positioning
- Researching pain points in a market before building a product or feature
- Looking for competitive intelligence (what real users say about competitors)
- Validating assumptions about customer needs
- Building a voice-of-customer bank from organic discussions

## Workflow

### Step 1: Identify Relevant Subreddits
- Search Reddit for 5-10 subreddits where the target audience discusses problems related to the client's space
- Include: niche subreddits (most valuable), industry subreddits, and 1-2 broad ones
- Document each subreddit with subscriber count and activity level

### Step 2: Define Search Queries
Create 10-15 search queries combining:
- Problem-oriented: "frustrated with," "looking for," "can't figure out," "help me"
- Solution-oriented: "switched to," "finally found," "recommend," "best tool for"
- Competitor-oriented: "[competitor name] alternative," "[competitor name] review"
- Category-oriented: "[category] recommendations," "what do you use for [job]"

### Step 3: Extract Insights
For each relevant thread, capture:
- **Direct quote** (exact user language)
- **Pain point** (the underlying problem)
- **Context** (their role, company size, situation)
- **Sentiment** (frustrated, hopeful, satisfied, angry)
- **Thread engagement** (upvotes, comment count — indicates resonance)

### Step 4: Pattern Analysis
Group extracted insights into themes:
1. **Top pain points** — ranked by frequency and intensity
2. **Common language** — exact words and phrases users use (VoC gold)
3. **Competitive sentiment** — what users love and hate about alternatives
4. **Unmet needs** — things users want that nobody provides
5. **Trigger events** — what situations make people start looking for solutions

### Step 5: Create Deliverables

**VoC Bank Update**: Add Reddit quotes to the Voice-of-Customer bank in Notion, tagged with source and date.

**Insight Report**: A Notion page summarizing:
- Top 5 pain points with supporting quotes
- Top 5 competitive insights
- 3 content ideas based on real questions people are asking
- 3 positioning angles based on language patterns

### Step 6: Ongoing Monitoring
Set a reminder to repeat this process monthly for high-value subreddits. Market sentiment shifts — stale Reddit research loses value quickly.

## Stack Context
- **Notion**: All insights documented in Notion. VoC bank is a Notion database with fields for quote, source, theme, sentiment, and date.
- **Next.js / Content**: Reddit insights directly inform blog content topics and landing page copy. Use exact customer language in hero headlines and feature descriptions.
- **Vercel Analytics**: After implementing copy changes based on Reddit insights, monitor conversion and engagement metrics.

## Quality Gate
- [ ] At least 5 relevant subreddits identified
- [ ] At least 30 individual insights extracted (quotes with context)
- [ ] Insights organized into themes (not just a list of quotes)
- [ ] VoC bank updated with new entries
- [ ] Insight report includes actionable recommendations (not just observations)
- [ ] All quotes attributed with links and dates

## Anti-Patterns
- **Cherry-picking** — do not only collect quotes that confirm existing beliefs. Include surprising and contradictory insights.
- **Ignoring context** — a complaint from a Fortune 500 enterprise user may not apply to small-business clients. Note the context.
- **Paraphrasing** — the value is in the exact language. Do not rewrite quotes into corporate-speak.
- **One-time mining** — Reddit sentiment shifts. Repeat monthly or quarterly.
- **Violating community norms** — this is for research, not for posting promotional content in subreddits.

## Related Skills
- `strategy/customer-research` — Reddit insights complement formal interviews
- `strategy/market-research-30day` — Reddit is one source within broader market research
- `communications/voice-extractor` — extracting brand voice patterns
- `communications/copywriting` — VoC bank feeds directly into copy
- `communications/content-idea-generator` — Reddit questions inspire content
