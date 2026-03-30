<!-- reconstructed -->
---
name: "launch-strategy"
description: "Step-by-step go-to-market launch plan with channel-specific playbooks for product or service launches"
workers: ["business-strategist", "marketing-strategist"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Launch Strategy

## When to Use
- Launching a new product, feature, or service
- Re-launching with new positioning
- Entering a new market segment
- Client says "we're ready to launch" but has no plan

## Workflow

### Step 1: Define Launch Goals
Answer these before anything else:
- **What are we launching?** (product, feature, service, brand)
- **Who is the target audience?** (specific segment from positioning work)
- **What does success look like?** (specific metrics: signups, revenue, traffic, press mentions)
- **When is launch day?** (fixed date or flexible?)
- **Budget?** (zero, small, or meaningful paid budget)

### Step 2: Pre-Launch (4-6 weeks before)
1. **Landing page** — build a pre-launch page with email capture (Next.js + Resend)
2. **Waitlist/early access** — if applicable, set up a waitlist with Supabase
3. **Content seeding** — publish 3-5 pieces of content that establish the problem your launch solves
4. **Community warming** — engage in relevant communities (Reddit, LinkedIn, Slack groups) without pitching
5. **Influencer/partner outreach** — identify 5-10 people who could amplify the launch
6. **Email list building** — capture emails via content upgrades, lead magnets, or waitlist

### Step 3: Launch Week Plan
Create a day-by-day calendar:

| Day | Channel | Action |
|-----|---------|--------|
| Day -1 | Email | Send "launching tomorrow" teaser to waitlist |
| Day 0 | Website | Push live. Update homepage, add launch banner |
| Day 0 | Email | Send launch announcement to full list |
| Day 0 | Social | Publish launch posts (LinkedIn, Twitter/X) |
| Day 0 | Communities | Post in relevant communities (ProductHunt, Reddit, HN) |
| Day 1 | Email | Follow-up to non-openers |
| Day 2 | Social | Share first customer reaction / testimonial |
| Day 3 | Content | Publish launch case study or behind-the-scenes |
| Day 5 | Email | "Last chance" or "first week results" update |

### Step 4: Channel Playbooks
For each active channel, define:
- **Message**: What are we saying? (aligned with positioning)
- **Format**: What type of content? (post, video, email, ad)
- **Timing**: When does it go live?
- **Owner**: Who is responsible?
- **Success metric**: How do we measure this channel's contribution?

### Step 5: Launch Day Execution
- Deploy the site update to Vercel (merge to main)
- Send launch emails via Resend
- Publish all scheduled social content
- Monitor Vercel Analytics in real-time for traffic spikes
- Respond to every comment, reply, and mention within 2 hours

### Step 6: Post-Launch Review (1 week after)
Document in Notion:
- What worked? (highest-performing channel, best content, unexpected wins)
- What didn't? (channels that underperformed, content that flopped)
- Key metrics vs. goals
- Lessons for next launch

## Stack Context
- **Next.js + Vercel**: Pre-launch landing page built with App Router. Use Server Actions for email capture. Deploy preview builds for stakeholder review, push to main for launch.
- **Resend**: All launch emails (teaser, announcement, follow-up) sent via Resend. Use the Next.js API route for email capture and sending.
- **Supabase**: If waitlist needed, store signups in Supabase with a simple table. Use Row Level Security.
- **Vercel Analytics**: Primary dashboard for monitoring launch traffic in real-time.
- **Notion**: Launch plan, channel playbooks, and post-launch review all live in Notion.
- **GitHub**: Use feature branches for pre-launch work. Merge to main = deploy = launch.

## Quality Gate
- [ ] Launch goals are specific and measurable (not "get the word out")
- [ ] Pre-launch checklist completed before launch day
- [ ] Day-by-day launch calendar created
- [ ] Each channel has a defined message, format, timing, and success metric
- [ ] Post-launch review scheduled and completed within 1 week
- [ ] All assets documented in Notion

## Anti-Patterns
- **Launching without positioning** — if you cannot articulate who this is for and why it is different, you are not ready to launch.
- **Big bang, no follow-up** — launch day is not the end. The week after launch matters more than launch day itself.
- **Too many channels** — better to do 3 channels well than 8 channels poorly. Pick channels where your audience already is.
- **No pre-launch** — going from zero to launch with no warming period means zero momentum on day one.
- **Vanity metrics** — "impressions" and "reach" are not success metrics. Track actions: signups, purchases, demo requests.

## Related Skills
- `strategy/positioning` — must be done before launch strategy
- `strategy/pricing-strategy` — pricing must be set before launch
- `communications/email-sequences` — building the launch email sequence
- `communications/social-content` — creating launch social posts
- `communications/content-strategy` — content calendar for pre-launch seeding
- `engineering/landing-page-generator` — building the launch landing page
