<!-- reconstructed -->
---
name: "cold-email"
description: "Cold email outreach copy — subject lines, personalization, follow-up sequences, and deliverability"
workers: ["content-writer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Cold Email

## When to Use
- Reaching prospects who have not heard of the client
- Partnership or collaboration outreach
- Sales prospecting
- PR and media outreach

## Workflow

### Step 1: Target Definition
- Who exactly are you emailing? (title, company size, industry)
- Why would they care? (what problem are you solving for them?)
- What is the ask? (reply, book a call, try a demo — one ask)

### Step 2: Email Structure
```
Subject: [Short, specific, curiosity-driven — 5-8 words]

Hi [Name],

[Opening: 1 sentence showing you researched them — not "I hope this finds you well"]

[Value: 2-3 sentences explaining what you can do for THEM — not about you]

[Proof: 1 sentence of social proof — "We helped [similar company] achieve [result]"]

[CTA: 1 clear, low-commitment ask — "Worth a 15-minute chat this week?"]

[Signature]
```

### Step 3: Subject Line Formulas
- "[Mutual connection] suggested I reach out"
- "Quick question about [their specific initiative]"
- "[Their company] + [your company]"
- "Idea for [specific problem they have]"
- "[Relevant metric] for [their company]"

**Never**: "Following up" (as first email), "Exciting opportunity", "Touching base"

### Step 4: Personalization Tiers
| Tier | Effort | Quality | Use When |
|------|--------|---------|----------|
| **High touch** | 10 min/email | Best | Top 20 prospects |
| **Medium touch** | 3 min/email | Good | Next 50 prospects |
| **Low touch** | Template | Okay | Bulk outreach |

High touch: reference a specific blog post, podcast appearance, or company announcement.
Medium touch: reference their industry or role-specific challenge.
Low touch: template with company name and basic variable swaps.

### Step 5: Follow-Up Sequence
```
Day 0: Initial email
Day 3: Follow-up 1 (add new value, not "just following up")
Day 7: Follow-up 2 (different angle or asset)
Day 14: Break-up email ("Not a fit? No worries — here's [free resource] either way")
```

### Step 6: Deliverability
- Use a verified custom domain (not Gmail)
- Warm up new sending domains
- Keep email volume gradual (start with 10-20/day)
- Include an unsubscribe mechanism
- Do not use spam trigger words

## Stack Context
- **Resend**: Sending platform. Use a verified domain. Monitor bounce and complaint rates.
- **Supabase**: Track outreach state (sent, opened, replied, bounced).
- **Notion**: Outreach scripts and tracking in Notion.
- **Next.js**: If building a landing page for outreach, track UTM parameters from email links.

## Quality Gate
- [ ] Target definition specific (not "everyone")
- [ ] Email is under 150 words
- [ ] One clear CTA per email
- [ ] Subject line is 5-8 words, specific
- [ ] Follow-up sequence planned (3-4 emails)
- [ ] Unsubscribe mechanism included
- [ ] Domain verified and warmed up

## Anti-Patterns
- **"I" focused** — the email should be about them, not you. Count the "I"s vs "you"s.
- **Wall of text** — cold emails should be 100-150 words max.
- **"Just following up"** — add new value in each follow-up, not just a reminder.
- **No research** — generic emails get deleted. Personalize at least the opening line.
- **Too many asks** — one email, one ask. "Book a call" or "reply with thoughts" — not both.

## Related Skills
- `communications/email-sequences` — email automation patterns
- `communications/copywriting` — persuasive writing fundamentals
- `operations/cold-outreach-sequence` — multi-channel outreach cadence
- `operations/sales-enablement` — sales materials that support outreach
