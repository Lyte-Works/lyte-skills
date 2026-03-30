<!-- reconstructed -->
---
name: "competitor-alternatives"
description: "Map and position against specific competitive alternatives including direct competitors, substitutes, and status quo"
workers: ["business-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Competitor Alternatives

## When to Use
- After initial positioning work to sharpen differentiation
- Client frequently loses deals to a specific alternative
- Building "Why Us" or comparison pages for the website
- Creating sales objection-handling materials
- Client asks "how are we different from X?"

## Workflow

### Step 1: List All Alternatives
Enumerate everything a prospective customer might choose instead:
1. **Direct competitors** — same category, same target customer
2. **Indirect competitors** — different category, same job-to-be-done
3. **DIY solutions** — spreadsheets, manual processes, internal tools
4. **Status quo** — doing nothing, living with the problem

### Step 2: Rank by Frequency
For each alternative, estimate how often the client loses to it (or would lose). Rank from most frequent to least. Focus the rest of the analysis on the top 3-5.

### Step 3: Build Alternative Profiles
For each top alternative, document:
- **What it is**: one-sentence description
- **Who chooses it**: what type of buyer, and why
- **Key advantage**: the single strongest reason someone picks this over the client
- **Key weakness**: the single biggest limitation or pain point
- **Switching cost**: how hard is it for someone using this to switch to the client?

### Step 4: Define "Against" Positioning
For each alternative, write a positioning angle:
> "If you're currently using [alternative] and struggling with [weakness], [client] is better because [specific advantage]."

### Step 5: Create Comparison Assets
Based on the positioning angles, draft:
- **Comparison page copy** — for the website (one page per major competitor, or a single comparison table)
- **Objection responses** — for sales conversations
- **Ad angles** — for targeted campaigns against competitor keywords

### Step 6: Document in Notion
Create an "Alternatives Map" page with the full analysis and link to any comparison page drafts.

## Stack Context
- **Next.js**: Comparison pages built as static pages in the App Router (`app/compare/[competitor]/page.tsx`). Use `generateStaticParams` for build-time generation if competitors are known.
- **Tailwind CSS**: Comparison tables use Tailwind's table utilities. Highlight the client's advantages with visual emphasis (color, weight).
- **Vercel**: Comparison pages auto-deploy. Use Vercel Analytics to track which comparison pages get the most traffic and conversions.
- **Notion**: The alternatives map lives in Notion. Sales team references it for objection handling.

## Quality Gate
- [ ] All alternative types covered (direct, indirect, DIY, status quo)
- [ ] Top alternatives ranked by frequency of loss
- [ ] Each alternative has a specific positioning angle (not generic)
- [ ] At least one actionable asset drafted (comparison page, objection response, or ad angle)
- [ ] Positioning angles are honest — do not claim superiority where it does not exist
- [ ] Documented in Notion

## Anti-Patterns
- **Ignoring the status quo** — "do nothing" is often the #1 competitor. Always include it.
- **Straw man comparisons** — misrepresenting a competitor's weakness to make yourself look better destroys credibility.
- **Feature checklists** — comparison pages that are just feature checkmarks miss the point. Lead with the customer problem and outcome, not features.
- **Comparing to everyone** — if you try to position against 15 alternatives, you position against none. Focus on the top 3-5.

## Related Skills
- `strategy/positioning` — overall market positioning (this skill sharpens it per-alternative)
- `strategy/competitive-teardown` — deep analysis of a single competitor
- `communications/copywriting` — writing the actual comparison page copy
- `communications/paid-ads` — running campaigns targeting competitor keywords
- `operations/sales-enablement` — battle cards and objection handling
