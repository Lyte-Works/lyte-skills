<!-- reconstructed -->
---
name: "cold-outreach-sequence"
description: "Multi-touch cold outreach cadence — email, LinkedIn, and follow-up timing for B2B prospecting"
workers: ["sales-lead"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Cold Outreach Sequence

## When to Use
- B2B prospecting for new business
- Building a multi-channel outreach cadence
- Sales pipeline needs more top-of-funnel leads
- Launching outreach for a new service or market

## Workflow

### Step 1: Build the Target List
| Field | Source |
|-------|--------|
| Name | LinkedIn, company website |
| Title | LinkedIn |
| Company | LinkedIn |
| Email | Company website, email finder tools |
| LinkedIn URL | LinkedIn search |
| Relevance note | Why this person specifically |

### Step 2: Design the Cadence
14-day multi-channel sequence:
```
Day 1:  Email 1 (value-first, personalized)
Day 2:  LinkedIn connection request (personalized note)
Day 4:  Email 2 (different angle, add value)
Day 7:  LinkedIn comment on their post (genuine engagement)
Day 9:  Email 3 (case study or proof point)
Day 12: LinkedIn message (if connected)
Day 14: Email 4 (break-up email)
```

### Step 3: Message Templates

**Email 1 — Value First:**
```
Subject: Idea for [their specific initiative]

Hi [Name],

I saw [specific observation about their company]. [One sentence connecting their challenge to your solution].

We helped [similar company] [achieve specific result]. Would that kind of result be valuable for [their company]?

Worth a 15-minute chat?

[Signature]
```

**Email 2 — Different Angle:**
```
Subject: [Relevant resource] for [their role]

Hi [Name],

Quick follow-up — thought this might be useful: [link to relevant resource, not a pitch].

[One sentence tying the resource to their situation].

Happy to discuss how this applies to [their company] if useful.

[Signature]
```

**Email 4 — Break-up:**
```
Subject: Should I close your file?

Hi [Name],

I've reached out a few times but haven't heard back — totally fine.

If [solving the problem] isn't a priority right now, I'll close your file. If it is, just reply and we can find a time.

Either way, here's [free resource] that might help: [link].

[Signature]
```

### Step 4: Personalization
- Reference something specific (recent post, company news, job change)
- Mention a mutual connection if one exists
- Tailor the value proposition to their role and industry
- Never send identical messages to multiple people at the same company

### Step 5: Track and Iterate
Track in a Notion or spreadsheet:
| Prospect | Day 1 | Day 2 | Day 4 | Day 7 | Day 9 | Day 12 | Day 14 | Status |
|----------|-------|-------|-------|-------|-------|--------|--------|--------|

Review weekly:
- Response rate by email position (which email gets replies?)
- Channel effectiveness (email vs. LinkedIn)
- Message effectiveness (which angle resonates?)

## Stack Context
- **Resend**: Email sending with verified domain.
- **Notion**: Prospect list, tracking, and cadence management.
- **Supabase**: If building a prospecting tool, store prospect data and outreach state.
- **Next.js**: Landing pages for outreach campaigns with UTM tracking.

## Quality Gate
- [ ] Target list researched and personalized
- [ ] Multi-channel cadence designed (email + LinkedIn minimum)
- [ ] Each message adds value (not just "following up")
- [ ] Break-up email included (respectful exit)
- [ ] Tracking system in place
- [ ] Weekly review of response rates

## Anti-Patterns
- **Mass blast** — identical messages to hundreds of people. Personalize or do not send.
- **"Just following up"** — every touchpoint must add value.
- **Single channel** — email-only is easy to ignore. Multi-channel increases visibility.
- **No break-up** — continuing to email someone who is not responding is spam.
- **No tracking** — if you do not measure, you cannot improve.

## Related Skills
- `communications/cold-email` — email copywriting
- `operations/sales-enablement` — materials for outreach
- `communications/linkedin-authority` — LinkedIn presence that supports outreach
- `operations/revops` — pipeline management
