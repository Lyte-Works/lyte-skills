<!-- reconstructed -->
---
name: "schema-markup"
description: "Structured data implementation — JSON-LD schema for organizations, products, FAQs, articles, and rich results"
workers: ["marketing-strategist", "frontend-developer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Schema Markup

## When to Use
- Improving search appearance with rich results
- AI discoverability optimization
- Adding structured data to a new or existing site
- SEO audit recommends schema implementation

## Workflow

### Step 1: Identify Applicable Schema Types
| Page Type | Schema | Rich Result |
|-----------|--------|------------|
| Homepage | Organization, WebSite | Site links, search box |
| Product/Service | Product, Offer | Price, availability |
| Blog post | Article, BlogPosting | Article snippet |
| FAQ | FAQPage | Expandable FAQ |
| How-to guide | HowTo | Step-by-step snippet |
| Pricing | Product, Offer | Price comparison |
| About | Organization, Person | Knowledge panel |
| Reviews | Review, AggregateRating | Star ratings |

### Step 2: Implementation Pattern
```typescript
// components/schema/organization.tsx
export function OrganizationSchema() {
  const schema = {
    '@context': 'https://schema.org',
    '@type': 'Organization',
    name: 'Company Name',
    url: 'https://yourdomain.com',
    logo: 'https://yourdomain.com/logo.png',
    description: 'One-line company description',
    sameAs: [
      'https://linkedin.com/company/yourcompany',
      'https://twitter.com/yourcompany',
    ],
    contactPoint: {
      '@type': 'ContactPoint',
      email: 'hello@yourdomain.com',
      contactType: 'customer service',
    },
  };

  return (
    <script
      type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify(schema) }}
    />
  );
}

// components/schema/faq.tsx
interface FAQItem { question: string; answer: string; }

export function FAQSchema({ items }: { items: FAQItem[] }) {
  const schema = {
    '@context': 'https://schema.org',
    '@type': 'FAQPage',
    mainEntity: items.map(item => ({
      '@type': 'Question',
      name: item.question,
      acceptedAnswer: {
        '@type': 'Answer',
        text: item.answer,
      },
    })),
  };

  return (
    <script
      type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify(schema) }}
    />
  );
}

// components/schema/article.tsx
export function ArticleSchema({ title, description, datePublished, author, url }: ArticleProps) {
  const schema = {
    '@context': 'https://schema.org',
    '@type': 'Article',
    headline: title,
    description,
    datePublished,
    author: { '@type': 'Person', name: author },
    url,
  };

  return (
    <script
      type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify(schema) }}
    />
  );
}
```

### Step 3: Add Schema to Pages
```typescript
// app/layout.tsx — Organization schema on every page
import { OrganizationSchema } from '@/components/schema/organization';

export default function RootLayout({ children }) {
  return (
    <html>
      <body>
        <OrganizationSchema />
        {children}
      </body>
    </html>
  );
}

// app/faq/page.tsx — FAQ schema on FAQ page
import { FAQSchema } from '@/components/schema/faq';

export default function FAQPage() {
  return (
    <>
      <FAQSchema items={faqItems} />
      {/* Page content */}
    </>
  );
}
```

### Step 4: Validate
- Test with Google Rich Results Test: https://search.google.com/test/rich-results
- Test with Schema.org validator: https://validator.schema.org/
- Check Google Search Console for structured data reports

## Stack Context
- **Next.js**: Schema components as Server Components. JSON-LD injected via `<script>` tags.
- **TypeScript**: Type the schema props for each component.
- **Vercel**: Schema renders server-side, available to crawlers immediately.

## Quality Gate
- [ ] Organization schema on all pages
- [ ] Page-specific schema (Article, FAQ, Product) where applicable
- [ ] All schema validated with Google Rich Results Test
- [ ] No errors in Google Search Console structured data report
- [ ] Schema matches actual page content (no misleading markup)

## Anti-Patterns
- **Schema that does not match content** — marking up a FAQ that does not appear on the page violates Google guidelines.
- **Over-marking** — not every page needs every schema type. Match schema to actual content.
- **Outdated schema** — if prices change but schema is hardcoded, it becomes inaccurate.
- **Ignoring validation** — invalid schema does not generate rich results. Always validate.

## Related Skills
- `communications/seo-audit` — SEO audit evaluates schema coverage
- `communications/ai-seo` — schema improves AI discoverability
- `communications/site-architecture` — IA informs schema strategy
- `engineering/frontend` — implementing schema components
