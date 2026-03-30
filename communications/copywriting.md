<!-- reconstructed -->
---
name: "copywriting"
description: "Conversion-focused copywriting — frameworks (PAS, AIDA, storytelling), website copy, and persuasive writing"
workers: ["content-writer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Copywriting

## When to Use
- Writing website pages (homepage, about, pricing, landing pages)
- Email copy (sequences, campaigns, newsletters)
- Ad copy (paid ads, social ads)
- Product descriptions and feature explanations
- Any text designed to persuade or convert

## Workflow

### Step 1: Gather Inputs
Before writing a single word:
- **Positioning**: What is the product? Who is it for? Why is it different?
- **VoC bank**: What language do customers use?
- **Goal**: What action should the reader take?
- **Audience**: What do they already know? What do they care about?

### Step 2: Choose a Framework
| Framework | Best For | Structure |
|-----------|---------|-----------|
| **PAS** | Landing pages, ads | Problem → Agitate → Solution |
| **AIDA** | Email, long-form | Attention → Interest → Desire → Action |
| **BAB** | Short copy, social | Before → After → Bridge |
| **4Ps** | Product pages | Promise → Picture → Proof → Push |
| **Storytelling** | Case studies, about pages | Character → Conflict → Resolution |

### Step 3: Write the Headline First
The headline does 80% of the work. Rules:
- Lead with the outcome, not the feature
- Be specific ("Save 10 hours/week" not "Save time")
- Address the reader ("You" not "Our customers")
- Test 5-10 variations before picking one

**Formula**: [Outcome] + [Specificity] + [Without pain point]
- "Get 3x more leads without hiring a marketing team"
- "Ship your landing page in 30 minutes, not 30 days"

### Step 4: Write the Body
**PAS Example:**
```
[Problem] You spend hours every week manually sending follow-up emails.

[Agitate] Meanwhile, your competitors are automating their outreach and
closing deals while you're stuck in your inbox.

[Solution] [Product] automates your entire follow-up sequence. Set it up
once, and every lead gets a personalized follow-up within 5 minutes.
```

### Step 5: Write the CTA
CTA rules:
- Use action verbs ("Start," "Get," "Try" — not "Submit" or "Click here")
- State the value ("Start your free trial" not "Sign up")
- Create urgency when genuine ("Join 500+ companies" not fake countdown timers)
- One CTA per section

### Step 6: Edit
Editing checklist:
- [ ] Cut every word that does not earn its place
- [ ] Replace jargon with plain language
- [ ] Break long paragraphs (2-3 sentences max for web)
- [ ] Read aloud — does it sound natural?
- [ ] Check: is this about the customer (you) or about us (we)?
- [ ] Verify: does every section advance toward the CTA?

## Stack Context
- **Next.js**: Copy lives in page components. Use Server Components for static copy pages.
- **Tailwind**: Typography and spacing affect readability. Use consistent text sizes and line heights.
- **Notion**: Draft copy in Notion for review before implementing in code.
- **Resend**: Email copy sent via Resend.
- **Vercel Analytics**: Measure copy performance via conversion events.

## Quality Gate
- [ ] Inputs gathered (positioning, VoC, goal, audience)
- [ ] Framework chosen and applied
- [ ] Headline tested (at least 5 variations considered)
- [ ] Body follows the framework structure
- [ ] CTA is action-oriented and value-driven
- [ ] Editing checklist completed
- [ ] Copy is about the customer, not the product

## Anti-Patterns
- **Feature-first writing** — "Our AI-powered platform leverages..." Nobody cares about features. Lead with outcomes.
- **Writing for yourself** — you are not the audience. Use customer language from the VoC bank.
- **No framework** — freestyle copy tends to ramble. Frameworks provide structure.
- **Clever over clear** — puns and wordplay sacrifice clarity. Clear always wins.
- **No CTA** — every piece of copy should drive an action. If there is no CTA, what is the point?

## Related Skills
- `communications/copy-editing` — editing and polishing copy
- `communications/email-sequences` — email-specific copy
- `communications/social-content` — social media copy
- `communications/voice-extractor` — finding the right voice
- `communications/de-ai-ify` — making AI-drafted copy sound human
