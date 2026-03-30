<!-- reconstructed -->
---
name: "ux-researcher"
description: "User research methods — usability testing, user interviews, card sorting, and research synthesis"
workers: ["product-manager", "ux-designer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# UX Researcher

## When to Use
- Before designing a new feature or product
- Existing feature has poor usability or adoption
- Redesigning a flow (onboarding, checkout, signup)
- Validating design decisions with real users
- Client says "users don't get it" or "nobody uses this feature"

## Workflow

### Step 1: Define Research Objective
Answer one question:
> What do we need to learn, and how will it change what we build?

If the answer does not change a decision, the research is not necessary.

### Step 2: Choose Research Method

| Method | Best For | Effort | When |
|--------|---------|--------|------|
| **Usability test** | Evaluating existing UI | Medium | Feature exists, need to validate |
| **User interview** | Understanding needs and behaviors | Medium | Before designing |
| **Card sorting** | Information architecture | Low | Before building navigation |
| **Tree testing** | Validating IA structure | Low | After card sorting |
| **A/B test** | Comparing two approaches | Medium | Both options exist |
| **Survey** | Quantitative validation | Low | Need numbers, not depth |
| **Heuristic review** | Quick UX audit | Low | No access to users |

### Step 3: Recruit Participants
- **Usability tests**: 5 participants find ~85% of usability issues
- **Interviews**: 5-8 participants for pattern identification
- **Surveys**: 30+ responses for statistical relevance

Recruit from:
- Existing customers (ask the client)
- Target audience communities
- Social media outreach

### Step 4: Conduct Research

**Usability Test Script:**
1. Introduction (2 min): Explain the purpose, get consent, reassure there are no wrong answers
2. Warm-up (3 min): Ask about their background and current tools
3. Tasks (20 min): Give 3-5 tasks to complete. Observe silently. Ask them to think aloud.
4. Debrief (5 min): Ask about overall impressions, what was easy, what was confusing

**Key rules:**
- Do not lead the participant ("Did you find the button easy to use?")
- Ask open questions ("Tell me what you're thinking right now")
- Note where they hesitate, click wrong, or express frustration
- Record the session (with permission)

### Step 5: Synthesize Findings
For each research session, extract:
- **Observation**: What happened (factual)
- **Insight**: Why it happened (interpretation)
- **Recommendation**: What to change (actionable)

Group insights into themes. Prioritize by:
- Severity (prevents task completion > slows task > annoyance)
- Frequency (found by 4/5 users > found by 1/5)

### Step 6: Document and Present
Create a research report in Notion:
- Research objective and method
- Participant profiles (anonymized)
- Key findings with severity ratings
- Recommendations prioritized by impact
- Video clips or quotes that illustrate findings

## Stack Context
- **Notion**: Research reports, participant databases, and finding databases live in Notion. Use a Notion database for tracking findings across studies.
- **Next.js / Vercel**: Preview deployments are ideal for usability testing. Share a Vercel preview URL with participants. No setup required on their end.
- **Vercel Analytics**: Complement qualitative usability testing with quantitative data — where do users actually click, how long do they spend on pages.
- **Supabase**: If building a research participant database, store participant info (with consent) in Supabase.

## Quality Gate
- [ ] Research objective is specific and decision-relevant
- [ ] Appropriate method selected for the question being asked
- [ ] At least 5 participants for usability tests or interviews
- [ ] Findings are categorized by severity and frequency
- [ ] Recommendations are specific and actionable
- [ ] Report documented in Notion with evidence

## Anti-Patterns
- **Research for research's sake** — if findings will not change a decision, do not conduct the study
- **Leading questions** — "Was that easy?" is not a research question. "Tell me about that experience" is.
- **Sample size of 1** — one user's feedback is an anecdote, not a finding. Look for patterns.
- **Reporting without recommendations** — findings without actionable next steps are academic exercises
- **Design validation only** — the best research happens before design, not after. Do not use research only to confirm decisions already made.

## Related Skills
- `strategy/ux-designer` — design work informed by research
- `strategy/customer-research` — broader customer research beyond UX
- `strategy/product-analytics` — quantitative complement to qualitative research
- `communications/signup-flow-cro` — optimizing flows based on research findings
- `communications/onboarding-cro` — onboarding improvements from usability tests
