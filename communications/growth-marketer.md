<!-- reconstructed -->
---
name: "growth-marketer"
description: "Holistic growth strategy — acquisition, activation, retention, revenue, and referral across all channels"
workers: ["marketing-strategist"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Growth Marketer

## When to Use
- Building a growth strategy from scratch
- Growth has plateaued and needs new levers
- Connecting marketing, product, and sales for unified growth
- AARRR funnel optimization

## Workflow

### Step 1: Map the AARRR Funnel
| Stage | Definition | Current Metric | Target |
|-------|-----------|---------------|--------|
| **Acquisition** | How do users find us? | Monthly visitors | |
| **Activation** | Do they have a good first experience? | Signup → first action % | |
| **Retention** | Do they come back? | Day 7/30 return rate | |
| **Revenue** | Do they pay? | Free → paid conversion % | |
| **Referral** | Do they tell others? | Referral rate | |

### Step 2: Identify the Bottleneck
Find the stage with the biggest drop-off. That is where to focus.
- If acquisition is low: focus on SEO, content, ads, partnerships
- If activation is low: fix onboarding, reduce friction
- If retention is low: improve product value, engagement loops
- If revenue is low: optimize pricing, paywall, upgrade triggers
- If referral is low: build referral program, make sharing easy

### Step 3: Growth Experiments
For the bottleneck stage, design 3-5 experiments:
```
Experiment: [Name]
Hypothesis: If we [change], then [metric] will [improve] because [reason].
Metric: [Specific metric to track]
Duration: [1-2 weeks]
Success criteria: [X% improvement]
```

### Step 4: Experiment Execution
1. Implement the change (small, isolated)
2. Track the metric (Vercel Analytics, custom events)
3. Run for the defined duration
4. Analyze results
5. Decision: scale, iterate, or kill

### Step 5: Growth Playbook
Document winning experiments in a growth playbook:
- What worked (with data)
- What did not work (save others from repeating)
- Reusable tactics per funnel stage

### Step 6: Monthly Growth Review
Review in Notion:
- Funnel metrics vs. targets
- Experiments run, results, learnings
- Next month's experiment pipeline
- Key growth metric trend

## Stack Context
- **Vercel Analytics**: Funnel metrics and experiment tracking.
- **Next.js**: A/B tests, onboarding flows, and conversion experiments implemented in the app.
- **Supabase**: User behavior tracking and cohort analysis.
- **Resend**: Activation and retention emails.
- **Notion**: Growth playbook, experiment log, and monthly reviews.

## Quality Gate
- [ ] AARRR funnel mapped with current metrics
- [ ] Bottleneck stage identified
- [ ] At least 3 experiments designed per cycle
- [ ] Each experiment has a hypothesis and success criteria
- [ ] Monthly growth review conducted
- [ ] Growth playbook maintained

## Anti-Patterns
- **Optimizing everywhere** — focus on one bottleneck at a time, not all stages simultaneously.
- **No hypothesis** — "let's try this" is not an experiment. State what you expect and why.
- **Too long experiments** — 1-2 weeks for most experiments. Longer wastes time on losers.
- **Ignoring retention** — acquiring users who leave is expensive. Fix retention before scaling acquisition.
- **Growth hacking** — short-term tricks that damage trust or user experience are not growth.

## Related Skills
- `communications/page-cro` — conversion optimization
- `communications/signup-flow-cro` — activation optimization
- `communications/churn-prevention` — retention strategy
- `communications/referral-program` — referral optimization
- `strategy/product-analytics` — measurement infrastructure
