<!-- reconstructed -->
---
name: "saas-metrics"
description: "SaaS-specific metrics — MRR, ARR, CAC, LTV, churn, NRR, and benchmarking for SaaS businesses"
workers: ["financial-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# SaaS Metrics

## When to Use
- Tracking SaaS business performance
- Benchmarking against industry standards
- Preparing investor or board reporting
- Identifying areas for improvement in a SaaS business

## Workflow

### Step 1: Core SaaS Metrics
| Metric | Formula | Good Benchmark |
|--------|---------|---------------|
| **MRR** | Sum of all monthly recurring revenue | Growing month-over-month |
| **ARR** | MRR x 12 | |
| **New MRR** | MRR from new customers this month | |
| **Expansion MRR** | MRR increase from existing customers (upgrades) | |
| **Churned MRR** | MRR lost from cancellations | |
| **Net New MRR** | New + Expansion - Churned | Positive = growing |
| **Logo Churn** | Customers lost / Total customers | < 5%/month |
| **Revenue Churn** | MRR lost / Total MRR | < 2%/month |
| **NRR (Net Revenue Retention)** | (Starting MRR + Expansion - Churn) / Starting MRR | > 100% |

### Step 2: Growth Metrics
| Metric | Formula | Good Benchmark |
|--------|---------|---------------|
| **MoM Growth** | (MRR this month - MRR last month) / MRR last month | > 10% early stage |
| **Quick Ratio** | (New MRR + Expansion MRR) / Churned MRR | > 4 |
| **Months to Recover CAC** | CAC / (ARPU x Gross Margin) | < 12 months |

### Step 3: Efficiency Metrics
| Metric | Formula | Good Benchmark |
|--------|---------|---------------|
| **CAC** | Total S&M spend / New customers | Depends on LTV |
| **LTV** | ARPU / Monthly churn rate | LTV > 3x CAC |
| **LTV:CAC** | LTV / CAC | > 3:1 |
| **Burn Multiple** | Net burn / Net new ARR | < 2x |
| **Rule of 40** | Revenue growth % + Profit margin % | > 40% |

### Step 4: Dashboard
Create a SaaS metrics dashboard in Notion:
```
# SaaS Metrics Dashboard — [Month/Year]

## MRR Breakdown
| Component | Amount | Change |
|-----------|--------|--------|
| Starting MRR | | |
| + New MRR | | |
| + Expansion MRR | | |
| - Churned MRR | | |
| = Ending MRR | | |

## Key Metrics
| Metric | Value | Trend | Status |
|--------|-------|-------|--------|
| NRR | | ↑↓→ | 🟢🟡🔴 |
| Logo Churn | | ↑↓→ | 🟢🟡🔴 |
| LTV:CAC | | ↑↓→ | 🟢🟡🔴 |
| Quick Ratio | | ↑↓→ | 🟢🟡🔴 |
```

### Step 5: Data Sources
| Data | Source |
|------|--------|
| Revenue / MRR | Stripe Dashboard or API |
| Customer count | Supabase users table |
| Churn events | Stripe subscription webhooks |
| Marketing spend | Notion + ad platform dashboards |
| Usage data | Supabase + Vercel Analytics |

### Step 6: Monthly Review
Review metrics monthly with leadership:
- What improved and why?
- What declined and why?
- Where is the biggest lever for improvement?
- Action items for next month

## Stack Context
- **Stripe**: Revenue data, subscription events, churn data.
- **Supabase**: Customer data, usage metrics.
- **Vercel Analytics**: Acquisition and engagement data.
- **Notion**: Metrics dashboard and monthly reports.

## Quality Gate
- [ ] All core SaaS metrics calculated
- [ ] Dashboard created and accessible
- [ ] Data sources identified and connected
- [ ] Monthly review cadence established
- [ ] Benchmarks compared to industry standards
- [ ] Action items generated from each review

## Anti-Patterns
- **Vanity MRR** — counting annual payments as monthly revenue overstates MRR.
- **Ignoring churn** — celebrating new MRR while ignoring churned MRR masks problems.
- **No segmentation** — overall metrics hide segment-level problems. Break down by plan, source, or cohort.
- **Metric overload** — 5-7 key metrics, not 30. Focus on what drives decisions.
- **Static dashboard** — a dashboard from 3 months ago is history, not management.

## Related Skills
- `operations/financial-analyst` — broader financial analysis
- `operations/revops` — pipeline and revenue alignment
- `communications/churn-prevention` — improving churn metrics
- `strategy/product-analytics` — product usage metrics
