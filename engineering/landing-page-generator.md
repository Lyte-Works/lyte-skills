<!-- reconstructed -->
---
name: "landing-page-generator"
description: "Rapidly generate conversion-optimized landing pages with Next.js App Router and Tailwind CSS"
workers: ["frontend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Landing Page Generator

## When to Use
- Client needs a landing page quickly (launch, campaign, event)
- Building a pre-launch or waitlist page
- Creating product or feature-specific landing pages
- A/B testing different page layouts

## Workflow

### Step 1: Define the Page Goal
Every landing page has ONE goal:
- Collect emails (waitlist, newsletter)
- Drive signups (free trial, account creation)
- Generate leads (contact form, demo request)
- Sell (purchase, subscribe)

One page, one goal, one CTA.

### Step 2: Choose the Layout Pattern
| Pattern | Best For |
|---------|---------|
| Hero + Benefits + CTA | Product launches |
| Hero + Social Proof + CTA | Trust-dependent products |
| Hero + Features + Pricing + CTA | SaaS products |
| Hero + Problem/Solution + CTA | Problem-aware audiences |
| Minimal Hero + CTA | Waitlist / coming soon |

### Step 3: Section Template
Every landing page uses these sections (in order):

1. **Hero**: Headline (outcome-focused), subheadline (how), CTA button
2. **Social Proof** (optional): Logos, testimonials, or metrics
3. **Problem**: Articulate the pain point
4. **Solution**: How the product solves it
5. **Features/Benefits**: 3-4 key benefits with icons
6. **Testimonials**: 2-3 customer quotes
7. **CTA**: Repeat the primary call to action
8. **FAQ** (optional): Address top objections

### Step 4: Generate the Page
```typescript
// app/[campaign]/page.tsx
import type { Metadata } from 'next';
import { Hero } from '@/components/landing/hero';
import { Benefits } from '@/components/landing/benefits';
import { Testimonials } from '@/components/landing/testimonials';
import { CTA } from '@/components/landing/cta';
import { FAQ } from '@/components/landing/faq';

export const metadata: Metadata = {
  title: 'Headline That States the Outcome',
  description: 'Supporting description for search and social sharing',
};

export default function LandingPage() {
  return (
    <main>
      <Hero
        headline="Headline that states the outcome the customer wants"
        subheadline="One sentence explaining how you deliver that outcome"
        ctaText="Get Started Free"
        ctaHref="/signup"
      />
      <Benefits items={[
        { title: 'Benefit 1', description: 'Why this matters', icon: '...' },
        { title: 'Benefit 2', description: 'Why this matters', icon: '...' },
        { title: 'Benefit 3', description: 'Why this matters', icon: '...' },
      ]} />
      <Testimonials items={[
        { quote: '...', name: '...', role: '...', company: '...' },
      ]} />
      <CTA
        headline="Ready to get started?"
        ctaText="Start Free Trial"
        ctaHref="/signup"
      />
      <FAQ items={[
        { question: '...', answer: '...' },
      ]} />
    </main>
  );
}
```

### Step 5: Optimize for Conversion
- Above-the-fold CTA (visible without scrolling)
- Single, consistent CTA throughout the page (same text, same destination)
- Remove navigation (no distractions from the goal)
- Mobile-first design (majority of landing page traffic is mobile)
- Fast load time (Server Component = zero client JS by default)

### Step 6: Add Tracking
```typescript
// Track CTA clicks with Vercel Analytics
import { track } from '@vercel/analytics';

<button onClick={() => track('cta_clicked', { page: 'launch' })}>
  Get Started
</button>
```

## Stack Context
- **Next.js App Router**: Landing pages are Server Components (fast, no JS bundle). Use `app/[campaign]/page.tsx` for campaign-specific pages.
- **Tailwind CSS**: Responsive, mobile-first layouts. Use consistent spacing and typography scales.
- **Vercel**: Auto-deploy on merge. Preview URLs for stakeholder review. Custom domains for campaign-specific URLs.
- **Resend**: Email capture forms submit to a Server Action that stores the email (Supabase) and sends a confirmation (Resend).
- **Vercel Analytics**: Track page views, CTA clicks, and conversion events.

## Quality Gate
- [ ] Page has ONE clear goal and ONE CTA
- [ ] Hero headline states an outcome, not a feature
- [ ] Page is responsive (tested on mobile)
- [ ] Metadata set (title, description, OG image)
- [ ] CTA is above the fold
- [ ] Page loads fast (Server Component, optimized images)
- [ ] Tracking implemented for conversion events

## Anti-Patterns
- **Multiple CTAs** — "Sign up," "Learn more," "Watch demo," "Contact us" on one page splits attention. One goal.
- **Feature-led headlines** — "AI-powered analytics platform" tells the visitor nothing. Lead with the outcome.
- **No social proof** — a page without any form of trust signal converts poorly.
- **Heavy client JS** — landing pages should be Server Components. No reason for client-side rendering.
- **No tracking** — if you cannot measure conversion, you cannot improve it.

## Related Skills
- `engineering/frontend` — detailed frontend patterns
- `communications/page-cro` — optimizing landing page conversion
- `communications/copywriting` — writing landing page copy
- `strategy/launch-strategy` — landing pages as part of launch plans
- `communications/ab-test-setup` — testing page variations
