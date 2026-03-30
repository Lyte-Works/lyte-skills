<!-- reconstructed -->
---
name: "agile-product-owner"
description: "Sprint-level product ownership — backlog grooming, acceptance criteria, sprint planning, and delivery"
workers: ["product-manager"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Agile Product Owner

## When to Use
- Running sprints for a development team
- Backlog needs grooming and prioritization
- Writing acceptance criteria for engineering
- Sprint planning, review, or retrospective
- Ensuring delivered work meets the product spec

## Workflow

### Step 1: Backlog Grooming (weekly)
Review the backlog in Notion:
1. **Add new items** from product specs, bug reports, and stakeholder requests
2. **Refine items**: ensure each has a clear description, user story, and acceptance criteria
3. **Estimate**: use T-shirt sizing (S/M/L/XL) for rough effort estimation
4. **Prioritize**: rank by ICE score or strategic alignment
5. **Remove**: archive items that are no longer relevant

### Step 2: Sprint Planning
At the start of each sprint (1-2 weeks):
1. **Review sprint goal**: one sentence describing what this sprint delivers
2. **Select items**: pull from the top of the prioritized backlog
3. **Capacity check**: ensure selected items fit within team capacity (do not overcommit)
4. **Assign**: assign items to engineering workers
5. **Document**: create a sprint page in Notion with goal, selected items, and assignments

### Step 3: Acceptance Criteria
Every item entering a sprint must have acceptance criteria:

```
Given [starting condition]
When [action taken]
Then [expected result]
```

Include:
- Happy path (normal usage)
- Edge cases (empty states, maximum values, concurrent users)
- Error states (what happens when things go wrong)
- Performance expectations (if applicable)

### Step 4: Sprint Execution Support
During the sprint:
- Be available to answer questions and clarify requirements
- Make scope decisions quickly (cut scope, not quality)
- Review in-progress work on Vercel preview deployments
- Do not add items mid-sprint unless absolutely critical

### Step 5: Sprint Review
At the end of each sprint:
1. **Demo**: review completed work on the Vercel preview or production deployment
2. **Acceptance**: verify each item meets its acceptance criteria
3. **Measure**: check metrics for items that are measurable
4. **Celebrate**: acknowledge completed work
5. **Document**: update the sprint page with outcomes

### Step 6: Sprint Retrospective
After each sprint:
- What went well?
- What could be improved?
- What will we change next sprint?
Document actions and follow through on them.

## Stack Context
- **Notion**: Backlog is a Notion database with properties: title, description, user story, acceptance criteria, priority, size, status, sprint, assignee. Sprint pages are separate Notion pages linking to backlog items.
- **GitHub**: Each backlog item maps to a GitHub Issue when it enters a sprint. PRs reference the issue. Acceptance criteria in the issue help code reviewers verify completeness.
- **Vercel**: Preview deployments are used for sprint review. Each PR gets a preview URL for acceptance testing before merge.
- **Next.js**: Acceptance criteria directly inform what the engineering worker builds and what the QA engineer tests.

## Quality Gate
- [ ] Backlog groomed weekly with no items older than 1 month without review
- [ ] Every sprint has a clear one-sentence goal
- [ ] Every item in the sprint has acceptance criteria in given/when/then format
- [ ] Sprint capacity is not exceeded (no overcommitting)
- [ ] Sprint review completed with acceptance testing
- [ ] Retrospective conducted with at least one actionable improvement

## Anti-Patterns
- **No acceptance criteria** — "build the settings page" is not a spec. Given/when/then is required.
- **Mid-sprint scope changes** — protect the sprint. New requests go to the backlog for next sprint.
- **Overcommitting** — a sprint with 150% of capacity planned will deliver 60% and demoralize everyone.
- **Skipping retrospectives** — the retro is how the team improves. Skipping it means repeating the same mistakes.
- **Acceptance by absence** — if the PO does not review delivered work, quality erodes. Always do the sprint review.

## Related Skills
- `strategy/product-manager` — feature specs that feed into the backlog
- `strategy/senior-pm` — strategic roadmap that the backlog serves
- `core/scrum-master` — sprint ceremony facilitation
- `engineering/tdd` — test-driven development aligned with acceptance criteria
- `engineering/qa-engineer` — quality assurance for sprint deliverables
