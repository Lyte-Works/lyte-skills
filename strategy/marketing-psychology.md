<!-- reconstructed -->
---
name: "marketing-psychology"
description: "Behavioral psychology frameworks for marketing — cognitive biases, persuasion principles, and decision-making patterns"
workers: ["research-analyst", "marketing-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Marketing Psychology

## When to Use
- Designing landing pages or pricing pages
- Writing conversion-focused copy
- Building onboarding flows
- Designing referral or loyalty programs
- Any situation where understanding human decision-making improves outcomes

## Workflow

### Step 1: Identify the Decision Point
What specific decision are you trying to influence?
- Buy vs. not buy
- Sign up vs. leave
- Upgrade vs. stay on free
- Refer vs. not refer
- Open email vs. ignore

### Step 2: Select Applicable Principles
Choose 2-3 principles that apply to the specific decision point. Do not try to use all of them at once.

**Core Principles:**

| Principle | Definition | Application |
|-----------|-----------|-------------|
| Social Proof | People follow the behavior of others | Testimonials, customer counts, "most popular" badges |
| Scarcity | Limited availability increases perceived value | Limited-time offers, seat caps, countdown timers |
| Anchoring | First number seen becomes the reference point | Show the highest price first on pricing pages |
| Loss Aversion | Losing something feels worse than gaining it | Free trials (loss of access), "don't miss out" framing |
| Reciprocity | People feel obligated to return favors | Free tools, free content, generous free tiers |
| Authority | People trust credible experts | Expert endorsements, certifications, data-backed claims |
| Commitment/Consistency | People align future actions with past behavior | Small initial commitments that lead to larger ones |
| Default Effect | People stick with the default option | Pre-select the recommended plan, opt-in defaults |
| Paradox of Choice | Too many options leads to no decision | Limit choices to 3 options, recommend one clearly |
| Endowment Effect | People value what they already have | "Your custom plan," personalization, saved progress |

### Step 3: Design the Implementation
For each selected principle, design a specific implementation:
- What element on the page or in the flow applies this principle?
- Where exactly does it appear?
- What is the expected impact on the decision?

### Step 4: Review for Ethics
Before implementing, check:
- [ ] Are we being transparent? (no dark patterns)
- [ ] Would we be comfortable if the customer knew we used this technique?
- [ ] Does this help the customer make a better decision, or just a faster one?
- [ ] Are we creating genuine value, or manufacturing urgency?

**Hard rule**: If the technique requires deception to work, do not use it. Alignment demands transparency.

### Step 5: Implement and Measure
- Implement the changes in the Next.js application
- Set up measurement in Vercel Analytics or via event tracking
- Compare before/after conversion rates
- If a technique does not improve outcomes, remove it

## Stack Context
- **Next.js**: Psychology principles are implemented as UI patterns in React components. Social proof components, pricing page layouts with anchoring, onboarding flows with commitment patterns.
- **Tailwind CSS**: Visual emphasis (color, size, weight) is how you direct attention. Use Tailwind utilities to create visual hierarchy that supports the psychological principle.
- **Vercel Analytics**: Measure the impact of each implementation. Track conversion events.
- **Supabase**: If personalizing based on user behavior (endowment effect), store user state in Supabase.

## Quality Gate
- [ ] Specific decision point identified (not vague "improve conversions")
- [ ] 2-3 principles selected with clear rationale
- [ ] Each principle has a specific, concrete implementation
- [ ] Ethics review completed — no dark patterns
- [ ] Measurement plan defined before implementation
- [ ] Changes are transparent and honest

## Anti-Patterns
- **Dark patterns** — scarcity that is fake, urgency that is manufactured, opt-outs that are hidden. These violate alignment principles and erode trust.
- **Principle stacking** — using 5+ principles at once creates a manipulative experience. Pick 2-3.
- **Psychology without value** — if the product does not deliver real value, no amount of psychological optimization will sustain growth.
- **Copy-paste application** — each principle must be adapted to the specific context. A countdown timer on a SaaS pricing page (where there is no real deadline) is dishonest.
- **Ignoring the ethics check** — skipping Step 4 is how good products become dark-pattern-laden conversion machines.

## Related Skills
- `communications/page-cro` — applying psychology to landing page optimization
- `communications/signup-flow-cro` — psychology in signup flows
- `communications/copywriting` — persuasive writing using psychological principles
- `strategy/pricing-strategy` — anchoring and framing in pricing
- `communications/ab-test-setup` — testing psychological implementations
