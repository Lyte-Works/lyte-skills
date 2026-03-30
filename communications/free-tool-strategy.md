<!-- reconstructed -->
---
name: "free-tool-strategy"
description: "Lead generation through free tools — strategy, design, implementation, and conversion optimization"
workers: ["marketing-strategist", "frontend-developer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Free Tool Strategy

## When to Use
- Need a lead generation engine beyond content marketing
- Want to build organic backlinks and social sharing
- Product has a workflow that can be simplified into a free tool
- Competitor offers free tools and captures your audience

## Workflow

### Step 1: Identify Tool Opportunities
Good free tools:
- Solve a small, specific problem related to your product
- Are self-contained (no login required for basic use)
- Produce a shareable output
- Naturally lead to the paid product

Examples: ROI calculators, graders/auditors, generators, converters, checklists.

### Step 2: Design the Tool
- **Input**: What does the user provide? (minimal — 1-5 inputs)
- **Processing**: What does the tool do? (calculation, generation, analysis)
- **Output**: What does the user get? (result, score, document, visual)
- **CTA**: What do you want them to do next? (email for full report, sign up for more, share)

### Step 3: Build with Next.js
```typescript
// app/tools/[tool-name]/page.tsx
// Server Component for the page shell
// Client Component for the interactive tool

export const metadata = {
  title: 'Free [Tool Name] — [Benefit]',
  description: 'Use our free [tool] to [outcome]. No signup required.',
};
```

Architecture:
- Tool page is a Server Component (fast initial load, SEO-friendly)
- Tool interaction is a Client Component (interactive form + results)
- Results can optionally be saved to Supabase (with email capture)
- Full report sent via Resend (email capture mechanism)

### Step 4: Conversion Mechanism
- **Ungated basic use**: Tool works without signup (builds trust, enables sharing)
- **Gated extended value**: Full report, saved results, or advanced features require email
- **CTA to product**: Results page includes a natural bridge to the paid product

### Step 5: SEO and Distribution
- Target "[type] calculator" or "[type] tool" keywords
- Build a dedicated landing page explaining the tool
- Submit to free tool directories
- Share on social media with example outputs
- Include social sharing on the results page

### Step 6: Measure
Track in Vercel Analytics:
- Tool page visits
- Tool completions (form submitted)
- Email captures (gated content conversions)
- Shares
- Tool → product conversion rate

## Stack Context
- **Next.js**: Tool page with Server Component shell + Client Component interaction. Server Actions for email capture and result storage.
- **Tailwind**: Interactive form styling. Results display.
- **Supabase**: Store tool results and user emails (with consent).
- **Resend**: Send full reports or results via email.
- **Vercel Analytics**: Track tool usage and conversion events.
- **Vercel**: Fast loading critical for tools (users abandon slow tools).

## Quality Gate
- [ ] Tool solves a real, specific problem
- [ ] Works without signup (ungated basic use)
- [ ] Clear conversion mechanism to capture email or lead to product
- [ ] SEO-optimized page (title, description, schema)
- [ ] Social sharing enabled on results
- [ ] Analytics tracking on tool completion and email capture

## Anti-Patterns
- **Gate everything** — requiring signup before showing any value kills adoption.
- **Too complex** — the best free tools are simple. 1-3 inputs, instant output.
- **No connection to product** — the tool should naturally lead to "if you liked this, you'll love our product."
- **No SEO** — free tools are a major organic traffic opportunity. Optimize the page.
- **Build and forget** — promote the tool actively. It does not market itself.

## Related Skills
- `communications/content-strategy` — free tools as content pillars
- `communications/page-cro` — optimizing tool conversion
- `engineering/frontend` — building the interactive tool
- `engineering/landing-page-generator` — tool landing page
