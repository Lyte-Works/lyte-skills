<!-- reconstructed -->
---
name: "ab-test-setup"
description: "A/B test design — hypothesis formation, experiment setup, statistical significance, and result interpretation"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# A/B Test Setup

## When to Use
- Testing a hypothesis about what improves conversion
- Comparing two versions of a page, headline, or CTA
- Validating a change before rolling it out to all users
- Data-driven decision-making for marketing or product changes

## Workflow

### Step 1: Form a Hypothesis
Template: "If we [change], then [metric] will [improve/increase/decrease] because [reason]."

Example: "If we change the CTA from 'Sign Up' to 'Start Free Trial,' then signup rate will increase because it reduces perceived commitment."

### Step 2: Define the Test
| Element | Value |
|---------|-------|
| **Test name** | Descriptive name |
| **Hypothesis** | If/then/because statement |
| **Metric** | Primary metric to measure |
| **Variants** | Control (A) and variant (B) — describe each |
| **Sample size** | Minimum for statistical significance |
| **Duration** | How long to run |
| **Success criteria** | What improvement is meaningful? |

### Step 3: Calculate Sample Size
For a meaningful test:
- Baseline conversion rate (current)
- Minimum detectable effect (smallest improvement that matters, usually 10-20%)
- Statistical significance level (95% = standard)
- Statistical power (80% = standard)

Rule of thumb: need ~400 conversions per variant for a test that detects a 10% relative change.

### Step 4: Implementation
Simple server-side A/B test:
```typescript
// middleware.ts — randomly assign variant
import { NextResponse } from 'next/server';

export function middleware(request: NextRequest) {
  const variant = request.cookies.get('ab-variant')?.value;
  if (!variant) {
    const response = NextResponse.next();
    response.cookies.set('ab-variant', Math.random() > 0.5 ? 'a' : 'b', {
      maxAge: 60 * 60 * 24 * 30, // 30 days
    });
    return response;
  }
}

// In the component:
import { cookies } from 'next/headers';

export default function CTASection() {
  const variant = cookies().get('ab-variant')?.value || 'a';
  return (
    <button>{variant === 'a' ? 'Sign Up' : 'Start Free Trial'}</button>
  );
}
```

Track with custom events:
```typescript
track('cta_clicked', { variant: 'a' }); // or 'b'
track('signup_completed', { variant: 'a' }); // or 'b'
```

### Step 5: Run the Test
- Do not peek at results before the test reaches sample size
- Do not stop early because one variant "looks better"
- Run for at least 1 full week (captures day-of-week variation)
- Do not change anything else during the test

### Step 6: Analyze Results
- Calculate conversion rate for each variant
- Check for statistical significance (95% confidence)
- If significant: implement winner, document learning
- If not significant: the change does not matter. Either test a bigger change or move on.

Document in Notion:
- Test name, hypothesis, variants
- Results (conversion rates, confidence level)
- Decision (implement winner / no change / iterate)
- Learning (what did we learn about our users?)

## Stack Context
- **Next.js**: Server-side variant assignment via middleware and cookies.
- **Vercel Analytics**: Custom event tracking per variant.
- **Tailwind**: Variant styling differences.
- **Notion**: Test documentation and results log.

## Quality Gate
- [ ] Hypothesis written in if/then/because format
- [ ] Primary metric defined
- [ ] Sample size calculated
- [ ] Only one variable changed between variants
- [ ] Test ran to completion (not stopped early)
- [ ] Results documented with statistical confidence

## Anti-Patterns
- **Peeking** — checking results daily and stopping when it "looks good" leads to false positives.
- **Testing too many things** — one variable per test. If you change headline AND CTA, you cannot learn which mattered.
- **No hypothesis** — "let's see what happens" is not a test. State what you expect and why.
- **Tiny sample sizes** — 50 visitors per variant is not enough for meaningful results.
- **Never acting on results** — running tests but never implementing winners is wasted effort.

## Related Skills
- `communications/page-cro` — CRO that generates test hypotheses
- `communications/copywriting` — copy variations for testing
- `strategy/marketing-psychology` — psychological principles to test
- `strategy/product-analytics` — measurement infrastructure
