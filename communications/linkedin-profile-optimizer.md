<!-- reconstructed -->
---
name: "linkedin-profile-optimizer"
description: "Optimize LinkedIn company and personal profiles — headlines, about sections, featured content, and SEO"
workers: ["pr-manager"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# LinkedIn Profile Optimizer

## When to Use
- New client onboarding (optimize founder/company LinkedIn)
- LinkedIn profile has low visibility or engagement
- Rebranding or repositioning requires profile updates
- Preparing for a launch that will drive LinkedIn traffic

## Workflow

### Step 1: Personal Profile Optimization

**Headline** (220 characters):
Not your job title. State the outcome you deliver.
- Before: "CEO at CompanyName"
- After: "Helping B2B SaaS companies grow from $1M to $10M ARR | CEO at CompanyName"

**About section** (2,600 characters):
```
[Hook — first 3 lines visible before "see more"]
Line 1: Bold statement about what you do or believe
Line 2: Who you help and the outcome you deliver
Line 3: Proof (numbers, credentials, or recognizable names)

[Body]
Your story in 2-3 short paragraphs. How you got here, what you've learned,
what drives you.

[CTA]
What should someone do next? (connect, visit website, DM me, sign up)

[Keywords]
Include relevant industry terms naturally for LinkedIn search SEO.
```

**Featured section:**
Pin 3-5 items:
- Best-performing LinkedIn post
- Company website link
- Case study or lead magnet
- Recent press or podcast appearance

**Experience:**
- Current role: describe outcomes, not responsibilities
- Include media (images, links, documents)

**Banner image:**
- Reinforce positioning (not a generic stock photo)
- Include a tagline or website URL

### Step 2: Company Page Optimization

**Tagline** (120 characters):
Clear statement of what the company does and for whom.

**About** (2,000 characters):
- What the company does (1-2 sentences)
- Who it serves (specific)
- Key differentiator
- Proof (customers, metrics, awards)
- CTA (website link)

**Page details:**
- Industry, company size, specialties filled out
- Website URL, phone (if applicable)
- Custom button (Visit website or Sign up)

### Step 3: Content Strategy
After optimizing the profile, see the `linkedin-authority` skill for ongoing content strategy.

## Stack Context
- **Notion**: Profile optimization checklist and copy drafts in Notion.
- **Next.js**: Website links from LinkedIn should point to optimized landing pages.
- **Vercel Analytics**: Track LinkedIn referral traffic.

## Quality Gate
- [ ] Headline states outcome, not just job title
- [ ] About section hooks in the first 3 lines
- [ ] Featured section has 3-5 relevant items
- [ ] Banner image reinforces positioning
- [ ] Company page fully completed
- [ ] Keywords included for LinkedIn search SEO

## Anti-Patterns
- **Job title as headline** — missed opportunity. The headline is prime real estate.
- **Empty featured section** — the featured section is above the fold. Use it.
- **Generic banner** — a stock photo says nothing about the brand.
- **No CTA** — every profile section should guide the visitor to the next step.
- **Keyword stuffing** — include keywords naturally, not as a list at the end.

## Related Skills
- `communications/linkedin-authority` — ongoing LinkedIn content strategy
- `communications/social-content` — content creation for LinkedIn
- `communications/voice-extractor` — voice for LinkedIn profile copy
- `strategy/positioning` — positioning that informs the headline
