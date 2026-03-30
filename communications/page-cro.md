<!-- reconstructed -->
---
name: "page-cro"
description: "Landing page conversion rate optimization — identify friction, test improvements, and increase conversion"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Page CRO

## When to Use
- Landing page has traffic but low conversion
- Launching a new page and want to optimize from day one
- A/B testing page layouts
- Quarterly conversion optimization review

## Workflow

### Step 1: Audit the Current Page
Score each element:
| Element | Present? | Effective? | Notes |
|---------|----------|-----------|-------|
| Clear headline (outcome-focused) | | | |
| Subheadline (how it works) | | | |
| CTA above the fold | | | |
| Social proof (testimonials, logos) | | | |
| Benefits (not features) | | | |
| Single CTA (not multiple actions) | | | |
| Mobile-optimized | | | |
| Fast loading (<3s) | | | |
| No navigation (no distractions) | | | |
| Objection handling (FAQ or trust signals) | | | |

### Step 2: Identify the Bottleneck
Using Vercel Analytics:
- Where do users drop off? (scroll depth, exit rate)
- Which CTA gets clicks? (custom event tracking)
- What is the bounce rate?
- Mobile vs. desktop conversion difference?

### Step 3: Prioritize Fixes (PIE Framework)
| Fix | Potential (1-5) | Importance (1-5) | Ease (1-5) | PIE Score |
|-----|-----------------|-------------------|-----------|-----------|

Top PIE score items go first.

### Step 4: Common Fixes
| Problem | Fix |
|---------|-----|
| Weak headline | Rewrite with outcome + specificity |
| No CTA above fold | Move CTA higher |
| Multiple CTAs | Remove all but one |
| No social proof | Add testimonials or customer logos |
| Slow loading | Optimize images, reduce client JS |
| Feature-led copy | Rewrite as benefits |
| No urgency | Add genuine scarcity or social proof numbers |
| Form too long | Reduce to essential fields only |
| No mobile optimization | Rebuild mobile-first |

### Step 5: Implement and Test
1. Make one change at a time
2. Track with Vercel Analytics custom events
3. Run for at least 1 week or 100 conversions
4. Compare against baseline
5. Keep winners, iterate on losers

### Step 6: Document
Create a CRO log in Notion:
- Date, change made, hypothesis
- Baseline metric
- Result (improvement, no change, decline)
- Decision (keep, revert, iterate)

## Stack Context
- **Next.js**: Page implemented as Server Component. CTA tracking via `@vercel/analytics`.
- **Tailwind**: Layout changes, visual emphasis on CTA, mobile-first responsive design.
- **Vercel Analytics**: Conversion event tracking and page performance data.
- **Vercel**: Fast load times improve conversion. Server Components minimize JS bundle.

## Quality Gate
- [ ] Current page audited with scoring
- [ ] Bottleneck identified with data (not guesswork)
- [ ] Fixes prioritized by PIE score
- [ ] One change tested at a time
- [ ] Results documented in CRO log
- [ ] Conversion rate improved vs. baseline

## Anti-Patterns
- **Redesigning everything** — test one change at a time. Full redesigns hide what actually worked.
- **No baseline** — measure current conversion before making changes.
- **Gut feeling** — use data to identify problems, not opinions.
- **Testing with no traffic** — need at least 100 conversions per variant for meaningful results.
- **Dark patterns** — tricking users into converting is not CRO. It is deception.

## Related Skills
- `communications/signup-flow-cro` — signup-specific optimization
- `communications/ab-test-setup` — structured A/B testing
- `communications/copywriting` — page copy optimization
- `strategy/marketing-psychology` — psychological principles for conversion
