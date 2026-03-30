<!-- reconstructed -->
---
name: "site-architecture"
description: "Information architecture for SEO — URL structure, internal linking, navigation, and content hierarchy"
workers: ["marketing-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Site Architecture

## When to Use
- Building a new website from scratch
- Redesigning site navigation and URL structure
- SEO audit reveals poor internal linking
- Adding a blog or new content section
- Site has grown organically and needs restructuring

## Workflow

### Step 1: Site Map
Create a hierarchical sitemap:
```
Homepage (/)
├── Product (/product)
│   ├── Features (/product/features)
│   └── Pricing (/pricing)
├── Solutions (/solutions)
│   ├── For Startups (/solutions/startups)
│   └── For Enterprise (/solutions/enterprise)
├── Blog (/blog)
│   ├── [Category] (/blog/category/[name])
│   └── [Post] (/blog/[slug])
├── Resources (/resources)
│   ├── Case Studies (/resources/case-studies)
│   └── Help Center (/help)
├── Company (/company)
│   ├── About (/about)
│   └── Contact (/contact)
└── Legal
    ├── Privacy (/privacy)
    └── Terms (/terms)
```

### Step 2: URL Structure Rules
- Flat and descriptive: `/pricing` not `/company/pages/pricing-page`
- Use hyphens, not underscores: `/case-studies` not `/case_studies`
- Lowercase only
- No file extensions
- No parameters for public pages
- Category in path for blogs: `/blog/seo-guide` or `/blog/category/seo`

### Step 3: Navigation Design
**Primary nav** (5-7 items max):
- Product, Solutions, Pricing, Blog, Contact

**Footer nav** (comprehensive):
- All main pages plus legal, social links, and company info

**Breadcrumbs** (for deep pages):
```
Home > Blog > SEO > How to Do an SEO Audit
```

### Step 4: Internal Linking Strategy
Every page should:
- Link to 2-3 related pages within the content
- Be reachable within 3 clicks from the homepage
- Have at least one internal link pointing to it

**Hub and spoke model:**
- Hub page: `/blog/category/seo` (links to all SEO articles)
- Spoke pages: individual articles link back to the hub and to each other

### Step 5: Next.js Implementation
```typescript
// app/blog/[slug]/page.tsx
// Dynamic routes for blog posts

export async function generateStaticParams() {
  const posts = await getAllPosts();
  return posts.map(post => ({ slug: post.slug }));
}

// app/blog/page.tsx
// Blog listing with category filters

// app/sitemap.ts
// Auto-generated sitemap including all pages
```

### Step 6: Redirect Plan
For site migrations, create a redirect map:
```typescript
// next.config.ts
export default {
  async redirects() {
    return [
      { source: '/old-page', destination: '/new-page', permanent: true },
    ];
  },
};
```

## Stack Context
- **Next.js App Router**: File-based routing creates the URL structure. Route groups for layout organization.
- **Tailwind**: Navigation components styled with Tailwind.
- **Vercel**: Redirects handled via `next.config.ts` or `vercel.json`.
- **Notion**: Site map and IA documentation in Notion.

## Quality Gate
- [ ] Site map documented with all pages
- [ ] URL structure is flat, descriptive, and consistent
- [ ] Primary nav has 5-7 items max
- [ ] Every page reachable within 3 clicks from homepage
- [ ] Internal linking strategy defined (hub and spoke)
- [ ] Redirects configured for any changed URLs
- [ ] Sitemap.xml auto-generated

## Anti-Patterns
- **Deep nesting** — `/company/about/team/leadership/ceo` is bad IA. Keep URLs flat.
- **No internal links** — orphan pages (no links pointing to them) are invisible to search engines.
- **Too many nav items** — 15+ nav items overwhelm users. Prioritize ruthlessly.
- **Changing URLs without redirects** — broken links lose SEO equity and frustrate users.
- **Navigation as afterthought** — plan IA before building pages, not after.

## Related Skills
- `communications/seo-audit` — SEO audit that evaluates site architecture
- `communications/schema-markup` — structured data for IA
- `communications/programmatic-seo` — scaling pages within the IA
- `engineering/frontend` — implementing the navigation and routing
