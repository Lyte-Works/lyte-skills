<!-- reconstructed -->
---
name: "referral-program"
description: "Design and optimize a customer referral program — incentives, mechanics, tracking, and growth"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Referral Program

## When to Use
- Product has happy customers who could refer others
- Want to reduce customer acquisition cost
- Building viral growth mechanics
- Launching a refer-a-friend program

## Workflow

### Step 1: Referral Program Design
| Element | Decision |
|---------|---------|
| **Incentive type** | Two-sided (both get value) > one-sided |
| **Incentive** | Credit, discount, free month, cash, feature unlock |
| **Mechanic** | Unique link, invite code, email invite |
| **Trigger** | When to prompt: after positive experience, milestone, NPS response |
| **Limit** | Cap per user? Unlimited? |

### Step 2: Two-Sided Incentive Design
| Referrer Gets | Friend Gets | Example |
|--------------|------------|---------|
| 1 free month | 1 free month | Dropbox model |
| $20 credit | 20% off first month | Marketplace model |
| Feature unlock | Extended trial | Feature-gate model |

### Step 3: Implementation
```typescript
// Generate unique referral link per user
// app/api/referral/route.ts
import { nanoid } from 'nanoid';

export async function POST(request: Request) {
  const session = await getServerSession();
  const code = nanoid(8);

  await supabase.from('referral_codes').insert({
    user_id: session.user.id,
    code,
    uses: 0,
  });

  return Response.json({
    link: `${process.env.NEXT_PUBLIC_URL}/ref/${code}`,
  });
}

// Track referral on signup
// app/ref/[code]/page.tsx
import { cookies } from 'next/headers';
import { redirect } from 'next/navigation';

export default function ReferralPage({ params }: { params: { code: string } }) {
  cookies().set('ref', params.code, { maxAge: 60 * 60 * 24 * 30 });
  redirect('/signup');
}
```

### Step 4: Prompt Strategy
When to ask for referrals (high-impact moments):
- After achieving a milestone (first project, first sale)
- After giving a high NPS score
- After a successful support interaction
- In the post-purchase confirmation page
- In email sequences (after proven value)

### Step 5: Measure
| Metric | Definition |
|--------|-----------|
| Referral rate | % of users who refer at least one person |
| Viral coefficient | Avg referrals per user x conversion rate of referred |
| Referred user quality | Retention and LTV of referred vs. non-referred |
| CAC comparison | Referral CAC vs. other channel CAC |

## Stack Context
- **Next.js**: Referral link pages, dashboard for tracking referrals.
- **Supabase**: Referral codes, tracking, and reward fulfillment.
- **Stripe**: If rewards are credits or discounts, apply via Stripe Coupons or Credits.
- **Resend**: Referral invitation emails and reward notification emails.
- **Vercel Analytics**: Track referral funnel.

## Quality Gate
- [ ] Two-sided incentive designed
- [ ] Referral mechanic implemented (unique links)
- [ ] Prompt timing aligned with positive moments
- [ ] Tracking for all referral stages (shared, clicked, signed up, activated)
- [ ] Rewards fulfilled automatically
- [ ] Viral coefficient measured

## Anti-Patterns
- **One-sided incentives** — only rewarding the referrer feels transactional. Reward both sides.
- **Asking too early** — prompting for referrals before the user has experienced value is premature.
- **No tracking** — if you cannot attribute signups to referrals, you cannot measure or improve.
- **Complex mechanics** — if explaining the referral program takes more than 2 sentences, simplify it.
- **Forgetting to fulfill** — delayed or unfulfilled rewards destroy trust. Automate fulfillment.

## Related Skills
- `communications/growth-marketer` — referral within growth strategy
- `communications/churn-prevention` — retain before you refer
- `communications/email-sequences` — referral prompt in email flows
- `engineering/stripe-integration` — reward fulfillment via Stripe
