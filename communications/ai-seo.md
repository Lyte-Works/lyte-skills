<!-- reconstructed -->
---
name: "ai-seo"
description: "Optimize content for AI search engines and LLM discoverability — structured content, entity clarity, and AI-friendly markup"
workers: ["marketing-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# AI SEO

## When to Use
- Optimizing content for AI search (ChatGPT, Perplexity, Gemini, Claude)
- Ensuring brand/product appears in LLM-generated answers
- Updating SEO strategy for the AI search era
- Creating content that serves both traditional and AI search

## Workflow

### Step 1: Understand AI Search Behavior
AI search engines prefer:
- **Clear, structured answers** to specific questions
- **Authoritative sources** with consistent entity information
- **Well-structured content** with clear headers and logical flow
- **Factual, citation-worthy content** that can be referenced
- **Schema markup** for machine-readable context

### Step 2: Entity Clarity
Ensure your brand/product is clearly defined:
- Consistent name usage across all pages
- Clear "About" or "What is [Product]" page
- Schema markup defining the organization and product
- Wikipedia/Wikidata presence (if appropriate)

### Step 3: Content Structure for AI
Write content that AI can easily parse and cite:
```markdown
## What is [Topic]?
[Clear, concise definition in 1-2 sentences]

## How [Topic] Works
[Step-by-step explanation]

## [Topic] vs [Alternative]
[Direct comparison that AI can reference]

## FAQ
[Question and answer format — AI loves this]
```

### Step 4: AI Discoverability Checklist
- [ ] Every page has a clear, specific topic (one topic per page)
- [ ] Questions are explicitly asked and answered (H2 as question, content as answer)
- [ ] Definitions are provided for key terms
- [ ] Comparisons are explicit and structured
- [ ] Data and statistics are included with sources
- [ ] Content is factually accurate and up-to-date
- [ ] Schema markup covers organization, product, FAQ, and how-to

### Step 5: Technical Implementation
```typescript
// Structured FAQ schema for AI discoverability
// app/faq/page.tsx
export const metadata = {
  title: 'FAQ — [Product Name]',
  description: 'Frequently asked questions about [Product]',
};

// Include JSON-LD FAQ schema
const faqSchema = {
  '@context': 'https://schema.org',
  '@type': 'FAQPage',
  mainEntity: [
    {
      '@type': 'Question',
      name: 'What is [Product]?',
      acceptedAnswer: {
        '@type': 'Answer',
        text: '[Clear, complete answer]',
      },
    },
  ],
};
```

### Step 6: Monitor AI Mentions
- Search for your brand in AI tools (ChatGPT, Perplexity, Claude)
- Note how the AI describes your product
- Identify inaccuracies in AI-generated descriptions
- Update content to correct misrepresentations

## Stack Context
- **Next.js**: Server Components render full HTML that AI crawlers can parse. Metadata API for structured titles/descriptions.
- **Schema markup**: JSON-LD in page components for machine-readable data.
- **Vercel**: Fast, reliable hosting ensures crawlers can access content.
- **Notion**: AI SEO strategy and monitoring documented in Notion.

## Quality Gate
- [ ] Every key page answers a specific question clearly
- [ ] Schema markup implemented for organization, product, and FAQ
- [ ] Content structured with clear headers and logical flow
- [ ] Brand entity consistently defined across the site
- [ ] AI search results monitored monthly
- [ ] Content is factually accurate (AI cites inaccurate content, creating amplified misinformation)

## Anti-Patterns
- **Ignoring AI search** — a growing percentage of search happens through AI tools. Optimize for both.
- **Gaming AI** — trying to manipulate AI responses with misleading content backfires as models improve.
- **Keyword-only thinking** — AI search is about concepts and entities, not just keywords.
- **No monitoring** — if you do not check how AI describes your product, you cannot correct errors.
- **Neglecting traditional SEO** — AI search and traditional SEO are complementary, not exclusive.

## Related Skills
- `communications/ai-discoverability-audit` — comprehensive AI discoverability assessment
- `communications/seo-audit` — traditional SEO audit
- `communications/schema-markup` — technical schema implementation
- `communications/content-strategy` — content planning for both human and AI audiences
