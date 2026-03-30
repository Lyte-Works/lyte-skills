<!-- reconstructed -->
---
name: "backend"
description: "Backend development with Next.js — API routes, Server Actions, database integration, authentication, and server-side logic"
workers: ["backend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Backend Developer

## When to Use
- Building API routes for external integrations or webhooks
- Implementing Server Actions for form submissions and data mutations
- Designing database schema and queries
- Setting up authentication and authorization
- Server-side business logic that does not belong in the frontend

## Workflow

### Step 1: Choose the Right Pattern
| Need | Pattern | Location |
|------|---------|----------|
| Read data for a page | Server Component async function | `app/page.tsx` |
| Form submission / mutation | Server Action | `app/actions/*.ts` |
| External webhook | API Route (POST) | `app/api/*/route.ts` |
| Third-party API proxy | API Route (GET/POST) | `app/api/*/route.ts` |
| Scheduled job | Vercel Cron | `vercel.json` + API route |
| Real-time updates | Supabase Realtime | Client-side subscription |

### Step 2: API Route Structure
```typescript
// app/api/[resource]/route.ts
import { NextRequest, NextResponse } from 'next/server';

export async function GET(request: NextRequest) {
  try {
    const { searchParams } = new URL(request.url);
    const id = searchParams.get('id');

    // Business logic here
    const data = await fetchData(id);

    return NextResponse.json(data);
  } catch (error) {
    console.error('API error:', error);
    return NextResponse.json(
      { error: 'Internal server error' },
      { status: 500 }
    );
  }
}

export async function POST(request: NextRequest) {
  try {
    const body = await request.json();

    // Validate input
    if (!body.email) {
      return NextResponse.json(
        { error: 'Email is required' },
        { status: 400 }
      );
    }

    // Business logic here
    const result = await processData(body);

    return NextResponse.json(result, { status: 201 });
  } catch (error) {
    console.error('API error:', error);
    return NextResponse.json(
      { error: 'Internal server error' },
      { status: 500 }
    );
  }
}
```

### Step 3: Server Actions
```typescript
// app/actions/subscribe.ts
"use server";

import { z } from 'zod';
import { supabase } from '@/lib/db';
import { resend } from '@/lib/email';

const subscribeSchema = z.object({
  email: z.string().email(),
  name: z.string().min(1).max(100),
});

export async function subscribe(formData: FormData) {
  const parsed = subscribeSchema.safeParse({
    email: formData.get('email'),
    name: formData.get('name'),
  });

  if (!parsed.success) {
    return { error: parsed.error.flatten().fieldErrors };
  }

  const { email, name } = parsed.data;

  // Store in database
  const { error: dbError } = await supabase
    .from('subscribers')
    .insert({ email, name });

  if (dbError) {
    if (dbError.code === '23505') {
      return { error: 'Already subscribed' };
    }
    return { error: 'Failed to subscribe' };
  }

  // Send welcome email
  await resend.emails.send({
    from: 'welcome@yourdomain.com',
    to: email,
    subject: `Welcome, ${name}!`,
    html: `<p>Thanks for subscribing!</p>`,
  });

  return { success: true };
}
```

### Step 4: Database Integration
```typescript
// lib/db.ts
import { createClient } from '@supabase/supabase-js';
import type { Database } from '@/types/supabase';

// Server-side client (full access)
export const supabase = createClient<Database>(
  process.env.NEXT_PUBLIC_SUPABASE_URL!,
  process.env.SUPABASE_SERVICE_ROLE_KEY!
);

// Client-side client (RLS-restricted)
export const supabaseClient = createClient<Database>(
  process.env.NEXT_PUBLIC_SUPABASE_URL!,
  process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!
);
```

### Step 5: Authentication (when needed)
```typescript
// Using NextAuth.js with Supabase adapter
// app/api/auth/[...nextauth]/route.ts
import NextAuth from 'next-auth';
import { SupabaseAdapter } from '@auth/supabase-adapter';

const handler = NextAuth({
  providers: [/* configure providers */],
  adapter: SupabaseAdapter({
    url: process.env.NEXT_PUBLIC_SUPABASE_URL!,
    secret: process.env.SUPABASE_SERVICE_ROLE_KEY!,
  }),
});

export { handler as GET, handler as POST };
```

### Step 6: Error Handling and Logging
- All async operations wrapped in try/catch
- Return appropriate HTTP status codes
- Log errors server-side with context
- Return user-friendly error messages to the client
- Never expose internal error details or stack traces

## Stack Context
- **Next.js App Router**: Server Actions for mutations, API routes for webhooks/external integrations.
- **Supabase**: Primary database. Use service role key for server-side, anon key + RLS for client-side.
- **Resend**: Email via Server Actions or API routes. Never expose the API key client-side.
- **Stripe**: Webhook handling in API routes with signature verification.
- **Vercel**: Serverless functions for API routes. 10s default timeout (configurable). Cron jobs via `vercel.json`.
- **Zod**: Input validation for all Server Actions and API routes.

## Quality Gate
- [ ] Input validation on all endpoints (Zod or equivalent)
- [ ] Error handling with appropriate HTTP status codes
- [ ] No secrets exposed to the client
- [ ] Database queries use parameterized inputs (no SQL injection)
- [ ] Authentication checked on protected routes
- [ ] TypeScript types for all request/response shapes
- [ ] Tested with edge cases (empty input, invalid input, concurrent requests)

## Anti-Patterns
- **No input validation** — never trust client input. Validate everything server-side.
- **Exposing secrets** — `NEXT_PUBLIC_` prefix makes variables available client-side. Keep secrets server-only.
- **No error handling** — unhandled errors crash the function. Always try/catch async operations.
- **Business logic in API routes** — extract business logic into `/lib/` functions. API routes are thin handlers.
- **Direct SQL strings** — use parameterized queries or the Supabase client. Never concatenate user input into SQL.

## Related Skills
- `engineering/fullstack` — combined frontend + backend patterns
- `engineering/database-designer` — schema design
- `engineering/stripe-integration` — payment backend
- `engineering/security-engineer` — securing backend endpoints
- `engineering/devops` — deployment and infrastructure
