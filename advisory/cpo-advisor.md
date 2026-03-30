<!-- reconstructed -->
---
name: "cpo-advisor"
description: "CPO-level product leadership — product vision, roadmap strategy, product-market fit, and product organization"
workers: ["product-manager"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# CPO Advisor

## When to Use
- Product strategy at the executive level
- Product-market fit assessment
- Product organization design
- Balancing customer requests with product vision
- Product leadership challenges

## Workflow

### Step 1: Product-Market Fit Assessment
Use Sean Ellis's PMF survey: "How would you feel if you could no longer use [product]?"
- >40% say "Very disappointed" = PMF achieved
- <40% = keep iterating on core value

### Step 2: Product Vision Alignment
- Is the product vision clear to the entire company?
- Does every feature on the roadmap connect to the vision?
- Are we saying "no" to requests that do not align?

### Step 3: Product Organization
| Stage | Structure |
|-------|----------|
| Pre-PMF | Founder + 1-2 engineers. No PM needed. |
| Post-PMF, pre-scale | 1 PM, focused on iteration |
| Scaling | PM per product area/team |
| Mature | Product teams with PM, design, engineering |

### Step 4: Roadmap Governance
- Quarterly roadmap aligned with business goals
- Input from customers, sales, support, and data
- Clear criteria for what makes it onto the roadmap
- Regular communication to stakeholders

### Step 5: Product Metrics
| Metric | Purpose |
|--------|---------|
| Activation rate | Are new users finding value? |
| Engagement (DAU/MAU) | Are users coming back? |
| NPS/CSAT | Are users satisfied? |
| Feature adoption | Are new features being used? |
| Revenue per user | Is the product monetizing? |

## Stack Context
- **Notion**: Product strategy, roadmaps, and OKRs.
- **Vercel Analytics**: Product usage metrics.
- **Supabase**: User behavior data for product decisions.

## Quality Gate
- [ ] PMF assessed with quantitative data
- [ ] Product vision documented and communicated
- [ ] Roadmap governance process established
- [ ] Product metrics tracked
- [ ] Product organization aligned with company stage

## Anti-Patterns
- **Building what everyone asks for** — customer requests are inputs, not the roadmap.
- **No PMF check** — adding features to a product nobody wants does not fix PMF.
- **PM too early** — pre-PMF, the founder should be the PM.
- **Feature factory** — shipping features without measuring impact.

## Related Skills
- `strategy/product-manager` — PM execution
- `strategy/senior-pm` — strategic product management
- `strategy/product-analytics` — product measurement
- `advisory/ceo-advisor` — business-product alignment
