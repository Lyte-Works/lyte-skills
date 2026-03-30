<!-- reconstructed -->
---
name: "customer-research"
description: "Interview frameworks, survey design, and persona building for understanding target customers"
workers: ["research-analyst"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Customer Research

## When to Use
- Before positioning or re-positioning work
- Client claims to know their customer but has no data
- Building personas for content strategy or product design
- Churn is increasing and the reason is unclear
- New market entry where customer understanding is low

## Workflow

### Step 1: Define Research Questions
Before talking to anyone, write down 3-5 specific questions you need answered:
- Why did customers choose us over alternatives?
- What was the trigger event that made them look for a solution?
- What would they miss most if we disappeared?
- What almost stopped them from buying?
- How do they describe what we do to other people?

### Step 2: Customer Interviews (5-10 interviews)
**Recruiting**: Ask the client to introduce you to:
- 3-4 happy customers (understand what works)
- 2-3 recently churned customers (understand what failed)
- 1-2 prospects who did not convert (understand objections)

**Interview Script** (30 minutes each):
1. "Tell me about your role and what you're responsible for." (2 min, warm-up)
2. "Walk me through how you found [product/service]." (5 min, discovery journey)
3. "What was happening that made you look for a solution?" (5 min, trigger event)
4. "What alternatives did you consider?" (3 min, competitive landscape)
5. "What almost stopped you from choosing us?" (3 min, objections)
6. "What would you miss most if we disappeared tomorrow?" (3 min, core value)
7. "How would you describe us to a colleague?" (2 min, word-of-mouth positioning)
8. "Is there anything I didn't ask that I should have?" (2 min, open-ended)

**Recording**: Always ask permission. Transcribe using AI transcription.

### Step 3: Survey (optional, for quantitative validation)
If you need numbers behind the qualitative insights:
- Keep it under 10 questions
- Use a mix of multiple choice and open-ended
- Include one Net Promoter Score (NPS) question
- Distribute via email (Resend) with a clear subject line and one CTA
- Target 30+ responses for statistical relevance

### Step 4: Synthesize into Personas
For each distinct customer segment identified, create a persona:
- **Name**: Descriptive (not a real name). E.g., "Growth-Stage Founder" not "Sarah"
- **Demographics**: Role, company size, industry
- **Trigger event**: What happened that made them look for a solution
- **Goals**: What they are trying to achieve
- **Frustrations**: What is not working today
- **Decision criteria**: How they evaluate options
- **Objections**: What almost stopped them
- **Quote**: One real quote from an interview that captures their perspective

### Step 5: Create a Voice-of-Customer (VoC) Bank
Extract specific phrases and words customers used during interviews. Organize by:
- How they describe the problem
- How they describe the desired outcome
- How they describe the product/service
- Objections in their own words

This bank feeds directly into copywriting, ad creative, and content strategy.

### Step 6: Document in Notion
Create a "Customer Research" section with:
- Research questions and methodology
- Interview summaries (anonymized)
- Personas (one page per persona)
- VoC bank
- Survey results (if applicable)

## Stack Context
- **Notion**: All research outputs live in Notion. Personas and VoC bank are referenced by content writers, marketers, and product managers.
- **Resend**: If running a survey, send distribution emails via Resend using a Next.js API route.
- **Next.js**: Survey landing page (if self-hosted) built as a simple form with Server Action for submission.
- **Supabase**: If storing survey responses, use Supabase table with appropriate RLS policies.

## Quality Gate
- [ ] At least 5 customer interviews conducted
- [ ] Both happy and unhappy customers included
- [ ] Research questions defined before interviews began
- [ ] Personas based on patterns across multiple interviews (not a single anecdote)
- [ ] VoC bank contains actual customer language, not paraphrased
- [ ] Documented in Notion with anonymized interview summaries

## Anti-Patterns
- **Leading questions** — "Don't you love our product?" is not research. Ask open-ended questions.
- **Only happy customers** — interviewing only fans gives a distorted picture. Include churned and unconverted.
- **Persona fiction** — personas based on assumptions rather than interviews are fiction. Real quotes and real patterns only.
- **Too many personas** — 2-4 personas cover most businesses. If you have 8 personas, you have not found the patterns.
- **Research without action** — research that sits in a doc and does not inform positioning, copy, or product decisions is wasted effort.

## Related Skills
- `strategy/positioning` — research feeds directly into positioning
- `strategy/reddit-insights` — complementary community-based research
- `strategy/market-research-30day` — broader market scanning
- `communications/voice-extractor` — extracting brand voice from content
- `communications/copywriting` — VoC bank feeds copywriting
