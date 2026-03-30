<!-- reconstructed -->
---
name: "revops"
description: "Revenue operations — marketing-to-sales handoff, pipeline management, and revenue process alignment"
workers: ["sales-lead"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# RevOps

## When to Use
- Marketing generates leads but sales does not close them (handoff problem)
- Pipeline lacks visibility or consistency
- Revenue forecasting is unreliable
- Aligning marketing, sales, and customer success

## Workflow

### Step 1: Define the Revenue Funnel
```
Marketing: Visitor → Lead → MQL (Marketing Qualified Lead)
Sales: MQL → SQL (Sales Qualified Lead) → Opportunity → Customer
Success: Customer → Expansion → Advocate
```

### Step 2: Lead Qualification Criteria
**MQL criteria** (marketing hands off when):
- Visited pricing page
- Downloaded a resource
- Requested a demo
- Company fits ICP (ideal customer profile)

**SQL criteria** (sales accepts when):
- Budget confirmed
- Authority identified
- Need validated
- Timeline established (BANT)

### Step 3: Handoff Process
| Step | Owner | Action | Tool |
|------|-------|--------|------|
| Lead captured | Marketing | Score and qualify | Supabase + custom logic |
| MQL flagged | Marketing | Notify sales | Resend (email notification) |
| Sales accepts | Sales | Move to SQL, begin outreach | Notion CRM |
| Meeting booked | Sales | Discovery call | Calendar + Notion |
| Proposal sent | Sales | Proposal in Notion | Notion + contract-writer |
| Closed won | Sales | Notify team, begin onboarding | Resend + Notion |

### Step 4: Pipeline Management
Track in a Notion database:
| Property | Purpose |
|----------|---------|
| Company name | Identification |
| Contact | Primary contact |
| Stage | Lead → MQL → SQL → Proposal → Negotiation → Won/Lost |
| Value | Expected revenue |
| Close date | Expected close date |
| Source | How they found us |
| Next action | What needs to happen next |
| Owner | Who is responsible |

### Step 5: Revenue Metrics
| Metric | Formula | Frequency |
|--------|---------|-----------|
| Pipeline value | Sum of all active opportunities | Weekly |
| Win rate | Won / (Won + Lost) | Monthly |
| Average deal size | Total revenue / Number of deals | Monthly |
| Sales cycle length | Average days from MQL to close | Monthly |
| Lead-to-close rate | Closed won / Total leads | Monthly |

### Step 6: Monthly Revenue Review
Report in Notion:
- Pipeline value and changes
- Win/loss analysis
- Lead source performance
- Forecast for next month
- Process improvements needed

## Stack Context
- **Notion**: CRM (pipeline database), lead tracking, and revenue reports.
- **Supabase**: Lead scoring and qualification logic (if building a custom solution).
- **Resend**: Lead notification emails, handoff alerts.
- **Vercel Analytics**: Track lead source attribution (UTM parameters).
- **Next.js**: Lead capture forms with source tracking.

## Quality Gate
- [ ] Revenue funnel defined with stages
- [ ] MQL and SQL criteria documented
- [ ] Handoff process established between marketing and sales
- [ ] Pipeline tracked in Notion
- [ ] Key revenue metrics defined and measured
- [ ] Monthly revenue review conducted

## Anti-Patterns
- **No handoff criteria** — marketing and sales arguing about lead quality means criteria are not defined.
- **No pipeline visibility** — if leadership cannot see the pipeline, they cannot forecast or help.
- **Vanity leads** — 1000 email signups that never convert are not leads. Qualify.
- **No win/loss analysis** — without understanding why deals are won or lost, you cannot improve.

## Related Skills
- `operations/sales-enablement` — sales tools and collateral
- `operations/cold-outreach-sequence` — top-of-funnel pipeline building
- `operations/saas-metrics` — SaaS-specific revenue metrics
- `operations/financial-analyst` — revenue forecasting
