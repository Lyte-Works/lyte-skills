<!-- reconstructed -->
---
name: "fullstack"
description: "Full-stack Next.js development — Server Components, API routes, Server Actions, database integration, and deployment"
workers: ["frontend-developer", "backend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Fullstack Developer

## When to Use
- Building features that span UI and backend logic
- Implementing forms with server-side processing
- Building data-driven pages with database queries
- Creating API integrations (payment, email, third-party services)
- Scaffolding a new full-stack application

## Workflow

### Step 1: Architecture Decision
Determine the data flow for the feature:
- **Server Component + direct query**: For read-only pages. Query the database directly in the Server Component.
- **Server Action**: For mutations (form submissions, data updates). Use `"use server"` actions.
- **API Route**: For webhooks, third-party integrations, and endpoints consumed by external services.

### Step 2: Data Layer
```typescript
// lib/db.ts — Database client (Supabase example)
import { createClient } from '@supabase/supabase-js';

export const supabase = createClient(
  process.env.NEXT_PUBLIC_SUPABASE_URL!,
  process.env.SUPABASE_SERVICE_ROLE_KEY!
);

// lib/queries/posts.ts — Query functions
export async function getPosts() {
  const { data, error } = await supabase
    .from('posts')
    .select('*')
    .order('created_at', { ascending: false });
  if (error) throw error;
  return data;
}
```

### Step 3: Server Actions
```typescript
// app/actions/contact.ts
"use server";

import { Resend } from 'resend';

const resend = new Resend(process.env.RESEND_API_KEY);

export async function submitContact(formData: FormData) {
  const email = formData.get('email') as string;
  const message = formData.get('message') as string;

  // Validate
  if (!email || !message) {
    return { error: 'Email and message are required' };
  }

  // Send email via Resend
  const { error } = await resend.emails.send({
    from: 'contact@yourdomain.com',
    to: 'hello@yourdomain.com',
    subject: `Contact from ${email}`,
    text: message,
  });

  if (error) {
    return { error: 'Failed to send message' };
  }

  return { success: true };
}
```

### Step 4: API Routes
```typescript
// app/api/webhook/stripe/route.ts
import { NextRequest, NextResponse } from 'next/server';
import Stripe from 'stripe';

const stripe = new Stripe(process.env.STRIPE_SECRET_KEY!);

export async function POST(request: NextRequest) {
  const body = await request.text();
  const signature = request.headers.get('stripe-signature')!;

  try {
    const event = stripe.webhooks.constructEvent(
      body,
      signature,
      process.env.STRIPE_WEBHOOK_SECRET!
    );

    switch (event.type) {
      case 'checkout.session.completed':
        // Handle successful payment
        break;
    }

    return NextResponse.json({ received: true });
  } catch (err) {
    return NextResponse.json({ error: 'Webhook error' }, { status: 400 });
  }
}
```

### Step 5: Connect UI to Backend
```typescript
// app/contact/page.tsx
import { submitContact } from '@/app/actions/contact';
import { ContactForm } from '@/components/features/contact-form';

export default function ContactPage() {
  return (
    <main className="max-w-2xl mx-auto px-4 py-12">
      <h1 className="text-3xl font-bold mb-6">Contact Us</h1>
      <ContactForm action={submitContact} />
    </main>
  );
}
```

### Step 6: Environment Variables
```
# .env.local (never committed)
RESEND_API_KEY=re_xxxxx
NEXT_PUBLIC_SUPABASE_URL=https://xxx.supabase.co
SUPABASE_SERVICE_ROLE_KEY=xxxxx
STRIPE_SECRET_KEY=sk_xxxxx
STRIPE_WEBHOOK_SECRET=whsec_xxxxx
```

Set these in Vercel project settings for production.

## Stack Context
- **Next.js App Router**: Server Components for reads, Server Actions for writes, API routes for webhooks.
- **Supabase**: Database for dynamic data. Use service role key server-side only. Use anon key + RLS for client-side.
- **Resend**: Email sending via Server Actions or API routes.
- **Stripe**: Payment processing via API routes (webhooks) and Server Actions (checkout session creation).
- **Vercel**: Environment variables configured in Vercel dashboard. Preview deployments for testing.

## Quality Gate
- [ ] Data fetching in Server Components (not client-side `useEffect`)
- [ ] Mutations use Server Actions (not client-side API calls where avoidable)
- [ ] API routes used only for webhooks and external integrations
- [ ] Environment variables documented (not committed)
- [ ] Error handling for all async operations
- [ ] TypeScript types for all data structures
- [ ] Tested on Vercel preview deployment

## Anti-Patterns
- **Client-side data fetching by default** — use Server Components. Only fetch client-side when real-time updates are needed.
- **Exposing secrets** — never use `NEXT_PUBLIC_` prefix for secret keys. Server-only variables stay server-side.
- **No error handling** — every database query, API call, and Server Action must handle errors.
- **Direct database calls in components** — abstract database queries into `/lib/queries/` for reusability.
- **Mixing Pages Router patterns** — no `getServerSideProps`. Use App Router patterns exclusively.

## Related Skills
- `engineering/frontend` — frontend-specific patterns
- `engineering/backend` — backend-specific patterns
- `engineering/stripe-integration` — payment integration details
- `engineering/database-designer` — schema design for Supabase
- `engineering/landing-page-generator` — quick page scaffolding
