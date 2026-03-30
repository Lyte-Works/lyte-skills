<!-- reconstructed -->
---
name: "voice-extractor"
description: "Extract brand voice from existing content — tone analysis, vocabulary patterns, and voice guidelines"
workers: ["content-writer"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Voice Extractor

## When to Use
- Onboarding a new client to understand their existing voice
- Creating a brand voice guide from scratch
- Ensuring consistency across multiple writers
- Before any copywriting or content work begins

## Workflow

### Step 1: Collect Samples
Gather 5-10 pieces of existing content that represent the brand's best voice:
- Website copy (homepage, about page)
- Social media posts (highest-engagement posts)
- Emails (newsletters, customer communications)
- Blog posts (most shared or linked)
- Sales materials (proposals, pitch decks)

### Step 2: Analyze Patterns
For each sample, extract:
- **Tone**: Formal ↔ Casual? Serious ↔ Playful? Technical ↔ Accessible?
- **Vocabulary**: Common words and phrases? Jargon used? Words avoided?
- **Sentence structure**: Short and punchy? Long and flowing? Mixed?
- **Perspective**: First person (I/we)? Second person (you)? Third person?
- **Personality traits**: If the brand were a person, how would you describe them?

### Step 3: Identify the Voice
Summarize the voice in 3-5 adjectives:
Example: "Confident, clear, slightly irreverent, technically competent, anti-corporate"

### Step 4: Create Voice Guidelines
```
# Brand Voice Guide

## Voice in 3 Words
[Adjective 1], [Adjective 2], [Adjective 3]

## We Sound Like
[Description of how we sound — 2-3 sentences]

## We DON'T Sound Like
[Description of what we avoid — 2-3 sentences]

## Vocabulary
### Words We Use
- [word/phrase] — [why]
- [word/phrase] — [why]

### Words We Avoid
- [word/phrase] — [why]
- [word/phrase] — [why]

## Example Sentences
### On-brand:
"[Example of copy that sounds like us]"

### Off-brand:
"[Example of copy that does NOT sound like us]"

## Tone Adjustments
- Blog posts: [slightly more casual / same / slightly more formal]
- Social media: [more casual, shorter sentences]
- Email: [warm, personal, conversational]
- Website: [clear, confident, benefit-focused]
```

### Step 5: Document and Share
Create the voice guide in Notion. Share with all content-producing workers.

## Stack Context
- **Notion**: Voice guide lives in Notion as a reference document for all content workers.
- **Next.js**: Voice guide informs all website copy.
- **Resend**: Voice guide applied to email copy.

## Quality Gate
- [ ] At least 5 content samples analyzed
- [ ] Voice summarized in 3-5 adjectives
- [ ] "We sound like" and "We don't sound like" sections complete
- [ ] Vocabulary list (use and avoid)
- [ ] Example sentences provided
- [ ] Documented in Notion and shared with team

## Anti-Patterns
- **Extracting from bad samples** — if existing content is poor, do not extract its voice. Create a new voice guide.
- **Too many adjectives** — 3-5 adjectives max. More than that is not a voice, it is a list.
- **Vague descriptions** — "professional and friendly" describes every brand. Be specific.
- **No examples** — guidelines without examples are hard to follow. Always include on-brand and off-brand examples.
- **Static document** — the voice guide should evolve as the brand evolves. Review annually.

## Related Skills
- `communications/copywriting` — applying the voice to copy
- `communications/copy-editing` — editing for voice consistency
- `communications/de-ai-ify` — ensuring AI content matches the voice
- `communications/content-humanizer` — humanizing content to match the voice
