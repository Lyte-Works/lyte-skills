<!-- reconstructed -->
---
name: "contract-writer"
description: "Proposal and contract drafting — service agreements, scope of work, terms, and pricing documentation"
workers: ["sales-lead", "legal-advisor"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Contract Writer

## When to Use
- Drafting a client proposal or statement of work
- Creating service agreements
- Writing terms of service or privacy policies
- Standardizing contract templates

## Workflow

### Step 1: Proposal Structure
```
# Proposal: [Project Name]
Prepared for: [Client Name]
Date: [Date]

## Executive Summary
[2-3 sentences: what we will do, the expected outcome, and the timeline]

## Understanding
[Restate the client's problem/need in your own words to demonstrate understanding]

## Proposed Solution
[What we will deliver, broken into phases if applicable]

## Scope of Work
### Included:
- [Deliverable 1] — [description]
- [Deliverable 2] — [description]

### Explicitly Excluded:
- [Thing not included]
- [Thing not included]

## Timeline
| Phase | Duration | Deliverable |
|-------|----------|-------------|
| Phase 1 | 2 weeks | [Deliverable] |
| Phase 2 | 3 weeks | [Deliverable] |

## Investment
| Item | Price |
|------|-------|
| [Phase/deliverable] | $X,XXX |
| **Total** | **$X,XXX** |

Payment terms: [50% upfront, 50% on delivery / monthly / etc.]

## Next Steps
1. Sign this proposal
2. [Kickoff meeting]
3. [First deliverable]
```

### Step 2: Service Agreement
Key sections for a service agreement:
1. **Parties**: Who is involved
2. **Scope of services**: What will be delivered
3. **Timeline**: When it will be delivered
4. **Compensation**: How much and when
5. **Intellectual property**: Who owns what
6. **Confidentiality**: What is protected
7. **Termination**: How either party can exit
8. **Liability**: Limitations and indemnification
9. **Governing law**: Jurisdiction

### Step 3: Terms of Service (for SaaS)
Key sections:
1. Acceptance of terms
2. Description of service
3. User accounts and responsibilities
4. Pricing and payment
5. Intellectual property
6. Data privacy (link to privacy policy)
7. Acceptable use policy
8. Limitation of liability
9. Termination
10. Changes to terms
11. Governing law

### Step 4: Review Process
- Draft in Notion
- Client review and redline
- Final version signed (digitally or in writing)
- Executed copy stored in Notion

**Disclaimer**: These are templates, not legal advice. Recommend client review with their attorney for significant agreements.

## Stack Context
- **Notion**: All proposals, agreements, and templates in Notion.
- **Next.js**: Terms of service and privacy policy as static pages (`app/terms/page.tsx`, `app/privacy/page.tsx`).
- **Resend**: Send proposals and contracts via email.

## Quality Gate
- [ ] Scope clearly defined (included AND excluded)
- [ ] Timeline with milestones
- [ ] Pricing transparent with payment terms
- [ ] IP ownership explicitly stated
- [ ] Termination clause included
- [ ] Disclaimer that this is not legal advice

## Anti-Patterns
- **Vague scope** — "we'll build a website" is not a scope. Specific deliverables prevent disputes.
- **No exclusions** — what is NOT included is as important as what is included.
- **Hidden costs** — all costs should be transparent upfront.
- **No termination clause** — both parties need an exit path.
- **Copy-paste without customization** — templates must be adapted to each engagement.

## Related Skills
- `operations/sales-enablement` — proposals as part of the sales process
- `operations/sales-engineer` — technical scope for proposals
- `engineering/gdpr-compliance` — privacy policy content
- `advisory/cfo-advisor` — pricing and financial terms
