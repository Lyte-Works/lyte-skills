<!-- reconstructed -->
---
name: "content-idea-generator"
description: "AI-powered content ideation — generate blog topics, social posts, and content angles from data signals"
workers: ["marketing-strategist", "content-writer"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Content Idea Generator

## When to Use
- Editorial calendar is empty and you need ideas
- Content pipeline is drying up
- Need fresh angles on existing topics
- Turning customer research into content
- Brainstorming for a specific campaign

## Workflow

### Step 1: Gather Input Signals
Collect raw material for ideation:
- **Customer questions**: What do customers ask in support, sales calls, demos?
- **Search queries**: What keywords bring traffic? What related keywords don't have content?
- **Reddit/community signals**: What questions does the audience ask online?
- **Competitor content**: What are competitors publishing? What gaps exist?
- **Industry news**: What trends or changes are relevant?
- **VoC bank**: What language do customers use to describe problems?

### Step 2: Ideation Frameworks

**The Question Flip**: Take every customer question and turn it into a blog post title.
- "How do I...?" → "How to [Do Thing]: A Step-by-Step Guide"
- "What's the difference between...?" → "[Thing A] vs [Thing B]: Which is Right for You?"
- "Why isn't my...?" → "Why Your [Thing] Isn't Working (And How to Fix It)"

**The Listicle Engine**: For every core topic, generate list variations.
- "7 [Topic] Mistakes That Cost You [Outcome]"
- "The Complete [Topic] Checklist for [Year]"
- "5 [Topic] Examples from Companies That [Achieved Outcome]"

**The Contrarian Take**: Challenge conventional wisdom in your space.
- "Why [Common Advice] Is Wrong for [Your Audience]"
- "Stop [Doing Common Thing]: Try [Better Thing] Instead"

**The Data Story**: Turn internal data or research into content.
- "We Analyzed [N] [Things] — Here's What We Found"
- "[Metric] Benchmarks for [Industry] in [Year]"

### Step 3: Score and Prioritize
| Idea | SEO Potential | Audience Interest | Effort | Uniqueness | Score |
|------|-------------|-------------------|--------|-----------|-------|

Score 1-5 on each dimension. Prioritize high-score ideas.

### Step 4: Develop Selected Ideas
For each selected idea, create a brief:
- **Title**: Working title (optimize later)
- **Target keyword**: Primary SEO keyword
- **Angle**: What makes this take unique?
- **Format**: Blog, case study, tool, video
- **Outline**: 3-5 main sections
- **CTA**: What should the reader do next?

### Step 5: Add to Editorial Calendar
Add to the Notion editorial calendar with status "Idea" and all brief details.

## Stack Context
- **Notion**: Ideas stored in Notion database. Brief details as page content. Editorial calendar integration.
- **Next.js**: Published content lives on the Next.js blog.
- **Vercel Analytics**: Measure which content ideas perform best once published.

## Quality Gate
- [ ] At least 3 input signal sources consulted
- [ ] At least 15 ideas generated
- [ ] Ideas scored and ranked
- [ ] Top 5-10 have content briefs
- [ ] Briefs added to editorial calendar in Notion

## Anti-Patterns
- **Generating without data** — ideation without input signals produces generic content.
- **Never executing** — a list of 50 ideas with zero published is not a content strategy.
- **Chasing trends only** — evergreen content compounds. Do not only chase trending topics.
- **Ignoring customer language** — use the VoC bank for titles and angles. Customer words > marketing words.

## Related Skills
- `communications/content-strategy` — editorial calendar that ideas feed into
- `strategy/reddit-insights` — community signals for ideation
- `strategy/customer-research` — customer language for content angles
- `communications/copywriting` — writing the actual content
