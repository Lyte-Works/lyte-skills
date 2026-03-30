<!-- reconstructed -->
---
name: "email-sequences"
description: "Email drip campaign design — welcome sequences, nurture flows, onboarding emails, and sequence logic"
workers: ["content-writer", "marketing-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Email Sequences

## When to Use
- Setting up a welcome sequence for new subscribers
- Onboarding emails for new users
- Nurture sequence for leads
- Re-engagement for inactive users
- Post-purchase follow-up

## Workflow

### Step 1: Define the Sequence Goal
| Sequence | Goal | Trigger | Length |
|----------|------|---------|--------|
| Welcome | Introduce brand, build trust | New subscriber | 3-5 emails over 2 weeks |
| Onboarding | Activate user, teach key features | New signup | 5-7 emails over 3 weeks |
| Nurture | Move lead toward purchase | Lead captured | 4-6 emails over 4 weeks |
| Re-engagement | Win back inactive users | No login for 30 days | 3 emails over 1 week |
| Post-purchase | Reduce churn, drive upsell | Purchase completed | 3-4 emails over 1 month |

### Step 2: Map the Sequence
Example welcome sequence:
```
Day 0: Welcome + immediate value (what they signed up for)
Day 2: Your story / why this exists
Day 4: Most popular resource / best content
Day 7: Social proof (case study or testimonial)
Day 10: Soft CTA (try the product, book a demo)
```

### Step 3: Write Each Email

**Email structure:**
- **From name**: A person, not a company ("Brandon from Lyte" not "Lyte Team")
- **Subject line**: Short (6-10 words), specific, curiosity or value-driven
- **Preview text**: Extends the subject line (do not repeat it)
- **Opening**: 1-2 sentences, personal, no corporate preamble
- **Body**: One idea per email. Short paragraphs. Conversational tone.
- **CTA**: One clear action per email
- **PS line**: Often the most-read part of an email. Use it.

### Step 4: Implement with Resend
```typescript
// lib/email/sequences.ts
import { Resend } from 'resend';

const resend = new Resend(process.env.RESEND_API_KEY);

export async function sendWelcomeEmail(email: string, name: string) {
  await resend.emails.send({
    from: 'Brandon <brandon@yourdomain.com>',
    to: email,
    subject: `Welcome, ${name} — here's what's next`,
    html: renderEmailTemplate('welcome', { name }),
  });
}

// Schedule subsequent emails
// Use Supabase to track sequence state
// Use Vercel Cron or Supabase Edge Functions for scheduling
```

### Step 5: Sequence State Management
```sql
-- Track where each user is in the sequence
CREATE TABLE email_sequences (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  user_email TEXT NOT NULL,
  sequence_name TEXT NOT NULL,
  current_step INT DEFAULT 0,
  started_at TIMESTAMPTZ DEFAULT now(),
  last_sent_at TIMESTAMPTZ,
  completed BOOLEAN DEFAULT false,
  UNIQUE(user_email, sequence_name)
);
```

### Step 6: Measure
| Metric | Good | Needs Work |
|--------|------|-----------|
| Open rate | >40% | <25% |
| Click rate | >5% | <2% |
| Unsubscribe rate | <0.5% | >1% |
| Sequence completion | >60% | <40% |

## Stack Context
- **Resend**: Email delivery. 100 emails/day on free tier.
- **Next.js**: Server Actions for triggering emails. API routes for webhook processing.
- **Supabase**: Track sequence state and subscriber data.
- **Vercel Cron**: Schedule daily email sending jobs.
- **Notion**: Sequence copy drafted in Notion before implementation.

## Quality Gate
- [ ] Sequence goal defined
- [ ] Sequence mapped with timing and content for each email
- [ ] Each email has one clear CTA
- [ ] Subject lines are specific and compelling
- [ ] Sequence state tracking implemented
- [ ] Unsubscribe mechanism included
- [ ] Metrics tracked and reviewed weekly

## Anti-Patterns
- **No unsubscribe** — legally required. Always include it.
- **Too many CTAs** — one email, one action. Do not ask them to read a blog, follow on LinkedIn, AND buy.
- **Corporate tone** — emails from "The Team" with corporate language get ignored. Write like a person.
- **No timing logic** — sending all 5 emails in one day is not a sequence. Space them out.
- **Ignoring metrics** — if open rates drop, the subject lines need work. If clicks drop, the content or CTA needs work.

## Related Skills
- `communications/cold-email` — outbound email copy
- `communications/copywriting` — email copywriting fundamentals
- `communications/newsletter` — ongoing email content
- `communications/onboarding-cro` — onboarding flow optimization
