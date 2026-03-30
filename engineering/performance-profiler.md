<!-- reconstructed -->
---
name: "performance-profiler"
description: "Web performance profiling — Core Web Vitals, bundle analysis, rendering optimization, and performance budgets"
workers: ["devops-engineer", "frontend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Performance Profiler

## When to Use
- Core Web Vitals scores are poor
- Page load time is slow
- Bundle size is larger than expected
- Client reports "the site feels slow"
- Pre-launch performance audit

## Workflow

### Step 1: Measure Core Web Vitals
| Metric | Good | Needs Improvement | Poor |
|--------|------|--------------------|------|
| LCP (Largest Contentful Paint) | < 2.5s | 2.5-4.0s | > 4.0s |
| INP (Interaction to Next Paint) | < 200ms | 200-500ms | > 500ms |
| CLS (Cumulative Layout Shift) | < 0.1 | 0.1-0.25 | > 0.25 |

Tools: Vercel Speed Insights, Lighthouse, PageSpeed Insights

### Step 2: Bundle Analysis
```bash
# Install bundle analyzer
npm install @next/bundle-analyzer

# next.config.ts
import bundleAnalyzer from '@next/bundle-analyzer';
const withBundleAnalyzer = bundleAnalyzer({ enabled: process.env.ANALYZE === 'true' });
export default withBundleAnalyzer({ /* config */ });

# Run analysis
ANALYZE=true npm run build
```

Check for:
- Large dependencies that can be replaced or tree-shaken
- Client-side code that should be server-side
- Duplicate packages
- Unused imports

### Step 3: Rendering Optimization
| Issue | Fix |
|-------|-----|
| Client Component when Server would work | Remove `"use client"`, move state up |
| Large client bundle | Dynamic import with `next/dynamic` |
| Unoptimized images | Use `next/image` with appropriate sizes |
| External fonts | Use `next/font` for self-hosting |
| Layout shift from images | Set `width` and `height` or use `fill` |
| Slow data fetching | Parallel fetches, caching, ISR |

### Step 4: Image Optimization
```typescript
import Image from 'next/image';

// Always specify dimensions
<Image src="/hero.jpg" alt="Hero" width={1200} height={600} priority />

// For responsive images
<Image src="/hero.jpg" alt="Hero" fill className="object-cover" sizes="100vw" priority />

// Priority for above-the-fold images only
```

### Step 5: Caching Strategy
```typescript
// Static page (cached at build time)
export const revalidate = false; // or omit for default static

// ISR (revalidate every hour)
export const revalidate = 3600;

// Dynamic (no cache)
export const dynamic = 'force-dynamic';
```

### Step 6: Performance Budget
Set limits and enforce:
| Metric | Budget |
|--------|--------|
| First Load JS | < 100KB |
| Page-specific JS | < 50KB |
| LCP | < 2.5s |
| Total page weight | < 500KB |
| Time to Interactive | < 3.5s |

## Stack Context
- **Vercel Speed Insights**: Real User Monitoring (RUM) for Core Web Vitals.
- **Next.js**: Server Components reduce client JS. `next/image` and `next/font` for asset optimization.
- **Tailwind CSS**: CSS is purged at build time — only used classes ship. Minimal CSS overhead.
- **Vercel Edge Network**: Static assets served from edge locations globally.

## Quality Gate
- [ ] Core Web Vitals all "Good" (green)
- [ ] Bundle analyzed and large dependencies addressed
- [ ] All images use `next/image`
- [ ] All fonts use `next/font`
- [ ] Above-the-fold images have `priority`
- [ ] Performance budget defined and met

## Anti-Patterns
- **Premature optimization** — measure first, then optimize. Do not guess where the bottleneck is.
- **`"use client"` on everything** — every Client Component adds to the JS bundle.
- **Unoptimized images** — raw images without `next/image` are the #1 cause of poor LCP.
- **No performance budget** — without a budget, performance degrades incrementally and nobody notices.
- **Measuring only once** — performance changes with every deploy. Monitor continuously.

## Related Skills
- `engineering/frontend` — frontend code that affects performance
- `engineering/devops` — deployment and monitoring
- `strategy/product-analytics` — performance as a product metric
- `communications/page-cro` — performance affects conversion
