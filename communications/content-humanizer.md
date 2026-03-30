<!-- reconstructed -->
---
name: "content-humanizer"
description: "Rewrite content to feel authentically human — add personality, specificity, and genuine voice"
workers: ["content-writer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Content Humanizer

## When to Use
- Content reads as technically correct but emotionally flat
- Rewriting generic content to match a specific brand voice
- Broader humanization beyond just removing AI tells
- Content needs personality injection

## Workflow

### Step 1: Assess the Content
Read the piece and rate:
- **Personality**: 1-5 (1 = corporate robot, 5 = distinct human voice)
- **Specificity**: 1-5 (1 = vague generalities, 5 = concrete examples)
- **Engagement**: 1-5 (1 = puts you to sleep, 5 = keeps you reading)
- **Authenticity**: 1-5 (1 = could be anyone, 5 = uniquely this person/brand)

### Step 2: Add Specificity
Replace every vague claim with a specific one:
- Before: "We've helped many companies improve their marketing."
- After: "In the past 6 months, we've helped 12 SaaS companies increase their organic traffic by an average of 47%."

### Step 3: Add Personality
- **Opinions**: State what you believe and why
- **Stories**: Add a brief anecdote (1-2 sentences) that illustrates the point
- **Humor** (if on-brand): A well-placed observation or self-deprecating comment
- **Imperfection**: Humans are not perfectly balanced. Lean into a perspective.

### Step 4: Add Rhythm
- Vary sentence length (short. Medium length sentences. And then a longer one that takes its time getting to the point.)
- Start sentences with "And" or "But" (perfectly valid, adds conversational tone)
- Use fragments for emphasis. Like this.
- Use em dashes — they feel more conversational than parentheses

### Step 5: Remove Corporate Filler
Delete:
- "We are committed to..." (just do the thing)
- "Our mission is to..." (show, do not tell)
- "Best-in-class" (says nothing)
- "Synergy" (always)
- "Thought leader" (self-proclaimed thought leadership is not thought leadership)

### Step 6: Read Aloud Test
Read the final version aloud. If you stumble, the reader will stumble. If it sounds like a press release, it needs more work.

## Stack Context
- **Notion**: Humanization pass is a stage in the content workflow in Notion.
- **Next.js**: Humanized content published on the site.
- **Alignment**: Transparent about AI assistance. Humanization is about quality and voice, not hiding AI use.

## Quality Gate
- [ ] Specificity score: at least 4/5
- [ ] Personality score: at least 3/5
- [ ] No corporate filler remaining
- [ ] At least one specific example or data point per section
- [ ] Read aloud test passed
- [ ] Voice matches the brand voice guide

## Anti-Patterns
- **Overcorrecting** — injecting so much personality that the content becomes unprofessional.
- **Fake stories** — do not invent anecdotes. Use real ones or skip them.
- **Personality without substance** — funny but empty content is still empty.
- **Inconsistent voice** — humanized content should match the brand voice guide, not the writer's personal voice.

## Related Skills
- `communications/de-ai-ify` — surgical removal of AI patterns
- `communications/voice-extractor` — establishing the voice to write in
- `communications/copy-editing` — editing fundamentals
- `communications/copywriting` — writing with personality from the start
