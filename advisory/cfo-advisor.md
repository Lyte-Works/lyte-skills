<!-- reconstructed -->
---
name: "cfo-advisor"
description: "CFO-level financial strategy — fundraising, financial planning, cash management, and financial governance"
workers: ["financial-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# CFO Advisor

## When to Use
- Financial strategy decisions (fundraising, pricing, cost structure)
- Cash management and runway planning
- Preparing for fundraising or investment
- Financial reporting to the board
- Budget allocation decisions

## Workflow

### Step 1: Financial Health Assessment
| Area | Key Questions |
|------|-------------|
| Revenue | Growing? Predictable? Diversified? |
| Costs | Under control? Fixed vs. variable ratio? |
| Cash | Runway in months? Burn rate? |
| Unit economics | LTV:CAC > 3? Payback < 12 months? |
| Profitability | Path to profitability clear? |

### Step 2: Cash Management
- Calculate monthly burn rate
- Calculate runway (cash / monthly burn)
- Identify levers to extend runway (reduce costs, increase revenue, raise capital)
- Maintain 6+ months runway as safety buffer

### Step 3: Financial Planning
- Annual budget with quarterly breakdown
- Revenue forecast (conservative, base, optimistic)
- Headcount plan aligned with revenue
- Capital expenditure plan
- Contingency reserve (10-15% of budget)

### Step 4: Fundraising Preparation
If pursuing investment:
- Financial model (3-year projection)
- Key metrics deck (MRR, growth, unit economics)
- Use of funds (specific allocation)
- Competitive landscape
- Team and capability overview

### Step 5: Financial Governance
- Monthly financial close and reporting
- Quarterly board reporting
- Annual budget review and refresh
- Audit preparation (when required)
- Segregation of duties for financial transactions

## Stack Context
- **Notion**: Financial reports, budgets, and investor materials in Notion.
- **Stripe**: Revenue data and financial transactions.
- **Supabase**: Customer data for unit economics calculations.

## Quality Gate
- [ ] Financial health assessment completed
- [ ] Runway calculated and monitored
- [ ] Annual budget in place
- [ ] Monthly reporting cadence established
- [ ] Unit economics calculated and tracked
- [ ] Fundraising materials prepared (if applicable)

## Anti-Patterns
- **Ignoring cash** — profitable on paper but out of cash is still dead.
- **No budget** — spending without a budget leads to surprises.
- **Optimistic-only forecasts** — always model conservative scenarios.
- **No financial governance** — as the company grows, financial controls become critical.

## Related Skills
- `operations/financial-analyst` — financial modeling and analysis
- `operations/saas-metrics` — SaaS-specific metrics
- `advisory/ceo-advisor` — aligning financial and business strategy
- `advisory/board-deck-builder` — board presentations
