<!-- reconstructed -->
---
name: "ai-discoverability-audit"
description: "Audit how a brand appears in AI-generated search results — coverage, accuracy, and optimization opportunities"
workers: ["marketing-strategist"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# AI Discoverability Audit

## When to Use
- Brand is not appearing in AI-generated search results
- AI tools describe the product inaccurately
- Evaluating AI search presence alongside traditional SEO
- Quarterly AI visibility check

## Workflow

### Step 1: Query AI Tools
Test your brand across multiple AI platforms:
- ChatGPT: "What is [Brand]?" "Best [category] tools" "[Brand] vs [Competitor]"
- Perplexity: Same queries (shows source citations)
- Claude: Same queries
- Google SGE: Same queries

Document results:
| Query | Platform | Mentioned? | Accurate? | Position | Sources Cited |
|-------|----------|-----------|----------|----------|---------------|

### Step 2: Assess Coverage
- **Branded queries**: Does the AI know what your brand is?
- **Category queries**: Does the AI recommend your product in category lists?
- **Comparison queries**: Does the AI accurately compare you to competitors?
- **Problem queries**: When someone describes the problem you solve, do you appear?

### Step 3: Assess Accuracy
For each mention:
- Is the product description correct?
- Is the pricing current?
- Are features accurately represented?
- Are any claims made that are incorrect?

### Step 4: Source Analysis
Check what sources AI is citing:
- Your own website content
- Third-party reviews (G2, Capterra, etc.)
- Blog posts and articles
- Social media content
- Competitor comparison pages

### Step 5: Gap Identification
| Gap | Impact | Fix |
|-----|--------|-----|
| Not mentioned in category queries | High | Create definitive category content |
| Incorrect pricing shown | High | Update pricing page, add schema |
| Missing from comparison queries | Medium | Create comparison pages |
| Description is vague | Medium | Add clear product definition page |

### Step 6: Action Plan
Create optimization recommendations:
1. Content to create or update (with priority)
2. Schema markup to add
3. Third-party presence to improve (reviews, directory listings)
4. Monitoring cadence (monthly recommended)

## Stack Context
- **Next.js**: Content pages optimized for AI parsing. Clear structure, explicit definitions.
- **Schema markup**: JSON-LD for product, organization, and FAQ.
- **Notion**: Audit results and action plan documented in Notion.
- **Vercel**: Fast, reliable hosting ensures AI crawlers can access content.

## Quality Gate
- [ ] Tested across at least 3 AI platforms
- [ ] Branded, category, comparison, and problem queries tested
- [ ] Accuracy of AI descriptions verified
- [ ] Gaps identified with impact assessment
- [ ] Action plan created with priorities
- [ ] Monitoring schedule established

## Anti-Patterns
- **Testing once** — AI models update frequently. Monitor monthly.
- **Only testing branded queries** — category and problem queries drive discovery.
- **Ignoring third-party sources** — AI cites reviews and articles, not just your website.
- **Manipulating AI** — trying to game AI responses is short-lived. Focus on accurate, comprehensive content.

## Related Skills
- `communications/ai-seo` — technical AI search optimization
- `communications/seo-audit` — traditional SEO audit
- `communications/content-strategy` — content planning for AI discoverability
- `communications/schema-markup` — structured data for machine readability
