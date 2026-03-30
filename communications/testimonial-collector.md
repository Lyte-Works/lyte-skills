<!-- reconstructed -->
---
name: "testimonial-collector"
description: "Framework for gathering, structuring, and deploying customer testimonials across marketing channels"
workers: ["content-writer"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Testimonial Collector

## When to Use
- Website lacks social proof
- Need testimonials for a landing page or pricing page
- Building a testimonial library for ongoing use
- Sales team needs customer proof points

## Workflow

### Step 1: Identify Candidates
Best testimonial sources:
- Customers who recently achieved a result
- Customers who renewed or upgraded
- Customers who referred others
- Support tickets that ended with praise

### Step 2: Ask the Right Way
**Timing**: Ask when the customer is happiest (after a win, after a compliment, after renewal).

**Template:**
```
Subject: Quick favor — would you share your experience?

Hi [Name],

I noticed [specific positive thing — you just hit X milestone / you mentioned Y].

Would you be willing to share a quick testimonial about your experience? It would really help others in a similar situation understand if we're a good fit.

Just 2-3 sentences about:
- What problem were you facing?
- What result have you seen?
- Would you recommend us?

If you're open to it, I can even draft something based on our conversations and you just approve/edit.

Thanks!
```

### Step 3: Structure the Testimonial
Transform raw feedback into structured testimonials:

**Short form** (for cards and badges):
> "[One-sentence result statement]"
> — [Name], [Title], [Company]

**Medium form** (for landing pages):
> "[The problem]. [What we did]. [The result]. [Recommendation]."
> — [Name], [Title], [Company]

**Long form** (for dedicated testimonial sections):
- Challenge they faced
- Why they chose you
- Results achieved
- Recommendation

### Step 4: Collect Supporting Details
For each testimonial:
- [ ] Written approval to use their name and company
- [ ] Photo (headshot preferred)
- [ ] Company logo
- [ ] Permission level: name only / name + company / name + company + photo

### Step 5: Organize in a Testimonial Library
Create a Notion database "Testimonials" with:
- Quote (short, medium, long versions)
- Customer name, title, company
- Industry / segment
- Product/feature referenced
- Use case / theme
- Photo and logo (attached)
- Approval status
- Date collected

### Step 6: Deploy Across Channels
| Location | Format | Example |
|----------|--------|---------|
| Homepage | Short quotes with photos | Testimonial carousel |
| Pricing page | Result-focused quotes | "Increased conversions 40%" |
| Landing pages | Use case-specific quotes | Matched to page audience |
| Email sequences | Social proof element | 1 quote per email |
| Sales proposals | Industry-matched quotes | Relevant to prospect's segment |
| Social media | Customer story posts | LinkedIn posts featuring customers |

## Stack Context
- **Notion**: Testimonial library as a Notion database.
- **Next.js**: Testimonial components as Server Components. Reusable across pages.
- **Tailwind**: Testimonial cards, carousels, and quote components.
- **Resend**: Testimonial request emails sent via Resend.

## Quality Gate
- [ ] At least 5 testimonials collected
- [ ] Each has written approval
- [ ] Short and medium versions available
- [ ] Organized in Notion with searchable properties
- [ ] Deployed on at least 3 locations (homepage, landing page, email)

## Anti-Patterns
- **Fake testimonials** — fabricated quotes are dishonest and legally risky. Only use real customer words.
- **Generic quotes** — "Great product!" means nothing. Push for specific results and details.
- **Collecting without deploying** — a library of testimonials nobody sees is wasted.
- **No approval** — always get written permission before using a customer's name and words.
- **Stale testimonials** — refresh the library annually. Old testimonials from defunct companies erode credibility.

## Related Skills
- `communications/case-study-builder` — longer-form customer stories
- `communications/copywriting` — using testimonials in copy
- `communications/page-cro` — deploying social proof for conversion
- `operations/sales-enablement` — testimonials in sales materials
