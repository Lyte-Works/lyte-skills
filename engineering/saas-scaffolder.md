<!-- reconstructed -->
---
name: "saas-scaffolder"
description: "Bootstrap a SaaS application — project structure, auth, billing, dashboard, and common SaaS patterns"
workers: ["systems-architect", "frontend-developer", "backend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# SaaS Scaffolder

## When to Use
- Starting a new SaaS product from scratch
- Client needs a boilerplate with auth, billing, and dashboard
- Standardizing the starting point for SaaS projects

## Workflow

### Step 1: Project Structure
```
my-saas/
├── app/
│   ├── (marketing)/          # Public pages
│   │   ├── page.tsx          # Homepage
│   │   ├── pricing/page.tsx
│   │   ├── blog/page.tsx
│   │   └── layout.tsx        # Marketing layout (nav + footer)
│   ├── (auth)/               # Auth pages
│   │   ├── login/page.tsx
│   │   ├── signup/page.tsx
│   │   └── layout.tsx        # Auth layout (centered, minimal)
│   ├── (dashboard)/          # Protected pages
│   │   ├── dashboard/page.tsx
│   │   ├── settings/page.tsx
│   │   ├── billing/page.tsx
│   │   └── layout.tsx        # Dashboard layout (sidebar + header)
│   ├── api/
│   │   ├── auth/[...nextauth]/route.ts
│   │   └── webhook/stripe/route.ts
│   ├── actions/
│   │   ├── auth.ts
│   │   ├── billing.ts
│   │   └── settings.ts
│   ├── layout.tsx            # Root layout
│   └── not-found.tsx
├── components/
│   ├── ui/                   # Shared UI components
│   ├── marketing/            # Marketing page components
│   └── dashboard/            # Dashboard components
├── lib/
│   ├── db.ts                 # Supabase client
│   ├── auth.ts               # NextAuth config
│   ├── stripe.ts             # Stripe client
│   ├── email.ts              # Resend client
│   └── utils.ts              # Utility functions
├── types/
│   └── supabase.ts           # Generated types
├── tailwind.config.ts
├── next.config.ts
└── package.json
```

### Step 2: Route Groups
Use Next.js route groups for different layouts:
- `(marketing)` — public pages with marketing nav/footer
- `(auth)` — login/signup with minimal centered layout
- `(dashboard)` — protected pages with sidebar navigation

### Step 3: Core Features Checklist
| Feature | Implementation |
|---------|---------------|
| Authentication | NextAuth.js with Supabase adapter |
| Authorization | Middleware + server-side session checks |
| Billing | Stripe Checkout + Customer Portal |
| User settings | Server Actions + Supabase |
| Team/org support | Supabase tables with RLS |
| Email | Resend for transactional email |
| Analytics | Vercel Analytics |
| SEO | Next.js Metadata API |

### Step 4: Database Schema
```sql
-- Core SaaS tables
CREATE TABLE organizations (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  name TEXT NOT NULL,
  stripe_customer_id TEXT,
  subscription_status TEXT DEFAULT 'trialing',
  plan TEXT DEFAULT 'free',
  created_at TIMESTAMPTZ DEFAULT now()
);

CREATE TABLE members (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  user_id UUID REFERENCES auth.users(id),
  organization_id UUID REFERENCES organizations(id),
  role TEXT DEFAULT 'member' CHECK (role IN ('owner', 'admin', 'member')),
  created_at TIMESTAMPTZ DEFAULT now(),
  UNIQUE(user_id, organization_id)
);

-- RLS policies
ALTER TABLE organizations ENABLE ROW LEVEL SECURITY;
ALTER TABLE members ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Members can view their org"
  ON organizations FOR SELECT
  USING (id IN (SELECT organization_id FROM members WHERE user_id = auth.uid()));
```

### Step 5: Essential Middleware
```typescript
// middleware.ts
import { withAuth } from 'next-auth/middleware';

export default withAuth({
  pages: { signIn: '/login' },
});

export const config = {
  matcher: ['/dashboard/:path*', '/settings/:path*', '/billing/:path*'],
};
```

### Step 6: Deploy and Verify
1. Push to GitHub
2. Link to Vercel
3. Set environment variables
4. Verify all flows: signup → dashboard → billing → settings

## Stack Context
- **Next.js App Router**: Route groups for layout separation. Server Components for pages, Server Actions for mutations.
- **Supabase**: Database, auth provider, and storage.
- **Stripe**: Subscription billing with checkout and customer portal.
- **NextAuth.js**: Session management with Supabase adapter.
- **Resend**: Welcome emails, password reset, notifications.
- **Tailwind CSS**: Consistent design system across marketing and dashboard.
- **Vercel**: Zero-config deployment with preview environments.

## Quality Gate
- [ ] All core features working (auth, billing, settings)
- [ ] RLS policies on all user-data tables
- [ ] Middleware protecting dashboard routes
- [ ] Environment variables documented
- [ ] Responsive design on all pages
- [ ] Stripe test mode verified before going live

## Anti-Patterns
- **Building everything before validating** — scaffold the minimum, then validate with users.
- **No route groups** — mixing marketing and dashboard layouts creates complexity.
- **Skipping RLS** — "we'll add security later" leads to security never.
- **Custom auth** — use NextAuth. Do not build auth from scratch.
- **No billing from day one** — if the SaaS will charge money, integrate Stripe early.

## Related Skills
- `engineering/senior-architect` — architectural decisions
- `engineering/stripe-integration` — detailed payment setup
- `engineering/database-designer` — schema design
- `engineering/security-engineer` — securing the application
- `engineering/frontend` — UI implementation
