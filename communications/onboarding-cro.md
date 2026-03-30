<!-- reconstructed -->
---
name: "onboarding-cro"
description: "User onboarding optimization — activation metrics, guided flows, and time-to-value reduction"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Onboarding CRO

## When to Use
- Users sign up but do not activate (complete first valuable action)
- Onboarding flow has high drop-off
- Reducing time-to-value for new users
- Improving free-to-paid conversion

## Workflow

### Step 1: Define the "Aha Moment"
What is the first action that correlates with retention?
- For a project tool: creating their first project
- For analytics: installing the tracking code
- For a SaaS: completing their first workflow

### Step 2: Map the Current Onboarding
```
Signup → [Step 1] → [Step 2] → [Step 3] → Aha Moment
```
Measure drop-off at each step.

### Step 3: Reduce Steps to Aha Moment
Every step between signup and the aha moment is a potential drop-off. Ruthlessly cut:
- Can this step be skipped? → Skip it
- Can this step be deferred? → Move to after activation
- Can this step be automated? → Do it for them
- Can this step be simplified? → Reduce to one click

### Step 4: Onboarding Patterns
| Pattern | Best For | Example |
|---------|---------|---------|
| **Checklist** | 3-5 setup steps | "Complete your profile: 3/5 done" |
| **Guided tour** | Complex UI | Tooltip walkthrough of key features |
| **Template/preset** | Content creation tools | "Start with a template" |
| **Empty state with CTA** | Data-dependent tools | "No projects yet — create your first" |
| **Progressive disclosure** | Feature-rich products | Show basics first, reveal advanced later |

### Step 5: Onboarding Emails
Complement in-app onboarding with email (Resend):
- Day 0: Welcome + quickstart guide
- Day 1: "Have you tried [key feature]?"
- Day 3: Tip or use case example
- Day 7: "Need help?" (if not activated)

### Step 6: Measure
| Metric | Definition | Target |
|--------|-----------|--------|
| Activation rate | % who complete aha moment | >60% |
| Time to value | Time from signup to aha moment | <5 minutes |
| Onboarding completion | % who finish all steps | >80% |
| Day 7 retention | % who return after 1 week | >40% |

## Stack Context
- **Next.js**: Onboarding pages as protected routes. Checklist or wizard as Client Components.
- **Supabase**: Track onboarding progress per user. Store completion state.
- **Resend**: Onboarding email sequence.
- **Vercel Analytics**: Custom events for each onboarding step.
- **Tailwind**: Progress indicators, empty states, tooltips.

## Quality Gate
- [ ] Aha moment defined and measurable
- [ ] Onboarding flow mapped with drop-off at each step
- [ ] Steps minimized (ruthlessly cut unnecessary ones)
- [ ] In-app and email onboarding coordinated
- [ ] Activation rate tracked
- [ ] Time to value measured and improving

## Anti-Patterns
- **Feature tour** — showing every feature before the user has done anything. Get them to the aha moment first.
- **No empty states** — blank screens with no guidance are confusing. Every empty state needs a CTA.
- **Mandatory setup** — requiring profile completion before using the product kills activation.
- **No follow-up** — users who do not activate need a nudge. Onboarding emails are essential.

## Related Skills
- `communications/signup-flow-cro` — pre-onboarding optimization
- `communications/email-sequences` — onboarding email flow
- `communications/churn-prevention` — retention after onboarding
- `strategy/product-analytics` — measuring activation
