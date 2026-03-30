<!-- reconstructed -->
---
name: "pricing-strategy"
description: "Conversion-focused pricing strategy including models, tiers, anchoring, and pricing page optimization"
workers: ["business-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Pricing Strategy

## When to Use
- New product or service needs pricing
- Current pricing is not converting
- Client wants to add tiers, change model, or raise prices
- Competitor undercuts on price
- Client asks "how should we price this?"

## Workflow

### Step 1: Understand the Value
Before setting a price, answer:
- What is the measurable outcome the customer gets? (revenue increase, time saved, cost reduced)
- What is that outcome worth to the customer in dollars?
- What are customers paying for alternatives? (from competitor-alternatives analysis)

### Step 2: Choose a Pricing Model
| Model | Best For | Example |
|-------|----------|---------|
| Flat rate | Simple products with one use case | $49/month |
| Tiered | Products with multiple segments | Free / Pro / Enterprise |
| Per-seat | Collaboration tools | $12/user/month |
| Usage-based | Infrastructure, API, variable consumption | $0.01/request |
| One-time | Digital products, templates, courses | $199 |
| Freemium | Products where free usage drives viral growth | Free tier + paid upgrade |

Pick the model that matches how the customer receives value. If they get more value as they use more, usage-based. If teams benefit, per-seat.

### Step 3: Set Price Points
Use these anchoring techniques:
1. **Value-based anchor**: Price at 10-20% of the measurable value delivered
2. **Competitor anchor**: Position relative to alternatives (cheaper, same, premium)
3. **Three-tier anchor**: Offer 3 tiers where the middle tier is the target. The top tier makes the middle look reasonable.

### Step 4: Design the Pricing Page
The pricing page is a conversion page, not an information page:
- **Headline**: State the outcome, not the price ("Grow your revenue" not "Our plans")
- **Recommended tier**: Visually highlight the tier you want most customers to choose
- **Feature comparison**: Show what each tier includes. Lead with the features that matter most.
- **Social proof**: Add testimonials or customer counts near the pricing table
- **FAQ**: Address objections (cancellation, refunds, what happens if I outgrow my plan)
- **CTA**: Clear action button on each tier. Use action language ("Start growing" not "Sign up")

### Step 5: Build the Pricing Page
Implement as a Next.js page:
```typescript
// app/pricing/page.tsx
// Server Component — no client-side JS needed for the pricing table
// Use Tailwind for the tier cards with visual emphasis on recommended tier
// If Stripe integration is active, link CTAs to Stripe Checkout
```

### Step 6: Test and Iterate
- A/B test pricing page layouts (not prices — changing prices frequently erodes trust)
- Monitor conversion rate per tier in Vercel Analytics
- Track which tier customers choose and whether they upgrade later
- Review pricing quarterly against competitive landscape

## Stack Context
- **Next.js**: Pricing page is a Server Component at `app/pricing/page.tsx`. No client-side JS needed for display. If Stripe integration is active, CTA buttons link to Stripe Checkout sessions created via Server Actions.
- **Tailwind CSS**: Use Tailwind's grid for tier cards. Highlight recommended tier with a distinct border, background, or "Most Popular" badge.
- **Stripe**: When payments are active, connect pricing tiers directly to Stripe Products and Prices. Use Stripe's hosted checkout or embedded checkout.
- **Vercel Analytics**: Track pricing page views, time-on-page, and conversion to signup/purchase.
- **Notion**: Pricing rationale, competitor price research, and A/B test results documented in Notion.

## Quality Gate
- [ ] Price is justified by value delivered (not cost-plus or gut feeling)
- [ ] Pricing model matches how customer receives value
- [ ] At least 2 competitive alternatives researched for price anchoring
- [ ] Pricing page has a clear recommended tier
- [ ] Pricing page addresses top 3 objections
- [ ] Documented in Notion with rationale for each price point

## Anti-Patterns
- **Cost-plus pricing** — pricing based on your costs ignores customer value. A feature that costs you $1/month to run might save the customer $1,000/month.
- **Too many tiers** — 3 tiers is ideal. 5+ tiers create decision paralysis.
- **Hidden pricing** — "Contact us for pricing" loses most small-business buyers. Be transparent.
- **Frequent price changes** — changing prices monthly erodes trust. Set prices, test the page, review quarterly.
- **Race to the bottom** — competing on price is a losing strategy for small businesses. Compete on value and specificity.

## Related Skills
- `strategy/positioning` — pricing must align with market position
- `strategy/competitor-alternatives` — competitive price research
- `engineering/stripe-integration` — implementing payment flows
- `communications/paywall-cro` — optimizing the upgrade/paywall experience
- `communications/page-cro` — optimizing the pricing page for conversion
