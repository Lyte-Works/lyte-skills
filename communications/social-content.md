<!-- reconstructed -->
---
name: "social-content"
description: "Platform-native social media content creation — LinkedIn, Twitter/X, and platform-specific formats"
workers: ["content-writer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Social Content

## When to Use
- Creating social media posts for campaigns
- Repurposing content for social platforms
- Building a consistent social posting cadence
- Platform-specific content optimization

## Workflow

### Step 1: Platform Rules
| Platform | Best Format | Tone | Frequency | Key Rule |
|----------|-----------|------|-----------|---------|
| LinkedIn | Text posts, carousels | Professional but human | 3-5x/week | Value first, hook in first line |
| Twitter/X | Short threads, hot takes | Concise, opinionated | 1-3x/day | Say it in fewer words |
| Instagram | Visuals, reels, carousels | Visual, aspirational | 3-5x/week | Image quality matters most |

### Step 2: Content Types
| Type | Purpose | Example |
|------|---------|---------|
| Insight | Establish authority | "3 things I learned from [experience]" |
| Story | Build connection | "Last month we [did something] — here's what happened" |
| How-to | Provide value | "Step-by-step: How to [achieve outcome]" |
| Opinion | Drive engagement | "Unpopular opinion: [contrarian take]" |
| Case study | Show proof | "How [client] achieved [result] in [timeframe]" |
| Curated | Show awareness | "Best [resources] I found this week" |
| Question | Drive engagement | "What's your biggest challenge with [topic]?" |

### Step 3: Post Structure

**LinkedIn post:**
```
[Hook — bold statement or question]

[Context — 2-3 short paragraphs]

[Value — framework, list, or insight]

[CTA — question or engagement prompt]
```

**Twitter/X thread:**
```
1/ [Hook — the tweet that stops the scroll]
2-5/ [Value — one point per tweet]
6/ [Summary + CTA]
```

### Step 4: Repurposing Pipeline
One piece of content becomes many:
```
Blog post → LinkedIn text post (key insight)
         → Twitter thread (main points)
         → Email newsletter excerpt
         → Social card image
```

### Step 5: Scheduling
Use Notion to plan and track:
- Content calendar with publish dates
- Platform assignment per post
- Status: Draft → Approved → Published
- Link to published post
- Engagement metrics (added after publishing)

### Step 6: Engagement
After publishing:
- Reply to every comment within 2 hours
- Share to relevant communities (when genuinely helpful)
- Tag mentioned people or companies
- Track what resonates for future content

## Stack Context
- **Notion**: Social content calendar and tracking.
- **Next.js**: Blog content that gets repurposed for social.
- **Vercel Analytics**: Track social referral traffic to the website.
- **Tailwind**: Social card/OG images styled with Tailwind (via social-card-gen skill).

## Quality Gate
- [ ] Content tailored per platform (not cross-posted identically)
- [ ] Hook in the first line of every post
- [ ] Each post has one clear purpose
- [ ] Publishing cadence consistent
- [ ] Engagement maintained (replies within 2 hours)
- [ ] Metrics tracked in Notion

## Anti-Patterns
- **Cross-posting** — the same text on LinkedIn and Twitter does not work. Each platform has different norms.
- **Selling in every post** — social is about value and connection. 80% value, 20% promotion.
- **Hashtag spam** — 1-3 relevant hashtags max. Not #Every #Word #Is #A #Hashtag.
- **No engagement** — posting and disappearing kills reach. Engage before and after publishing.
- **Inconsistency** — algorithms reward consistency. 3 posts/week every week beats 10 posts one week and 0 the next.

## Related Skills
- `communications/linkedin-authority` — LinkedIn-specific strategy
- `communications/copywriting` — writing fundamentals
- `communications/content-strategy` — social within broader content plan
- `communications/social-card-gen` — creating visual social content
