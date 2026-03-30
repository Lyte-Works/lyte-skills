---
name: "site-assessment"
description: "Comprehensive website assessment — SEO, GEO/AI discoverability, technical architecture, content, competitive positioning. Use for prospect evaluation, competitor analysis, or client audits."
workers: ["research-analyst", "marketing-strategist", "business-strategist", "systems-architect"]
stack: "aligned"
source: "Lyte Works original — built from field experience"
---

# Site Assessment

A two-pass technical and strategic assessment of any website. Extracts what single-fetch tools miss: meta tags, structured data, rendering method, AI discoverability, and full content structure.

## When to Use

- Evaluating a prospect's current web presence before engagement
- Competitive analysis — understanding what competitors do well and where they're weak
- Client audit — assessing a client's site after or during work to measure progress
- Market research — scanning multiple sites in a vertical to find patterns
- Sales support — building a concrete "here's what we'd fix" pitch

## Workflow

### Step 1: Raw HTML Extraction

Fetch the raw HTML source using `curl -s -L {url}`. This captures everything that content-conversion tools strip out.

**Extract from `<head>`:**

| Signal | What to Find | Why It Matters |
|--------|-------------|----------------|
| Title tag | `<title>` | Primary search result display, keyword targeting |
| Meta description | `<meta name="description">` | Search snippet, click-through rate |
| Open Graph | `og:title`, `og:description`, `og:image`, `og:url`, `og:type` | Social sharing appearance (Facebook, LinkedIn, iMessage) |
| Twitter Card | `twitter:card`, `twitter:title`, `twitter:description`, `twitter:image` | Twitter/X sharing appearance |
| Canonical URL | `<link rel="canonical">` | Duplicate content prevention, authority consolidation |
| Robots | `<meta name="robots">` | Crawl directives — index/noindex, follow/nofollow |
| Geo targeting | `geo.region`, `geo.placename`, `geo.position`, `ICBM` | Local SEO signals |
| Structured data | `<script type="application/ld+json">` | JSON-LD schema markup for rich results and AI understanding |
| Hreflang | `<link rel="alternate" hreflang="x">` | International/multilingual targeting |
| Google verification | `google-site-verification` | Search Console connected |
| Analytics | Google Analytics, GTM, Vercel Analytics, Plausible, etc. | Tracking maturity |
| Performance | `preconnect`, `dns-prefetch`, `preload` | Performance optimization signals |

**Extract from `<body>`:**

| Signal | What to Find | Why It Matters |
|--------|-------------|----------------|
| Rendering method | Is `<body>` empty (SPA) or contains HTML content (SSR/SSG)? | SPAs may be invisible to crawlers and AI models |
| Noscript fallback | `<noscript>` content | SPA fallback for non-JS environments |
| Script sources | Framework detection (React, Vue, Next.js, Nuxt, Astro, etc.) | Tech stack identification |

**SPA Detection Rule:** If `<body>` contains only a mount point like `<div id="root"></div>` or `<div id="app"></div>`, the site is a client-side rendered SPA. Flag this immediately — it means:
- Search engine crawlers *may* not see the full content (Google renders JS, but with delay; other engines may not)
- AI models (ChatGPT, Perplexity, Claude) likely cannot read the page content
- Any assessment tool that reads raw HTML will see an empty page
- The `<noscript>` fallback (if present) is the only thing non-JS clients see

### Step 2: Rendered Content Extraction

Use WebFetch to read the URL. This processes the page through a renderer and returns markdown content.

**Extract:**
- **Heading hierarchy** — H1 (should be exactly one), H2s, H3s. Is there a clear information architecture?
- **Hero/above-the-fold** — What's the first thing a visitor sees? Is the value prop clear in under 5 seconds?
- **Navigation structure** — Main nav links, footer links. How many pages? How deep?
- **Social proof** — Client logos, named companies, testimonials, case studies, trust badges, media mentions
- **Content sections** — Blog/insights, resources, podcast, guides, documentation
- **CTAs** — What actions are visitors asked to take? How many? Are they clear?
- **Contact** — Forms, email, phone, chat widgets, social links
- **Messaging** — Tone, positioning language, who they say they serve, how they differentiate

### Step 3: GEO Assessment (Generative Engine Optimization)

GEO is equal in importance to SEO. Search engines rank pages. Generative engines (ChatGPT, Perplexity, Claude, Gemini, Copilot) answer questions. A site can rank #1 on Google and be completely invisible to AI models. Assess GEO as its own discipline, not a subsection of SEO.

**Structured Data for AI Understanding:**
- Is JSON-LD present? What schema types? (Organization, LocalBusiness, Product, Service, Article, FAQ, HowTo)
- Are entity relationships explicit? (company → services → clients → team members)
- Is there enough structured data for an AI model to build a complete picture of the business?
- Would an AI model querying "best [category] companies" or "[service] for [audience]" find this business?

**Content Accessibility for AI Models:**
- Rendering: SSR/SSG (AI-readable) or CSR/SPA (potentially invisible)?
- Are key facts stated directly in plain text? (what the company does, who they serve, how they differentiate, where they're located)
- Or are facts buried in marketing language, animations, or JS-rendered components?
- Are headings semantic anchors that AI models can use to understand page structure?

**Authority Signals for AI Citation:**
- External mentions: press coverage, earned media, industry publications
- E-E-A-T: Experience, Expertise, Authoritativeness, Trustworthiness demonstrated?
- Team members named with credentials? (AI models cite attributed expertise)
- Client names stated explicitly? (AI models reference named relationships)
- Original research, data, or proprietary insights that AI models would cite as a source?

**AI Search Test (when doing deep assessment):**
- Query ChatGPT, Perplexity, or Claude with questions relevant to the business's domain
- Does the business appear in AI-generated responses?
- How accurately does the AI describe the business?
- What competitors does the AI mention instead? (this is competitive GEO intelligence)

### Step 4: Key Subpages (depth check)

Fetch 2-3 critical subpages to assess content depth:

1. **Blog/insights page** — Does it exist? How many posts? How recent? What topics?
2. **Services/product page** — Clear offering? Well-structured? Good copy?
3. **About page** — Team, story, positioning, trust signals

If the blog has no posts in the last 3 months, flag it. If services are vague, flag it. If about is missing, flag it.

### Step 5: Assessment Scoring

Score each dimension on a 1-5 scale:

| Dimension | 1 (Critical) | 3 (Functional) | 5 (Excellent) |
|-----------|--------------|-----------------|----------------|
| **SEO** | Missing title/description, no robots, no canonical | Basic meta tags present, some gaps | Complete meta, OG, Twitter, canonical, robots, sitemap |
| **GEO** | SPA with no fallback, no structured data, no entity clarity | Some content crawlable, basic JSON-LD | SSR/SSG, complete JSON-LD with entity relationships, facts in plain text, AI models cite the business accurately |
| **Content** | No blog, thin copy, no social proof | Blog exists but stale, basic copy | Active blog, strong copy, named clients, case studies, original insights |
| **Technical** | Slow, no HTTPS, broken links | Functional, basic optimization | Fast, secure, optimized, modern stack |
| **Positioning** | Unclear who they serve or why | Generic but understandable | Sharp positioning, clear differentiation, strong voice |
| **Conversion** | No CTAs, confusing navigation | Basic CTA, functional flow | Clear CTAs, low friction, trust-building path |

**SEO and GEO are scored independently and carry equal weight.** A site can score 5 on SEO and 1 on GEO — this is increasingly common with sites that optimize for Google but are invisible to AI models. The reverse is rare but possible (strong structured data, poor traditional SEO). Both must be addressed.

### Step 6: Competitive Positioning (when comparing multiple sites)

When assessing competitors alongside a primary site:
- Score all sites on the same dimensions
- Identify where the primary site wins and loses
- Find gaps competitors haven't filled (opportunity)
- Note messaging patterns across the vertical (what's table stakes vs. differentiating)

## Stack Context

This skill is stack-agnostic on the *target* site — you're assessing whatever someone else built. But findings inform recommendations through our default stack:

- If the site is a poorly-rendering SPA → recommend Next.js with SSR/SSG
- If structured data is missing → recommend Next.js Metadata API + JSON-LD generation
- If analytics are absent or basic → recommend Vercel Analytics
- If email capture exists but is disconnected → recommend Resend integration
- If content is on a separate CMS → note migration opportunity to MDX or Notion-backed content

## Quality Gate

- [ ] Raw HTML was fetched (not just WebFetch) — `<head>` content is present in findings
- [ ] SPA vs SSR rendering method is identified and flagged
- [ ] All SEO meta tags scored: title, description, OG, Twitter, canonical, robots
- [ ] GEO assessed independently: structured data, AI readability, authority signals, content accessibility
- [ ] SEO and GEO findings are presented with equal weight — neither is a subsection of the other
- [ ] Geo targeting (geographic) checked — distinct from GEO (generative engine optimization)
- [ ] At least 2 subpages were assessed for depth
- [ ] Scores are justified with specific evidence, not vibes
- [ ] If competitive analysis: all sites scored on same dimensions for both SEO and GEO

## Anti-Patterns

- **Single-fetch assessment** — WebFetch alone misses `<head>` content entirely. Always do the raw HTML pass first. This is the #1 failure mode.
- **Assuming content is visible to crawlers** — If the site is an SPA, the content you see in a browser may be invisible to Google, AI models, and assessment tools. Always check the rendering method.
- **Generic findings** — "SEO could be improved" is worthless. Be specific: "Meta description is missing. OG image is set but og:description is empty. No JSON-LD structured data for Organization or LocalBusiness."
- **Promising what's not there** — If the site is actually well-built, say so. Don't manufacture problems to justify engagement. Alignment applies.
- **Ignoring the noscript fallback** — SPA sites with good `<noscript>` content are making an effort. Credit it, but note it's a fallback, not a solution.
- **Skipping subpages** — A homepage can look great while the rest of the site is empty. Always check depth.

## Related Skills

- `seo-audit` — deeper SEO-specific analysis (technical SEO, keyword gaps, backlink profile)
- `ai-discoverability-audit` — focused assessment of how AI models surface the brand
- `competitive-teardown` — strategic competitive positioning analysis
- `content-strategy` — content gap analysis and editorial planning
- `page-cro` — conversion rate optimization for specific pages
