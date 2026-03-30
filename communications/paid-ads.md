<!-- reconstructed -->
---
name: "paid-ads"
description: "Paid advertising strategy — campaign structure, bidding, targeting, creative strategy, and budget allocation"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Paid Ads

## When to Use
- Launching paid campaigns (Google Ads, LinkedIn Ads, Meta Ads)
- Existing campaigns are underperforming
- Client has budget and needs faster growth than organic
- Testing positioning or messaging with paid validation

## Workflow

### Step 1: Campaign Strategy
| Decision | Answer |
|----------|--------|
| **Goal** | Awareness / Traffic / Leads / Sales |
| **Platform** | Google (intent) / LinkedIn (B2B) / Meta (B2C) / Twitter (tech) |
| **Budget** | Monthly spend |
| **Target audience** | Demographics, interests, behaviors, job titles |
| **Offer** | What are we promoting? (product, free trial, content, tool) |

### Step 2: Campaign Structure
```
Account
└── Campaign (one per goal/offer)
    ├── Ad Group 1 (audience segment or keyword theme)
    │   ├── Ad 1 (creative variation A)
    │   └── Ad 2 (creative variation B)
    └── Ad Group 2 (different segment or theme)
        ├── Ad 1
        └── Ad 2
```

### Step 3: Targeting
**Google Ads**: Target by keyword intent
- Brand keywords: "[Your brand name]" (protect brand searches)
- Competitor keywords: "[Competitor] alternative"
- Problem keywords: "how to [solve problem]"
- Category keywords: "best [category] tool"

**LinkedIn Ads**: Target by professional attributes
- Job titles, seniority, company size, industry
- Matched audiences (email lists, website visitors)

### Step 4: Ad Copy
Follow the copywriting frameworks:
- **Headline**: Outcome + specificity
- **Description**: Problem → solution → CTA
- **CTA**: Clear action ("Start free trial" not "Learn more")

Write 3-5 variations per ad group for testing.

### Step 5: Landing Pages
Every ad must go to a dedicated landing page, not the homepage.
- Message match: the landing page headline should mirror the ad copy
- One CTA per page (matching the campaign goal)
- Remove navigation (no distractions)
- Use the landing-page-generator skill

### Step 6: Measure and Optimize
| Metric | Good | Needs Work |
|--------|------|-----------|
| CTR | >2% (Google Search) | <1% |
| Conversion rate | >3% (landing page) | <1% |
| CPA | Below target | Above target |
| ROAS | >3x | <2x |

Weekly optimization:
- Pause underperforming ads
- Scale winning ads
- Adjust bids and budgets
- Test new creative variations

## Stack Context
- **Next.js**: Dedicated landing pages for each campaign. UTM parameter tracking.
- **Vercel Analytics**: Track ad traffic and conversion events.
- **Notion**: Campaign plans, creative briefs, and performance reports.
- **Tailwind**: Landing page styling.
- **Vercel**: Fast landing page loading improves Quality Score and conversion rate.

## Quality Gate
- [ ] Campaign goal and budget defined
- [ ] Target audience specified (not "everyone")
- [ ] Dedicated landing page per campaign (not homepage)
- [ ] At least 3 ad variations for testing
- [ ] Conversion tracking implemented
- [ ] Weekly optimization cadence established

## Anti-Patterns
- **Sending ads to the homepage** — homepage is not optimized for a specific campaign. Use dedicated landing pages.
- **One ad, no testing** — always run multiple variations.
- **No conversion tracking** — spending money without measuring results is guessing.
- **Set and forget** — ads need weekly optimization. Performance decays without attention.
- **Broad targeting** — narrow targeting with relevant messaging beats broad targeting every time.

## Related Skills
- `communications/ad-creative` — ad copy and visual direction
- `communications/page-cro` — landing page conversion optimization
- `engineering/landing-page-generator` — building campaign landing pages
- `communications/analytics-tracking` — conversion tracking setup
