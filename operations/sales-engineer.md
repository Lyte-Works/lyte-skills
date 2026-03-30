<!-- reconstructed -->
---
name: "sales-engineer"
description: "Technical sales support — demo preparation, technical objection handling, and proof-of-concept design"
workers: ["sales-lead"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Sales Engineer

## When to Use
- Preparing a product demo for a prospect
- Answering technical questions during the sales process
- Building a proof-of-concept for a specific prospect
- Creating technical documentation for sales proposals

## Workflow

### Step 1: Pre-Demo Research
- What is the prospect's technical environment?
- What specific problems are they trying to solve?
- Who is in the meeting? (technical vs. business stakeholders)
- What competitors are they evaluating?
- What integrations do they need?

### Step 2: Demo Preparation
- **Custom demo environment**: Vercel preview deployment with prospect-relevant data
- **Demo script**: Ordered by prospect priority, not feature list
- **Fallback plan**: If the demo breaks, have screenshots or a recorded backup
- **Technical depth**: Match to the audience (executive summary vs. deep dive)

### Step 3: Demo Flow
1. **Confirm the problem** (2 min): "You mentioned you're struggling with X. Is that still the top priority?"
2. **Show the solution** (15 min): Walk through the product solving their specific problem
3. **Show the differentiator** (5 min): What makes this better than alternatives
4. **Technical Q&A** (10 min): Answer questions honestly
5. **Next steps** (3 min): Clear action item

### Step 4: Technical Objection Handling
| Objection | Response Strategy |
|-----------|-----------------|
| "Does it integrate with X?" | If yes: show it. If no: explain workaround or roadmap |
| "How secure is it?" | Reference security practices, compliance (SOC 2, GDPR) |
| "Can it handle our scale?" | Reference architecture, benchmarks, similar customers |
| "We built something internally" | Acknowledge, then show TCO comparison |
| "What about data migration?" | Outline migration path step by step |

### Step 5: Proof of Concept (if needed)
For high-value prospects, build a limited POC:
- Scope: solve ONE specific problem
- Timeline: 1-2 weeks max
- Success criteria: defined before building
- Built with the standard stack (Next.js, Supabase, Vercel)

### Step 6: Follow-Up
After the demo:
- Send a summary email within 24 hours
- Include answers to any questions you could not answer live
- Provide a link to the demo environment (if applicable)
- Document the technical requirements in Notion

## Stack Context
- **Vercel**: Preview deployments for custom demo environments.
- **Next.js**: Demo apps built with the standard stack.
- **Supabase**: Demo data in a separate Supabase project.
- **Notion**: Technical requirements, demo scripts, and follow-up notes.

## Quality Gate
- [ ] Pre-demo research completed
- [ ] Demo environment tested and working
- [ ] Demo scripted around prospect's problems (not a feature tour)
- [ ] Technical objections anticipated with prepared responses
- [ ] Follow-up sent within 24 hours
- [ ] Requirements documented in Notion

## Anti-Patterns
- **Feature tour** — demos that walk through every feature bore prospects. Show their problem being solved.
- **Unprepared** — a broken demo or wrong data destroys credibility.
- **Bluffing technical answers** — "I'll need to check on that" is better than a wrong answer.
- **No next steps** — a great demo with no clear next action is a missed opportunity.

## Related Skills
- `operations/sales-enablement` — sales materials and battle cards
- `communications/meeting-prep` — meeting preparation
- `strategy/competitive-teardown` — competitive intelligence for demos
- `engineering/saas-scaffolder` — POC scaffolding
