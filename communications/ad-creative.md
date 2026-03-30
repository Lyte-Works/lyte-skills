<!-- reconstructed -->
---
name: "ad-creative"
description: "Ad creative development — copy, visual direction, and format optimization for paid advertising"
workers: ["performance-marketer", "content-writer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Ad Creative

## When to Use
- Writing ad copy for paid campaigns
- Developing visual concepts for display and social ads
- A/B testing creative variations
- Refreshing underperforming ad creative

## Workflow

### Step 1: Creative Brief
| Element | Answer |
|---------|--------|
| Campaign goal | What action do we want? |
| Target audience | Who are we talking to? |
| Key message | One thing we want them to remember |
| Proof point | Why should they believe us? |
| CTA | What should they do? |
| Tone | Matches brand voice guide |

### Step 2: Ad Copy Formulas
**Headline formulas:**
- [Outcome] in [Timeframe]: "Get 3x more leads in 30 days"
- [Outcome] without [Pain]: "Scale your business without hiring"
- Question: "Still spending 10 hours on manual reports?"
- Social proof: "Join 500+ companies already using..."

**Description formulas:**
- PAS: Problem → Agitate → Solution (in 90 characters)
- Benefit stack: "[Benefit 1]. [Benefit 2]. [Benefit 3]. Try free."
- Testimonial: "[Customer quote]. Start your free trial."

### Step 3: Creative Variations
For each ad group, create:
- **3 headline variations** (different angles: outcome, pain, social proof)
- **2 description variations** (different benefits or proof points)
- **2 visual concepts** (if display/social): product screenshot vs. outcome illustration

### Step 4: Format Specifications
| Platform | Format | Size | Text Limits |
|----------|--------|------|------------|
| Google Search | Text | N/A | 30 char headline x3, 90 char description x2 |
| LinkedIn Single Image | Image + text | 1200x627 | 150 char intro, 70 char headline |
| Meta Feed | Image/Video | 1080x1080 | 125 char primary, 40 char headline |
| Twitter | Image + text | 1200x675 | 280 char |

### Step 5: Test Plan
- Test one variable at a time (headline OR image, not both)
- Run each variation for at least 7 days or 100 clicks
- Declare a winner when statistical significance is reached
- Kill losers, scale winners, create new variations

## Stack Context
- **Notion**: Creative briefs and ad copy drafts in Notion.
- **Tailwind / Next.js**: If creating visual ad assets programmatically, use the social-card-gen skill.
- **Vercel Analytics**: Track performance of traffic from each creative variation.

## Quality Gate
- [ ] Creative brief completed before writing
- [ ] At least 3 headline variations
- [ ] Copy follows proven formulas
- [ ] Specifications match the target platform
- [ ] Test plan defined (one variable at a time)

## Anti-Patterns
- **One ad** — never run a single creative. Always test variations.
- **Feature-led copy** — ads that lead with features instead of outcomes underperform.
- **Ignoring platform norms** — LinkedIn ads should not look like Instagram ads. Adapt to each platform.
- **No proof** — claims without social proof or specifics are ignored.
- **Testing too many variables** — if you change the headline AND image AND CTA, you cannot learn what worked.

## Related Skills
- `communications/paid-ads` — campaign strategy and management
- `communications/copywriting` — copywriting fundamentals
- `communications/page-cro` — landing page that ads point to
- `communications/social-card-gen` — visual asset creation
