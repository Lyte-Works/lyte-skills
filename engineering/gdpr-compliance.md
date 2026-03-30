<!-- reconstructed -->
---
name: "gdpr-compliance"
description: "GDPR compliance for web applications — data mapping, consent management, privacy policies, and data subject rights"
workers: ["security-analyst", "legal-advisor"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# GDPR Compliance

## When to Use
- Application collects personal data from EU/EEA users
- Setting up cookie consent and privacy controls
- Writing privacy policies and terms of service
- Implementing data subject rights (access, deletion, portability)
- Client asks about GDPR or data privacy compliance

## Workflow

### Step 1: Data Mapping
Document all personal data the application collects:

| Data Type | Source | Storage | Purpose | Retention | Legal Basis |
|-----------|--------|---------|---------|-----------|-------------|
| Email | Signup form | Supabase | Account creation | Until deletion | Consent |
| Name | Profile | Supabase | Personalization | Until deletion | Consent |
| IP Address | Server logs | Vercel | Security | 30 days | Legitimate interest |
| Page views | Analytics | Vercel Analytics | Product improvement | Aggregated | Legitimate interest |

### Step 2: Consent Management
For Vercel Analytics (cookie-free): no consent banner needed.
For other tracking (GA4, third-party scripts): implement consent:

```typescript
// components/cookie-consent.tsx
"use client";
import { useState, useEffect } from 'react';

export function CookieConsent() {
  const [consent, setConsent] = useState<boolean | null>(null);

  useEffect(() => {
    const stored = localStorage.getItem('cookie-consent');
    if (stored !== null) setConsent(stored === 'true');
  }, []);

  if (consent !== null) return null; // Already decided

  return (
    <div className="fixed bottom-0 inset-x-0 bg-white border-t p-4 shadow-lg z-50">
      <div className="max-w-4xl mx-auto flex items-center justify-between gap-4">
        <p className="text-sm">We use cookies for analytics. <a href="/privacy" className="underline">Privacy Policy</a></p>
        <div className="flex gap-2">
          <button onClick={() => { setConsent(false); localStorage.setItem('cookie-consent', 'false'); }}
            className="px-4 py-2 text-sm border rounded">Decline</button>
          <button onClick={() => { setConsent(true); localStorage.setItem('cookie-consent', 'true'); }}
            className="px-4 py-2 text-sm bg-blue-600 text-white rounded">Accept</button>
        </div>
      </div>
    </div>
  );
}
```

### Step 3: Privacy Policy
Every application needs a privacy policy page (`app/privacy/page.tsx`) covering:
1. What data we collect
2. Why we collect it (legal basis)
3. How we use it
4. Who we share it with (third-party services: Vercel, Supabase, Resend, Stripe)
5. How long we keep it
6. User rights (access, correction, deletion, portability)
7. How to contact us

### Step 4: Data Subject Rights
Implement mechanisms for:
- **Right of access**: User can request all their data
- **Right to rectification**: User can correct their data
- **Right to erasure**: User can request deletion
- **Right to data portability**: User can export their data

```typescript
// app/api/data-export/route.ts
import { NextResponse } from 'next/server';
import { getServerSession } from 'next-auth';
import { supabase } from '@/lib/db';

export async function GET() {
  const session = await getServerSession();
  if (!session) return NextResponse.json({ error: 'Unauthorized' }, { status: 401 });

  const { data: userData } = await supabase
    .from('users')
    .select('*')
    .eq('id', session.user.id)
    .single();

  return NextResponse.json(userData, {
    headers: {
      'Content-Disposition': 'attachment; filename="my-data.json"',
    },
  });
}
```

### Step 5: Data Minimization
Review all data collection points:
- Do we need this field? If not, remove it.
- Can we anonymize or aggregate instead of storing raw data?
- Is the retention period justified?

### Step 6: Third-Party Data Processing
Document all third-party services that process user data:
- **Vercel**: Hosting, logs (Data Processing Agreement available)
- **Supabase**: Database (DPA available, EU hosting option)
- **Resend**: Email sending (DPA available)
- **Stripe**: Payments (PCI DSS compliant, DPA available)

## Stack Context
- **Vercel Analytics**: Cookie-free, privacy-friendly. No consent banner needed for Vercel Analytics alone.
- **Supabase**: Offers EU-region hosting for data residency requirements. RLS policies enforce data access controls.
- **Next.js**: Privacy policy and data export endpoints as Server Components and API routes.
- **Resend**: Data processing agreement available. Email content processed per Resend's privacy policy.

## Quality Gate
- [ ] Data map completed for all personal data
- [ ] Legal basis identified for each data type
- [ ] Consent mechanism implemented (if needed beyond Vercel Analytics)
- [ ] Privacy policy published and accessible from every page
- [ ] Data export and deletion endpoints implemented
- [ ] Third-party DPAs documented
- [ ] Retention periods defined and enforced

## Anti-Patterns
- **Consent for everything** — not all processing requires consent. Legitimate interest is a valid legal basis.
- **Dark patterns** — making it harder to decline cookies than to accept them violates GDPR.
- **Privacy policy copy-paste** — generic privacy policies that do not match actual data practices are non-compliant.
- **Collecting "just in case"** — data minimization means only collecting what you need for a defined purpose.
- **No deletion mechanism** — if you cannot delete a user's data, you are non-compliant.

## Related Skills
- `engineering/security-engineer` — security measures that support compliance
- `engineering/security-audit` — auditing for compliance gaps
- `engineering/soc2-compliance` — complementary compliance framework
- `engineering/database-designer` — schema design with privacy in mind
