<!-- reconstructed -->
---
name: "financial-analyst"
description: "Financial modeling, budgeting, forecasting, and financial reporting for small businesses and startups"
workers: ["financial-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Financial Analyst

## When to Use
- Building a financial model or budget
- Revenue forecasting
- Unit economics analysis
- Preparing financial reports for stakeholders
- Evaluating the financial viability of a project

## Workflow

### Step 1: Revenue Model
Define how revenue works:
| Model | Formula |
|-------|---------|
| SaaS | Customers x ARPU x 12 = ARR |
| Usage-based | Users x Avg Usage x Price/Unit = Revenue |
| Services | Hours x Rate = Revenue |
| E-commerce | Visitors x Conversion Rate x AOV = Revenue |

### Step 2: Cost Structure
| Category | Items | Fixed/Variable |
|----------|-------|---------------|
| Infrastructure | Vercel, Supabase, Resend | Fixed (mostly free tier) |
| People | Team compensation | Fixed |
| Marketing | Ads, tools, content | Variable |
| Operations | Software, legal, accounting | Fixed |

### Step 3: Unit Economics
| Metric | Formula | Healthy Benchmark |
|--------|---------|------------------|
| CAC (Customer Acquisition Cost) | Total sales+marketing spend / New customers | Depends on LTV |
| LTV (Lifetime Value) | ARPU x Avg customer lifespan | LTV > 3x CAC |
| LTV:CAC Ratio | LTV / CAC | > 3:1 |
| Payback period | CAC / Monthly revenue per customer | < 12 months |
| Gross margin | (Revenue - COGS) / Revenue | > 70% for SaaS |

### Step 4: Financial Projections
Build a 12-month projection:
| Month | Revenue | Costs | Profit | Cumulative |
|-------|---------|-------|--------|-----------|
| M1 | | | | |
| M2 | | | | |
| ... | | | | |
| M12 | | | | |

Three scenarios: conservative, base case, optimistic.

### Step 5: Cash Flow Analysis
- Monthly cash in (revenue, investment, other income)
- Monthly cash out (costs, one-time expenses)
- Net cash flow
- Runway: how many months until cash runs out?

### Step 6: Reporting
Monthly financial report in Notion:
- Revenue vs. forecast
- Key metrics (CAC, LTV, churn, MRR)
- Cash position and runway
- Notable changes or risks
- Recommendations

## Stack Context
- **Notion**: Financial models, reports, and dashboards in Notion.
- **Stripe**: Revenue data from Stripe dashboard or API.
- **Supabase**: Customer and usage data for unit economics.
- **Vercel Analytics**: Traffic data for revenue modeling (visitors x conversion = leads).

## Quality Gate
- [ ] Revenue model clearly defined
- [ ] Cost structure documented
- [ ] Unit economics calculated (CAC, LTV, LTV:CAC)
- [ ] 12-month projection with 3 scenarios
- [ ] Cash flow analysis with runway calculation
- [ ] Monthly reporting cadence established

## Anti-Patterns
- **Revenue without costs** — revenue projections without cost modeling are not financial analysis.
- **Single scenario** — only the base case? What if things go worse or better?
- **Ignoring cash flow** — profitable on paper but out of cash is still dead.
- **No unit economics** — growing revenue without knowing CAC and LTV is flying blind.
- **Annual updates only** — financial models need monthly review to stay relevant.

## Related Skills
- `operations/saas-metrics` — SaaS-specific metrics
- `operations/revops` — revenue pipeline analysis
- `advisory/cfo-advisor` — financial strategy advisory
- `strategy/pricing-strategy` — pricing impact on financials
