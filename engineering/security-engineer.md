<!-- reconstructed -->
---
name: "security-engineer"
description: "Application security — authentication, authorization, input validation, OWASP protections, and security headers"
workers: ["security-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Security Engineer

## When to Use
- Setting up authentication and authorization
- Securing API routes and Server Actions
- Implementing security headers
- Reviewing code for security vulnerabilities
- Hardening a Next.js application before launch

## Workflow

### Step 1: Security Headers
```typescript
// next.config.ts
const securityHeaders = [
  { key: 'X-DNS-Prefetch-Control', value: 'on' },
  { key: 'Strict-Transport-Security', value: 'max-age=63072000; includeSubDomains; preload' },
  { key: 'X-Frame-Options', value: 'SAMEORIGIN' },
  { key: 'X-Content-Type-Options', value: 'nosniff' },
  { key: 'Referrer-Policy', value: 'origin-when-cross-origin' },
  { key: 'Permissions-Policy', value: 'camera=(), microphone=(), geolocation=()' },
];

export default {
  async headers() {
    return [{ source: '/(.*)', headers: securityHeaders }];
  },
};
```

### Step 2: Content Security Policy
```typescript
// middleware.ts
import { NextResponse } from 'next/server';
import type { NextRequest } from 'next/server';

export function middleware(request: NextRequest) {
  const nonce = Buffer.from(crypto.randomUUID()).toString('base64');
  const csp = [
    `default-src 'self'`,
    `script-src 'self' 'nonce-${nonce}' 'strict-dynamic'`,
    `style-src 'self' 'unsafe-inline'`, // Tailwind requires unsafe-inline
    `img-src 'self' blob: data:`,
    `font-src 'self'`,
    `connect-src 'self' ${process.env.NEXT_PUBLIC_SUPABASE_URL || ''}`,
    `frame-ancestors 'none'`,
  ].join('; ');

  const response = NextResponse.next();
  response.headers.set('Content-Security-Policy', csp);
  return response;
}
```

### Step 3: Input Validation
Every endpoint that accepts user input MUST validate:
```typescript
import { z } from 'zod';

const contactSchema = z.object({
  email: z.string().email().max(255),
  name: z.string().min(1).max(100),
  message: z.string().min(1).max(5000),
});

// In Server Action or API route:
const parsed = contactSchema.safeParse(input);
if (!parsed.success) {
  return { error: 'Invalid input', details: parsed.error.flatten() };
}
```

### Step 4: Authentication
```typescript
// Using NextAuth.js
// Protect routes via middleware
export { default } from 'next-auth/middleware';

export const config = {
  matcher: ['/dashboard/:path*', '/api/protected/:path*'],
};
```

### Step 5: Authorization
```typescript
// Check user permissions in Server Actions
import { getServerSession } from 'next-auth';
import { authOptions } from '@/lib/auth';

export async function deleteProject(projectId: string) {
  const session = await getServerSession(authOptions);
  if (!session) throw new Error('Unauthorized');

  // Check ownership
  const project = await getProject(projectId);
  if (project.owner_id !== session.user.id) {
    throw new Error('Forbidden');
  }

  await supabase.from('projects').delete().eq('id', projectId);
}
```

### Step 6: Security Checklist
Run before every production deployment:
- [ ] Security headers configured
- [ ] CSP policy active
- [ ] All inputs validated (Zod)
- [ ] Authentication on protected routes
- [ ] Authorization checks in Server Actions
- [ ] No secrets in client code (check with `NEXT_PUBLIC_` search)
- [ ] RLS enabled on all Supabase tables with user data
- [ ] `npm audit` clean (no critical/high vulnerabilities)
- [ ] Environment variables not committed to git
- [ ] Rate limiting on public API endpoints

## Stack Context
- **Next.js**: Middleware for CSP and route protection. Security headers in `next.config.ts`.
- **Supabase**: RLS for database security. Never use service role key client-side.
- **NextAuth.js**: Authentication and session management.
- **Zod**: Input validation for all endpoints.
- **Vercel**: Environment variables managed in Vercel dashboard. Preview deploys use separate env vars.

## Quality Gate
- [ ] Security headers return A+ on securityheaders.com
- [ ] All forms and API endpoints have input validation
- [ ] Protected routes require authentication
- [ ] Server Actions check authorization
- [ ] No `NEXT_PUBLIC_` variables contain secrets
- [ ] RLS enabled and tested on all user data tables

## Anti-Patterns
- **Security by obscurity** — hiding endpoints or using unpredictable URLs is not security.
- **Client-side auth only** — always verify authentication server-side. Client-side checks are UX, not security.
- **Trusting client input** — validate everything server-side, even if the client also validates.
- **Overly permissive CORS** — `Access-Control-Allow-Origin: *` is rarely appropriate.
- **Secrets in code** — never hardcode API keys, database URLs, or secrets. Use environment variables.

## Related Skills
- `engineering/secops` — incident response and security operations
- `engineering/security-audit` — comprehensive security assessment
- `engineering/gdpr-compliance` — privacy and data protection
- `engineering/backend` — securing backend endpoints
