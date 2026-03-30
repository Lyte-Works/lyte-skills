<!-- reconstructed -->
---
name: "copy-editing"
description: "Copy editing — style, tone, grammar, clarity, and consistency editing for all written content"
workers: ["content-writer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Copy Editing

## When to Use
- Reviewing and polishing draft copy before publishing
- Ensuring consistency across website pages
- Editing AI-generated content for quality
- Establishing and enforcing a style guide
- Final pass before launch

## Workflow

### Step 1: Style Guide Check
If the client has a style guide, reference it. If not, establish basics:
- **Tone**: Professional but approachable / Casual and friendly / Technical and precise
- **Voice**: First person (we/our) or third person (the company)
- **Formatting**: Oxford comma? Sentence case or title case for headings?
- **Terminology**: Consistent terms for key concepts (e.g., "users" not "customers/clients/users" interchangeably)

### Step 2: Structural Edit
- [ ] Does the piece follow a logical structure?
- [ ] Is there a clear beginning, middle, and end?
- [ ] Does each section earn its place?
- [ ] Are transitions smooth between sections?
- [ ] Is the CTA positioned correctly?

### Step 3: Line Edit
- [ ] Sentences are concise (cut unnecessary words)
- [ ] Paragraphs are short (2-3 sentences for web)
- [ ] Active voice preferred over passive
- [ ] No jargon without explanation
- [ ] Consistent tense throughout
- [ ] Numbers formatted consistently (spell out 1-9, numerals for 10+)

### Step 4: Grammar and Mechanics
- [ ] Subject-verb agreement
- [ ] Proper comma usage
- [ ] No run-on sentences
- [ ] Correct homophone usage (their/there/they're, its/it's)
- [ ] Capitalization consistent
- [ ] Links work and are descriptive (not "click here")

### Step 5: Brand Voice Check
- [ ] Tone matches the brand
- [ ] No off-brand language (too casual, too corporate, too aggressive)
- [ ] Consistent with other published content
- [ ] Reads as one voice, even if multiple people contributed

### Step 6: Final Review
- [ ] Read aloud (catches awkward phrasing)
- [ ] Check on mobile (formatting breaks on small screens?)
- [ ] Verify all facts, names, and numbers
- [ ] Metadata correct (title, description)
- [ ] No placeholder text remaining

## Stack Context
- **Notion**: Draft → edit → review workflow in Notion. Use comments for feedback.
- **Next.js**: Final copy implemented in page components.
- **Tailwind**: Text formatting (line height, max width for readability) should be consistent.

## Quality Gate
- [ ] All checklist steps completed
- [ ] Style guide referenced or established
- [ ] Read aloud test passed
- [ ] Reviewed on mobile
- [ ] No placeholder text or TODO notes remaining

## Anti-Patterns
- **Editing while writing** — write the draft first, then edit. Do not do both simultaneously.
- **Over-editing** — editing the voice out of a piece makes it sterile. Preserve personality.
- **Inconsistent standards** — if you use the Oxford comma on one page, use it on all pages.
- **Skipping mobile review** — copy that looks good on desktop may break on mobile.
- **No style guide** — editing without standards leads to inconsistency.

## Related Skills
- `communications/copywriting` — writing the initial draft
- `communications/de-ai-ify` — removing AI-sounding patterns
- `communications/content-humanizer` — making content feel more human
- `communications/voice-extractor` — establishing the voice to edit toward
