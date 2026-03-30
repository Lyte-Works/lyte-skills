<!-- reconstructed -->
---
name: "sales-enablement"
description: "Sales collateral creation — battle cards, objection handling, pitch decks, and sales process documentation"
workers: ["sales-lead"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Sales Enablement

## When to Use
- Sales team needs updated collateral
- Creating battle cards against competitors
- Building or refining the sales pitch
- Onboarding a new salesperson
- Sales is losing deals and needs better tools

## Workflow

### Step 1: Battle Cards
One card per competitor, covering:
```
# Battle Card: [Competitor Name]

## Quick Summary
[1 sentence: what they do, who they serve]

## Their Strengths
- [Honest assessment]

## Their Weaknesses
- [Where they fall short]

## When We Win Against Them
[Scenarios where our product is clearly better]

## When We Lose
[Scenarios where they have an advantage — be honest]

## Key Talking Points
- "[Customer-facing statement about our advantage]"

## Objection Responses
- "They're cheaper" → [Response]
- "They have [feature] you don't" → [Response]
- "We already use them" → [Response]
```

### Step 2: Pitch Deck
Slide structure:
1. **The Problem** (1 slide): What pain does the audience feel?
2. **The Cost** (1 slide): What happens if they do nothing?
3. **The Solution** (1-2 slides): What we do and how it works
4. **Social Proof** (1 slide): Customers, metrics, testimonials
5. **Differentiators** (1 slide): Why us, not them?
6. **Pricing** (1 slide): Clear, simple options
7. **Next Steps** (1 slide): What to do now

### Step 3: Objection Handling Guide
| Objection | Category | Response |
|-----------|---------|---------|
| "Too expensive" | Price | "[Value statement]. Customers see [ROI metric]." |
| "We're happy with current solution" | Status quo | "What would [specific improvement] mean for your team?" |
| "Need to check with [decision maker]" | Authority | "Happy to join that conversation. What would be most helpful for them?" |
| "Not the right time" | Timing | "When would be better? Happy to reconnect then." |
| "Need more features" | Feature gap | "Which features are must-haves for your use case?" |

### Step 4: Sales Process Documentation
Document the standard sales process:
1. **Lead qualification**: criteria (budget, authority, need, timeline)
2. **Discovery call**: questions to ask, information to gather
3. **Demo**: see sales-engineer skill
4. **Proposal**: template and pricing
5. **Negotiation**: what is negotiable and what is not
6. **Close**: contract and onboarding handoff

### Step 5: Organize in Notion
Create a "Sales Playbook" section in Notion:
- Battle cards (one page per competitor)
- Pitch deck (linked or embedded)
- Objection handling guide
- Sales process documentation
- Case studies and testimonials (linked from content)
- Proposal templates

## Stack Context
- **Notion**: All sales collateral lives in Notion for easy access and updating.
- **Next.js**: Product demo pages and comparison pages on the website.
- **Vercel**: Demo environments via preview deployments.

## Quality Gate
- [ ] Battle cards created for top 3-5 competitors
- [ ] Pitch deck follows the problem-solution-proof structure
- [ ] Objection responses cover top 5 objections
- [ ] Sales process documented end-to-end
- [ ] All collateral organized and accessible in Notion
- [ ] Updated quarterly

## Anti-Patterns
- **Dishonest battle cards** — misrepresenting competitors damages credibility when the prospect checks.
- **Stale collateral** — outdated pricing, features, or competitive info is worse than no collateral.
- **Feature-led pitch** — lead with the customer's problem, not your product's features.
- **No objection prep** — "I'll get back to you on that" to common objections shows lack of preparation.

## Related Skills
- `operations/sales-engineer` — technical sales support
- `strategy/competitive-teardown` — competitive intelligence for battle cards
- `strategy/competitor-alternatives` — positioning against alternatives
- `communications/case-study-builder` — proof points for sales
- `communications/testimonial-collector` — social proof for sales
