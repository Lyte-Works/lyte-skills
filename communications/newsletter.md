<!-- reconstructed -->
---
name: "newsletter"
description: "Newsletter creation and curation — format design, content sourcing, subscriber growth, and delivery"
workers: ["content-writer"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Newsletter

## When to Use
- Starting a newsletter for a brand or company
- Improving an existing newsletter's engagement
- Building an email subscriber base
- Establishing a regular content distribution channel

## Workflow

### Step 1: Define the Newsletter
- **Name**: Memorable, descriptive
- **Frequency**: Weekly (most common), biweekly, or monthly
- **Format**: Curated links, original content, or hybrid
- **Value proposition**: In one sentence, why should someone subscribe?
- **Target audience**: Same as the product's target customer

### Step 2: Choose a Format
| Format | Effort | Best For |
|--------|--------|---------|
| Curated links + commentary | Medium | Industry thought leadership |
| Original essay/insight | High | Personal brand building |
| Company updates + content | Low | Customer communication |
| Data/metrics roundup | Medium | Data-driven audiences |
| Hybrid (1 insight + curated) | Medium | Most versatile |

### Step 3: Newsletter Template
```
Subject: [Newsletter Name] #[Issue Number] — [Headline]

[Opening — 2-3 sentences, personal, sets the theme]

## Main Insight
[One original thought, story, or analysis — 200-300 words]

## Worth Reading
- [Link 1]: [One-sentence description of why it matters]
- [Link 2]: [One-sentence description]
- [Link 3]: [One-sentence description]

## Quick Take
[One sentence opinion on a trending topic]

[CTA — reply, share, or check out something]

---
[Unsubscribe link]
```

### Step 4: Build with Resend
```typescript
// app/api/newsletter/send/route.ts
import { Resend } from 'resend';
import { supabase } from '@/lib/db';

const resend = new Resend(process.env.RESEND_API_KEY);

export async function POST(request: Request) {
  const { subject, html } = await request.json();

  // Get all active subscribers
  const { data: subscribers } = await supabase
    .from('subscribers')
    .select('email')
    .eq('status', 'active');

  // Send via Resend batch
  // Note: Resend free tier is 100 emails/day
  for (const subscriber of subscribers || []) {
    await resend.emails.send({
      from: 'Newsletter <newsletter@yourdomain.com>',
      to: subscriber.email,
      subject,
      html,
    });
  }

  return Response.json({ sent: subscribers?.length || 0 });
}
```

### Step 5: Subscriber Growth
- **Website**: Email capture on blog posts, homepage, and dedicated subscribe page
- **Social**: Promote best issues on LinkedIn and Twitter
- **Content**: Tease newsletter content in social posts
- **Cross-promotion**: Partner with complementary newsletters
- **Referral**: "Share this newsletter" CTA in every issue

### Step 6: Measure
| Metric | Good | Needs Work |
|--------|------|-----------|
| Open rate | >40% | <25% |
| Click rate | >5% | <2% |
| Unsubscribe rate | <0.5% per issue | >1% |
| Growth rate | >5%/month | Flat or declining |

## Stack Context
- **Resend**: Email delivery platform. Verified domain required.
- **Supabase**: Subscriber database with email, status, and subscription date.
- **Next.js**: Subscribe page and email capture forms. Server Actions for signup.
- **Notion**: Newsletter calendar, issue drafts, and performance tracking.
- **Vercel Analytics**: Track newsletter referral traffic to the website.

## Quality Gate
- [ ] Newsletter format and template defined
- [ ] Value proposition clear (why subscribe?)
- [ ] Consistent publishing schedule
- [ ] Subscriber growth strategy active
- [ ] Each issue has a clear theme and CTA
- [ ] Metrics tracked and reviewed
- [ ] Unsubscribe mechanism working

## Anti-Patterns
- **Inconsistent schedule** — promise weekly, deliver randomly. Consistency builds trust.
- **All promotion** — newsletters that only promote the product lose subscribers.
- **No personality** — generic newsletters are forgettable. Have a voice.
- **No growth strategy** — "if we write it, they will subscribe" does not work.
- **Buying email lists** — never. Destroys deliverability and violates regulations.

## Related Skills
- `communications/email-sequences` — automated email flows
- `communications/content-strategy` — newsletter within content plan
- `communications/copywriting` — writing newsletter copy
- `communications/linkedin-authority` — promoting newsletter on LinkedIn
