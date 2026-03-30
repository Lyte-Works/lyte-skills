<!-- reconstructed -->
---
name: "programmatic-seo"
description: "Template-based page generation at scale for SEO — dynamic pages, data-driven content, and long-tail keyword capture"
workers: ["marketing-strategist", "frontend-developer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Programmatic SEO

## When to Use
- Targeting hundreds or thousands of long-tail keywords
- Building comparison, directory, or location-based pages
- Data exists that can be templatized into useful pages
- Need to scale content production beyond manual writing

## Workflow

### Step 1: Identify the Pattern
Find a repeatable page pattern that serves real search intent:
- "[Product] vs [Competitor]" — comparison pages
- "[Product] for [Industry]" — industry-specific landing pages
- "[Service] in [City]" — location pages
- "Best [Category] tools for [Use Case]" — curated lists
- "[Tool] alternatives" — alternative comparison pages

### Step 2: Validate Demand
Before building, verify:
- Do people actually search for these terms? (keyword research)
- Is there a page-level pattern? (same template, different data)
- Can we provide genuine value? (not just thin placeholder pages)

### Step 3: Build the Data Set
Create a structured data source:
```typescript
// data/comparisons.ts
export const comparisons = [
  {
    slug: 'us-vs-competitor-a',
    competitor: 'Competitor A',
    ourAdvantages: ['Feature 1', 'Feature 2'],
    theirAdvantages: ['Feature 3'],
    verdict: 'Best for teams who need...',
  },
  // ... hundreds of entries
];
```

Or use Supabase for dynamic data:
```sql
CREATE TABLE comparisons (
  slug TEXT PRIMARY KEY,
  competitor TEXT NOT NULL,
  our_advantages JSONB,
  their_advantages JSONB,
  verdict TEXT
);
```

### Step 4: Build the Template
```typescript
// app/compare/[slug]/page.tsx
import { comparisons } from '@/data/comparisons';
import { notFound } from 'next/navigation';

export async function generateStaticParams() {
  return comparisons.map(c => ({ slug: c.slug }));
}

export async function generateMetadata({ params }: Props) {
  const data = comparisons.find(c => c.slug === params.slug);
  if (!data) return {};
  return {
    title: `${data.competitor} vs Us — Honest Comparison`,
    description: `Compare ${data.competitor} and our product. See which is better for your needs.`,
  };
}

export default function ComparisonPage({ params }: Props) {
  const data = comparisons.find(c => c.slug === params.slug);
  if (!data) notFound();

  return (
    <main className="max-w-3xl mx-auto px-4 py-12">
      <h1 className="text-3xl font-bold">{data.competitor} vs Us</h1>
      {/* Template-driven content */}
    </main>
  );
}
```

### Step 5: Ensure Quality
Each generated page must:
- Provide genuine value (not thin content)
- Have unique, useful content (not just swapped names)
- Include proper metadata
- Be interlinked with related pages
- Have a clear CTA

### Step 6: Scale and Monitor
- Start with 10-20 pages. Verify they index and rank.
- Scale to 100+ once the pattern is validated.
- Monitor for thin content warnings in Google Search Console.
- Update data regularly to keep pages fresh.

## Stack Context
- **Next.js**: `generateStaticParams` for build-time page generation. Dynamic routes for the pattern.
- **Supabase**: Data source for large datasets. Query at build time for static generation.
- **Vercel**: ISR (Incremental Static Regeneration) for pages that update frequently.
- **Tailwind**: Consistent template styling across all generated pages.

## Quality Gate
- [ ] Search demand validated for the page pattern
- [ ] Each page provides genuine value (not thin content)
- [ ] Proper metadata on every page
- [ ] Internal linking between related pages
- [ ] Pages indexed in Google Search Console
- [ ] No thin content warnings

## Anti-Patterns
- **Thin content at scale** — generating 1000 pages with just swapped keywords is spam.
- **No validation** — build a small batch first. Do not generate 500 pages without verifying the pattern works.
- **No internal linking** — generated pages need links to and from existing content.
- **Static data** — if competitor pricing changes and your comparison page is wrong, it hurts credibility.
- **Ignoring quality** — each page must pass the test: "Would a human find this useful?"

## Related Skills
- `communications/seo-audit` — SEO strategy that identifies programmatic opportunities
- `communications/site-architecture` — URL structure for programmatic pages
- `communications/content-strategy` — programmatic content within the broader strategy
- `engineering/frontend` — building the page templates
