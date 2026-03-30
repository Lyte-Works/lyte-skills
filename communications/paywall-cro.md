<!-- reconstructed -->
---
name: "paywall-cro"
description: "Paywall and upgrade flow optimization — pricing page conversion, upgrade triggers, and plan selection"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Paywall CRO

## When to Use
- Free-to-paid conversion is low
- Pricing page has traffic but few upgrades
- Optimizing the upgrade trigger and timing
- Testing pricing page layouts

## Workflow

### Step 1: Map the Upgrade Journey
```
Free usage → Hit limit/see locked feature → Visit pricing → Compare plans → Checkout → Paid
```
Measure conversion at each step.

### Step 2: Upgrade Trigger Optimization
When users hit a paywall, the experience matters:
- **Soft wall**: Show the value of upgrading without blocking usage
- **Hard wall**: Block access with a clear upgrade path
- **Metered wall**: Allow N free uses, then require upgrade

Best practice: show what they are missing, not just that they cannot access it.

### Step 3: Pricing Page Optimization
Apply page-cro principles plus pricing-specific patterns:
- **Recommended tier highlighted** (visual emphasis with Tailwind)
- **Annual/monthly toggle** (show savings for annual)
- **Feature comparison table** (clear what each tier includes)
- **Money-back guarantee** (reduces risk)
- **FAQ addressing objections** (cancellation, hidden fees, what happens if I downgrade)

### Step 4: Reduce Checkout Friction
- Pre-fill what you know (email, name)
- Use Stripe hosted checkout (trusted, secure appearance)
- Show what they get immediately after payment
- Send confirmation email via Resend

### Step 5: Post-Upgrade Experience
- Immediate access to paid features (no waiting)
- Welcome email for paid customers
- Quick win: guide them to the most valuable paid feature

### Step 6: Measure
| Metric | Definition |
|--------|-----------|
| Pricing page view rate | % of users who visit pricing |
| Pricing → checkout rate | % who start checkout |
| Checkout completion rate | % who complete payment |
| Overall free → paid rate | End-to-end conversion |

## Stack Context
- **Next.js**: Pricing page as Server Component. Upgrade modals as Client Components.
- **Stripe**: Checkout sessions and customer portal.
- **Supabase**: Track plan status and feature access.
- **Resend**: Upgrade confirmation and welcome emails.
- **Vercel Analytics**: Funnel tracking for upgrade journey.
- **Tailwind**: Tier cards with visual hierarchy.

## Quality Gate
- [ ] Upgrade triggers show value (not just "upgrade to access")
- [ ] Recommended tier visually highlighted
- [ ] Pricing page addresses top objections
- [ ] Checkout friction minimized
- [ ] Post-upgrade experience immediate
- [ ] Full funnel tracked

## Anti-Patterns
- **Surprise paywall** — users should know what is free and what is paid before signing up.
- **Hard block without value preview** — show what they get, not just a lock icon.
- **No recommended tier** — without guidance, users pick the cheapest or leave.
- **Complex checkout** — use Stripe hosted checkout. Do not build a custom checkout form.

## Related Skills
- `strategy/pricing-strategy` — pricing model and tier design
- `communications/page-cro` — general page optimization
- `engineering/stripe-integration` — payment implementation
- `communications/ab-test-setup` — testing pricing page variations
