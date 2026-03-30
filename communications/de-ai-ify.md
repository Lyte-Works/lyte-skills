<!-- reconstructed -->
---
name: "de-ai-ify"
description: "Remove AI-sounding patterns from content — identify and fix robotic phrasing, repetitive structure, and AI tells"
workers: ["content-writer"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# De-AI-ify

## When to Use
- Editing AI-generated content before publishing
- Content "sounds like ChatGPT" and needs a human pass
- Quality control for AI-assisted writing workflows
- Teaching writers to spot and fix AI patterns

## Workflow

### Step 1: Identify AI Tells
Common patterns that signal AI-generated text:

**Vocabulary tells:**
- "Delve," "tapestry," "landscape," "leverage," "robust," "utilize"
- "In today's [digital/modern/fast-paced] landscape/world"
- "It's important to note that..."
- "Let's dive in" / "Let's explore"
- "Game-changer," "cutting-edge," "revolutionize"

**Structure tells:**
- Every paragraph starts with a transition word
- Exactly 3 bullet points per section (AI loves threes)
- Intro paragraph that restates the title
- Conclusion that summarizes everything already said
- Identical sentence length throughout

**Content tells:**
- Hedging on everything ("it depends," "there are many factors")
- No specific opinions or recommendations
- Covers every possible angle instead of taking a stance
- Lacks specific examples, numbers, or personal experience
- Empty phrases that sound good but say nothing

### Step 2: Apply Fixes

**Vocabulary:**
- Replace "utilize" with "use"
- Replace "leverage" with the specific action
- Replace "landscape" with the actual thing
- Delete "It's worth noting that" — just state the thing
- Cut every sentence that starts with "In today's..."

**Structure:**
- Vary paragraph length (1 sentence to 4 sentences)
- Start some paragraphs mid-thought
- Remove transitional filler ("Furthermore," "Moreover," "Additionally")
- Cut the intro paragraph if it just restates the title
- Cut the conclusion if it just restates the article

**Content:**
- Add a specific opinion: "The best approach is X because Y"
- Add a real example with numbers: "We saw a 40% increase when..."
- Remove hedging: replace "it can be beneficial" with "do this"
- Add personality: humor, frustration, enthusiasm — whatever fits the voice
- Delete sentences that add no new information

### Step 3: The "Would a Human Say This?" Test
Read each sentence and ask: "Would the person whose name is on this actually say this in conversation?" If no, rewrite or cut.

### Step 4: Final Pass
- Read aloud — AI text is often grammatically perfect but rhythmically dead
- Check for personality — does it sound like a real person?
- Verify specificity — are there concrete examples, not just generalizations?
- Count the "delve/leverage/robust" words — should be zero

## Stack Context
- **Notion**: De-AI-ify checklist applied during the content review workflow in Notion.
- **Next.js**: Final content published on the site after de-AI-ify pass.
- **Alignment**: This skill directly supports the principle of transparency — content should not pretend to be something it is not.

## Quality Gate
- [ ] No AI vocabulary tells (delve, landscape, leverage, robust, utilize)
- [ ] No AI structure tells (uniform paragraphs, always-three lists)
- [ ] Specific opinions included (not hedged)
- [ ] Real examples or data included
- [ ] "Would a human say this?" test passed
- [ ] Read aloud — sounds natural

## Anti-Patterns
- **Over-correcting** — making content intentionally bad to seem "human." The goal is natural, not sloppy.
- **Hiding AI use** — de-AI-ify is about quality, not deception. If asked, be transparent about AI assistance.
- **Only fixing vocabulary** — swapping words without fixing structure and content is surface-level.
- **Skipping the human** — no amount of de-AI-ify replaces a human review. A person must read the final version.

## Related Skills
- `communications/content-humanizer` — broader approach to humanizing content
- `communications/copy-editing` — editing fundamentals
- `communications/voice-extractor` — the voice to edit toward
- `communications/copywriting` — writing from scratch when editing AI output is not enough
