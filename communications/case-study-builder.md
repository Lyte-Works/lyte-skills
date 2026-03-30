<!-- reconstructed -->
---
name: "case-study-builder"
description: "Structured case study creation — customer story framework, data collection, writing, and publishing"
workers: ["content-writer"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Case Study Builder

## When to Use
- Client has a success story worth telling
- Sales team needs proof points
- Website needs social proof content
- Customer achieved measurable results

## Workflow

### Step 1: Select the Customer
Best case study candidates:
- Achieved measurable results (numbers, not just feelings)
- Represent the ideal customer profile
- Are willing to be named and quoted
- Used the product/service in a way that is replicable

### Step 2: Customer Interview
Interview questions (30 minutes):
1. What was the situation before? (the problem)
2. What had you tried before? (alternatives that failed)
3. Why did you choose us? (decision criteria)
4. What was the implementation like? (process)
5. What results have you seen? (specific metrics)
6. What surprised you? (unexpected value)
7. What would you tell someone considering us? (testimonial)

### Step 3: Case Study Structure
```markdown
# [Customer Name]: [Headline with result]

## The Challenge
[2-3 paragraphs describing the problem before using the product]

## The Solution
[2-3 paragraphs describing what they chose and why]

## The Results
[Specific metrics in a callout or table]
- [Metric 1]: [Before] → [After]
- [Metric 2]: [Before] → [After]
- [Metric 3]: [Before] → [After]

## Key Quote
> "[Direct quote from the customer]"
> — [Name], [Title], [Company]

## About [Customer Company]
[1 paragraph about who they are]
```

### Step 4: Visual Elements
- Customer logo
- Before/after metrics (large, visual)
- Customer photo (if available)
- Pull quotes (highlighted)

### Step 5: Publish and Distribute
- Publish on the website (`app/resources/case-studies/[slug]/page.tsx`)
- Add to the homepage or relevant landing pages
- Send to the sales team as a sales asset
- Share on social media
- Include in relevant email sequences
- Add schema markup (Article type)

### Step 6: Get Approval
Always get written approval from the customer before publishing. Send the draft for review.

## Stack Context
- **Next.js**: Case study pages as Server Components. Dynamic routes for each study.
- **Tailwind**: Styled with callout boxes for metrics, pull quotes for testimonials.
- **Notion**: Draft and approval workflow in Notion.
- **Vercel Analytics**: Track case study page performance.
- **Vercel**: SEO-optimized Server Component pages.

## Quality Gate
- [ ] Customer interview completed
- [ ] Specific metrics included (not vague "improved performance")
- [ ] Direct customer quote included
- [ ] Customer approval obtained (written)
- [ ] Published on website with proper metadata
- [ ] Distributed to sales team and social channels

## Anti-Patterns
- **No metrics** — "they loved it" is not a case study. Include specific numbers.
- **No customer voice** — a case study without a direct quote feels like marketing, not proof.
- **Publishing without approval** — always get written sign-off from the customer.
- **One and done** — case studies should be actively used in sales, email, and social. Not just published and forgotten.
- **Only success stories** — honesty about challenges encountered builds more credibility than a flawless narrative.

## Related Skills
- `communications/testimonial-collector` — gathering shorter proof points
- `communications/copywriting` — writing the case study
- `communications/content-strategy` — case studies within content plan
- `operations/sales-enablement` — case studies as sales assets
