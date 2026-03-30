<!-- reconstructed -->
---
name: "competitive-teardown"
description: "Structured competitive analysis framework with deliverables for tearing down competitor strategy, product, and messaging"
workers: ["business-strategist", "research-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Competitive Teardown

## When to Use
- Before positioning or re-positioning work
- Client is losing deals to a specific competitor
- New competitor enters the market
- Preparing sales battle cards
- Evaluating market entry opportunity

## Workflow

### Step 1: Select Target Competitor
Pick one competitor per teardown. Do not try to analyze the entire market at once.

### Step 2: Product Teardown
Document in a structured table:
| Dimension | Competitor | Our Client | Gap |
|-----------|-----------|------------|-----|
| Core offering | | | |
| Pricing model | | | |
| Target customer | | | |
| Key features | | | |
| Integrations | | | |
| Onboarding experience | | | |
| Support model | | | |

### Step 3: Messaging Teardown
Analyze the competitor's website and marketing:
- **Homepage hero**: What claim do they lead with?
- **Value propositions**: What 3-5 benefits do they emphasize?
- **Social proof**: What kind of proof do they use (logos, testimonials, case studies, numbers)?
- **CTAs**: What action do they push? (free trial, demo, contact sales)
- **Tone**: Technical vs. casual? Fear-based vs. aspirational?

### Step 4: Channel Teardown
Where and how the competitor acquires customers:
- **SEO**: What keywords do they rank for? What content do they produce?
- **Paid**: Are they running ads? On which platforms? What messaging?
- **Social**: Which platforms are active? What content format? Engagement levels?
- **Email**: Sign up for their list. Document the welcome sequence.
- **Partnerships**: Who do they integrate with or co-market with?

### Step 5: Strengths and Weaknesses
Based on Steps 2-4, summarize:
- **3 things they do better than our client** (be honest)
- **3 things our client does better** (be specific)
- **3 gaps or opportunities** (things neither does well)

### Step 6: Strategic Recommendations
For each gap or weakness identified:
- Can the client exploit this? How?
- What would it cost (time, money, effort)?
- Priority: high / medium / low

### Step 7: Document in Notion
Create a "Competitive Teardown: [Competitor Name]" page with all sections above. Tag with date for freshness tracking.

## Stack Context
- **Notion**: Teardown documents live in the client's Notion workspace under a "Competitive Intelligence" section.
- **Next.js / Vercel**: When teardown reveals messaging gaps, the frontend worker uses findings to improve the client's website copy, page structure, and CTAs.
- **Vercel Analytics**: Compare client's site metrics against competitor benchmarks identified in the teardown.

## Quality Gate
- [ ] Single competitor per teardown (not a market overview)
- [ ] Product comparison table is complete with specific details, not vague claims
- [ ] Messaging analysis references actual competitor copy (with URLs/screenshots)
- [ ] Channel analysis includes at least 3 channels
- [ ] Strengths section includes honest acknowledgment of competitor advantages
- [ ] Recommendations are prioritized and actionable
- [ ] Documented in Notion with date stamp

## Anti-Patterns
- **Confirmation bias** — do not start with the conclusion that the client is better. Honest assessment is the point.
- **Stale data** — a teardown older than 6 months is unreliable. Date-stamp everything.
- **Too many competitors at once** — do one teardown per competitor. Comparing 5 competitors in one doc creates noise, not signal.
- **Feature-only analysis** — features are the least durable differentiator. Focus on positioning, messaging, and go-to-market strategy.
- **Ignoring the customer perspective** — a teardown that only looks at what the competitor says, not what their customers say (reviews, forums, social), misses the real story.

## Related Skills
- `strategy/positioning` — teardown findings directly inform positioning work
- `strategy/competitor-alternatives` — focused on positioning against specific alternatives
- `strategy/customer-research` — customer perspective on competitors
- `strategy/reddit-insights` — community signals about competitors
- `operations/sales-enablement` — teardown outputs feed into battle cards
