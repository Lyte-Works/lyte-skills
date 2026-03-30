<!-- reconstructed -->
---
name: "seo-audit"
description: "Step-by-step SEO audit checklist — technical SEO, on-page, content, and off-page analysis"
workers: ["marketing-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# SEO Audit

## When to Use
- New client onboarding (baseline SEO assessment)
- Site not ranking for target keywords
- Traffic dropped unexpectedly
- Before a site redesign or migration
- Quarterly SEO health check

## Workflow

### Step 1: Technical SEO
- [ ] Site is indexed (search `site:domain.com` in Google)
- [ ] robots.txt is correct (`/robots.txt`)
- [ ] XML sitemap exists and is submitted (`/sitemap.xml`)
- [ ] HTTPS enforced (Vercel handles this)
- [ ] No duplicate content (www vs non-www, trailing slashes)
- [ ] Page speed scores (Core Web Vitals all green)
- [ ] Mobile-friendly (responsive design verified)
- [ ] No broken links (404 errors)
- [ ] Canonical tags set on all pages
- [ ] Structured data / schema markup present

### Step 2: On-Page SEO
For each key page:
- [ ] Unique, descriptive title tag (50-60 characters)
- [ ] Meta description (120-155 characters, includes CTA)
- [ ] H1 tag present and descriptive (one per page)
- [ ] Header hierarchy logical (H1 → H2 → H3)
- [ ] Images have descriptive alt text
- [ ] Internal links to related pages
- [ ] URL is clean and descriptive (`/pricing` not `/page?id=42`)

### Step 3: Content Audit
- [ ] Key pages exist for target keywords (homepage, features, pricing, blog)
- [ ] Blog has consistent publishing cadence
- [ ] Content matches search intent (informational, transactional, navigational)
- [ ] Thin content pages identified (< 300 words with no value)
- [ ] Content freshness (when was each page last updated?)

### Step 4: Keyword Analysis
- Identify top 10-20 target keywords
- Current ranking position for each
- Search volume and difficulty
- Content gap: keywords competitors rank for that we do not

### Step 5: Off-Page SEO
- [ ] Backlink profile (quantity, quality, relevance)
- [ ] Google Business Profile (if applicable)
- [ ] Social profiles linked
- [ ] Directory listings accurate

### Step 6: Findings Report
Create a Notion page "SEO Audit — [Date]" with:
- Summary: overall SEO health score (Good / Needs Work / Poor)
- Technical findings with fix priority
- On-page optimization opportunities
- Content gaps and recommendations
- Action plan: top 10 items to fix, prioritized by impact

## Stack Context
- **Next.js Metadata API**: Use `generateMetadata` in `layout.tsx` and `page.tsx` for titles and descriptions.
- **Next.js Sitemap**: Generate sitemap with `app/sitemap.ts`.
- **Vercel**: HTTPS and performance handled by default. Edge network for fast loading.
- **Vercel Analytics**: Core Web Vitals monitoring.
- **`next/image`**: Image optimization improves page speed.
- **Notion**: Audit report and action plan stored in Notion.

```typescript
// app/sitemap.ts
import type { MetadataRoute } from 'next';

export default function sitemap(): MetadataRoute.Sitemap {
  return [
    { url: 'https://yourdomain.com', lastModified: new Date(), changeFrequency: 'weekly', priority: 1 },
    { url: 'https://yourdomain.com/pricing', lastModified: new Date(), changeFrequency: 'monthly', priority: 0.8 },
    // Add all public pages
  ];
}
```

## Quality Gate
- [ ] All checklist items evaluated
- [ ] Technical issues categorized by severity
- [ ] Top 10 action items identified and prioritized
- [ ] Baseline metrics recorded for future comparison
- [ ] Report documented in Notion with date

## Anti-Patterns
- **Audit without action** — an audit report that sits in a folder is wasted effort. Top 10 items must have owners and deadlines.
- **Keyword stuffing** — optimizing for keywords by unnaturally cramming them into content hurts more than it helps.
- **Ignoring technical SEO** — content optimization on a technically broken site is ineffective.
- **One-time audit** — SEO degrades. Audit quarterly.
- **Chasing vanity keywords** — ranking for high-volume, low-intent keywords drives traffic that does not convert.

## Related Skills
- `communications/ai-seo` — AI-specific search optimization
- `communications/site-architecture` — information architecture for SEO
- `communications/schema-markup` — structured data implementation
- `communications/analytics-tracking` — measuring SEO performance
- `communications/content-strategy` — content planning informed by SEO
