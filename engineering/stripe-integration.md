<!-- reconstructed -->
---
name: "stripe-integration"
description: "Stripe payment integration — checkout sessions, webhooks, subscriptions, and customer portal"
workers: ["backend-developer", "frontend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Stripe Integration

## When to Use
- Adding payments to a Next.js application
- Setting up subscription billing
- One-time purchases or digital product sales
- Customer portal for billing management
- Handling Stripe webhooks

## Workflow

### Step 1: Stripe Setup
1. Create a Stripe account
2. Get API keys from the Stripe dashboard
3. Install the SDK: `npm install stripe @stripe/stripe-js`
4. Add environment variables:
```
STRIPE_SECRET_KEY=sk_test_xxxxx
STRIPE_PUBLISHABLE_KEY=pk_test_xxxxx
STRIPE_WEBHOOK_SECRET=whsec_xxxxx
```

### Step 2: Create Products and Prices
In the Stripe Dashboard (or via API):
- Create Products (what you sell)
- Create Prices (how much and how often)
- Note the Price IDs for use in code

### Step 3: Checkout Session (Server Action)
```typescript
// app/actions/checkout.ts
"use server";

import Stripe from 'stripe';
import { redirect } from 'next/navigation';

const stripe = new Stripe(process.env.STRIPE_SECRET_KEY!);

export async function createCheckout(priceId: string) {
  const session = await stripe.checkout.sessions.create({
    mode: 'subscription', // or 'payment' for one-time
    payment_method_types: ['card'],
    line_items: [{ price: priceId, quantity: 1 }],
    success_url: `${process.env.NEXT_PUBLIC_URL}/success?session_id={CHECKOUT_SESSION_ID}`,
    cancel_url: `${process.env.NEXT_PUBLIC_URL}/pricing`,
  });

  redirect(session.url!);
}
```

### Step 4: Webhook Handler
```typescript
// app/api/webhook/stripe/route.ts
import { NextRequest, NextResponse } from 'next/server';
import Stripe from 'stripe';
import { supabase } from '@/lib/db';

const stripe = new Stripe(process.env.STRIPE_SECRET_KEY!);

export async function POST(request: NextRequest) {
  const body = await request.text();
  const signature = request.headers.get('stripe-signature')!;

  let event: Stripe.Event;
  try {
    event = stripe.webhooks.constructEvent(
      body,
      signature,
      process.env.STRIPE_WEBHOOK_SECRET!
    );
  } catch (err) {
    return NextResponse.json({ error: 'Invalid signature' }, { status: 400 });
  }

  switch (event.type) {
    case 'checkout.session.completed': {
      const session = event.data.object as Stripe.Checkout.Session;
      // Update user subscription status in database
      await supabase
        .from('users')
        .update({ subscription_status: 'active', stripe_customer_id: session.customer })
        .eq('email', session.customer_email);
      break;
    }
    case 'customer.subscription.deleted': {
      const subscription = event.data.object as Stripe.Subscription;
      await supabase
        .from('users')
        .update({ subscription_status: 'canceled' })
        .eq('stripe_customer_id', subscription.customer);
      break;
    }
  }

  return NextResponse.json({ received: true });
}
```

### Step 5: Customer Portal
```typescript
// app/actions/portal.ts
"use server";

import Stripe from 'stripe';
import { redirect } from 'next/navigation';

const stripe = new Stripe(process.env.STRIPE_SECRET_KEY!);

export async function createPortalSession(customerId: string) {
  const session = await stripe.billingPortal.sessions.create({
    customer: customerId,
    return_url: `${process.env.NEXT_PUBLIC_URL}/account`,
  });

  redirect(session.url);
}
```

### Step 6: Pricing Page Integration
```typescript
// app/pricing/page.tsx
import { createCheckout } from '@/app/actions/checkout';

const plans = [
  { name: 'Starter', price: '$29/mo', priceId: 'price_xxxxx' },
  { name: 'Pro', price: '$79/mo', priceId: 'price_yyyyy', recommended: true },
  { name: 'Enterprise', price: '$199/mo', priceId: 'price_zzzzz' },
];

export default function PricingPage() {
  return (
    <div className="grid md:grid-cols-3 gap-8 max-w-5xl mx-auto py-12 px-4">
      {plans.map(plan => (
        <div key={plan.name} className={`border rounded-lg p-6 ${plan.recommended ? 'border-blue-500 ring-2 ring-blue-200' : ''}`}>
          <h3 className="text-xl font-bold">{plan.name}</h3>
          <p className="text-3xl font-bold mt-2">{plan.price}</p>
          <form action={createCheckout.bind(null, plan.priceId)}>
            <button type="submit" className="w-full mt-6 bg-blue-600 text-white py-2 rounded hover:bg-blue-700">
              Get Started
            </button>
          </form>
        </div>
      ))}
    </div>
  );
}
```

## Stack Context
- **Next.js**: Server Actions for checkout creation, API routes for webhooks. Pricing page as Server Component.
- **Stripe**: Stripe Checkout (hosted) for payment collection. Customer Portal for billing management. Webhooks for event processing.
- **Supabase**: Store subscription status, customer IDs, and plan information. Use RLS to ensure users can only access their own billing data.
- **Vercel**: Set Stripe environment variables in Vercel dashboard. Use Stripe CLI for local webhook testing.
- **Tailwind**: Pricing tier cards with visual emphasis on recommended plan.

## Quality Gate
- [ ] Webhook signature verification implemented (never trust unverified webhooks)
- [ ] All Stripe API calls have error handling
- [ ] Environment variables set in Vercel (not hardcoded)
- [ ] Customer portal available for self-service billing
- [ ] Subscription status synced to database via webhooks
- [ ] Tested with Stripe test mode before going live

## Anti-Patterns
- **No webhook verification** — processing unverified webhooks is a security vulnerability.
- **Client-side price IDs** — never let the client modify the price ID. Use server-side binding.
- **No error handling on checkout** — Stripe API calls can fail. Handle errors gracefully.
- **Hardcoded prices** — use Stripe Products/Prices. Hardcoded amounts in code will drift.
- **Ignoring subscription lifecycle** — handle all webhook events: created, updated, deleted, payment_failed.

## Related Skills
- `strategy/pricing-strategy` — pricing model and tier design
- `engineering/backend` — server-side patterns
- `engineering/security-engineer` — securing payment flows
- `communications/paywall-cro` — optimizing upgrade flows
