<!-- reconstructed -->
---
name: "content-strategy"
description: "Content strategy — editorial calendar, content pillars, distribution planning, and content operations"
workers: ["marketing-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Content Strategy

## When to Use
- Building a content program from scratch
- Content exists but is inconsistent or unfocused
- Need to align content with business goals
- Planning content for a launch or campaign
- Quarterly content planning

## Workflow

### Step 1: Define Content Goals
Content must serve a measurable business goal:
| Goal | Content Type | Metric |
|------|-------------|--------|
| Drive organic traffic | Blog, SEO pages | Organic sessions |
| Generate leads | Gated content, free tools | Email signups |
| Nurture prospects | Email sequences, case studies | Conversion rate |
| Support sales | Comparison pages, case studies | Sales cycle length |
| Retain customers | Help docs, tutorials | Churn rate |

### Step 2: Content Pillars (3-5)
Define the core topics your content will cover. Each pillar should:
- Align with what you sell
- Match what your audience searches for
- Be broad enough for ongoing content but specific enough to be ownable

Example for a SaaS company:
1. "[Category] best practices" — educational content
2. "Customer success stories" — social proof
3. "[Industry] trends" — thought leadership
4. "How to [specific workflow]" — tutorial content

### Step 3: Content Formats
| Format | Effort | SEO Value | Lead Gen |
|--------|--------|----------|----------|
| Blog post (800-1500 words) | Medium | High | Medium |
| Pillar page (3000+ words) | High | Very High | Medium |
| Case study | Medium | Medium | High |
| Email newsletter | Low | None | Medium |
| Social post | Low | None | Low |
| Free tool | High | High | Very High |
| Comparison page | Medium | High | High |

### Step 4: Editorial Calendar
Create a Notion database with:
- **Title**: Content title
- **Pillar**: Which content pillar
- **Format**: Blog, case study, social, etc.
- **Target keyword**: Primary SEO keyword
- **Status**: Idea → Outline → Draft → Review → Published
- **Publish date**: Scheduled date
- **Author/Owner**: Who is responsible
- **Distribution**: Where it will be shared after publishing

Plan 4-8 pieces per month for a consistent cadence.

### Step 5: Content Distribution
For each piece of content:
1. **Publish** on the website (Next.js blog)
2. **Email** to subscribers (Resend)
3. **Social** — LinkedIn, Twitter/X (native format, not just links)
4. **Community** — share in relevant communities if genuinely helpful
5. **Repurpose** — turn a blog post into social posts, email content, etc.

### Step 6: Measurement
Monthly content review:
- Traffic per piece (Vercel Analytics)
- Email signups per piece
- Time on page and scroll depth
- Search ranking for target keywords
- Social engagement

## Stack Context
- **Next.js**: Blog built with App Router. Dynamic routes for posts (`app/blog/[slug]/page.tsx`). Server Components for fast loading.
- **Notion**: Editorial calendar and content pipeline managed in Notion.
- **Resend**: Newsletter distribution via Resend. Email templates built in code.
- **Vercel Analytics**: Content performance tracking.
- **Tailwind**: Blog styling with consistent typography.

## Quality Gate
- [ ] Content goals tied to business metrics
- [ ] 3-5 content pillars defined
- [ ] Editorial calendar created with at least 1 month planned
- [ ] Distribution plan for each piece of content
- [ ] Monthly performance review scheduled
- [ ] Content pipeline status visible in Notion

## Anti-Patterns
- **Content without strategy** — publishing random blog posts without a plan wastes effort.
- **SEO-only content** — content optimized only for search, not for readers, performs poorly.
- **No distribution** — "publish and pray" does not work. Plan distribution before publishing.
- **Inconsistent cadence** — 4 posts in January and 0 in February is worse than 2 per month consistently.
- **No measurement** — if you do not know what performs, you cannot improve.

## Related Skills
- `communications/seo-audit` — SEO informs content strategy
- `communications/content-idea-generator` — generating content ideas
- `communications/copywriting` — writing the actual content
- `communications/newsletter` — email distribution channel
- `communications/social-content` — social distribution channel
