<!-- reconstructed -->
---
name: "analytics-tracking"
description: "Analytics implementation — Vercel Analytics setup, custom event tracking, conversion tracking, and reporting"
workers: ["marketing-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Analytics Tracking

## When to Use
- Setting up analytics for a new site
- Implementing conversion tracking
- Custom event tracking for specific user actions
- Building a reporting dashboard
- Migrating from GA4 to Vercel Analytics

## Workflow

### Step 1: Vercel Analytics Setup
```typescript
// app/layout.tsx
import { Analytics } from '@vercel/analytics/react';
import { SpeedInsights } from '@vercel/speed-insights/next';

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html>
      <body>
        {children}
        <Analytics />
        <SpeedInsights />
      </body>
    </html>
  );
}
```

### Step 2: Custom Event Tracking
```typescript
// Track specific user actions
import { track } from '@vercel/analytics';

// CTA clicks
track('cta_clicked', { location: 'hero', page: 'homepage' });

// Form submissions
track('form_submitted', { form: 'contact', source: 'pricing_page' });

// Signup completion
track('signup_completed', { plan: 'free', source: 'organic' });

// Feature usage
track('feature_used', { feature: 'export', plan: 'pro' });
```

### Step 3: Define Key Events
| Event | Trigger | Properties |
|-------|---------|-----------|
| `page_view` | Automatic (Vercel Analytics) | URL, referrer |
| `cta_clicked` | User clicks a CTA button | location, page |
| `form_submitted` | Form successfully submitted | form_name, source |
| `signup_completed` | User completes registration | plan, source |
| `checkout_started` | User initiates checkout | plan, price |
| `purchase_completed` | Payment successful | plan, price, method |

### Step 4: GA4 (Optional)
Only add GA4 if the client specifically requires it:
```typescript
// components/analytics/google-analytics.tsx
"use client";

import Script from 'next/script';

export function GoogleAnalytics({ measurementId }: { measurementId: string }) {
  return (
    <>
      <Script src={`https://www.googletagmanager.com/gtag/js?id=${measurementId}`} strategy="afterInteractive" />
      <Script id="ga4" strategy="afterInteractive">
        {`
          window.dataLayer = window.dataLayer || [];
          function gtag(){dataLayer.push(arguments);}
          gtag('js', new Date());
          gtag('config', '${measurementId}');
        `}
      </Script>
    </>
  );
}
```

**Note**: GA4 requires a cookie consent banner. Vercel Analytics does not.

### Step 5: Conversion Funnel Tracking
Map the conversion funnel:
```
Visit → CTA Click → Signup Start → Signup Complete → First Action → Upgrade
```
Track each step with custom events to identify drop-off points.

### Step 6: Reporting
Create a monthly report in Notion:
- Total visitors (Vercel Analytics)
- Top pages by traffic
- Conversion events by type
- Funnel conversion rates
- Traffic sources
- Trends vs. previous month

## Stack Context
- **Vercel Analytics**: Primary analytics. Cookie-free, no consent banner needed. Built into Vercel dashboard.
- **Vercel Speed Insights**: Core Web Vitals monitoring.
- **Next.js**: `@vercel/analytics` package for event tracking.
- **GA4**: Optional, only when client requires it. Needs consent banner.
- **Notion**: Monthly analytics reports.

## Quality Gate
- [ ] Vercel Analytics installed and verified
- [ ] Custom events defined for all key user actions
- [ ] Conversion funnel mapped and tracked
- [ ] Monthly reporting cadence established
- [ ] GA4 only added if client requires it (not by default)

## Anti-Patterns
- **GA4 by default** — Vercel Analytics is the default. GA4 adds complexity and requires consent.
- **Tracking everything** — track decisions, not clicks. Focus on events that inform business decisions.
- **No conversion tracking** — page views without conversion events are vanity metrics.
- **No reporting cadence** — analytics without regular review is theater.
- **Missing consent banner** — if GA4 is added, a consent banner is legally required in many jurisdictions.

## Related Skills
- `strategy/product-analytics` — product-level analytics
- `communications/seo-audit` — measuring SEO performance
- `communications/ab-test-setup` — testing hypotheses from analytics
- `communications/page-cro` — conversion optimization informed by analytics
