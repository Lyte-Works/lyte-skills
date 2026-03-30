<!-- reconstructed -->
---
name: "senior-pm"
description: "Strategic product management — roadmaps, stakeholder alignment, product vision, and cross-team coordination"
workers: ["product-manager"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Senior PM

## When to Use
- Building a multi-quarter product roadmap
- Aligning stakeholders (founder, engineering, marketing) on product direction
- Making trade-off decisions between competing priorities
- Product vision needs articulation or refresh
- Cross-functional coordination for a major initiative

## Workflow

### Step 1: Product Vision
Write a product vision statement:
> In [time horizon], [product] will be the [category] that [key differentiator] for [target customer], enabling them to [desired outcome].

### Step 2: Strategic Pillars
Define 3-4 strategic pillars that support the vision. Each pillar is a theme of work, not a feature.
- Example: "Self-serve onboarding," "Enterprise readiness," "Platform extensibility"
- Each pillar should have a measurable goal

### Step 3: Roadmap Construction
Build a roadmap at the quarter level:

| Quarter | Pillar | Initiative | Key Outcome |
|---------|--------|-----------|-------------|
| Q1 | Self-serve | Onboarding wizard | 50% reduction in support tickets |
| Q1 | Enterprise | Role-based access | Unlock enterprise sales |
| Q2 | Platform | API v2 | 3 partner integrations |

**Rules:**
- Each quarter has 2-3 initiatives max
- Each initiative ties to a pillar
- Each initiative has a measurable outcome
- Leave 20% capacity unplanned for urgent work

### Step 4: Stakeholder Alignment
For each stakeholder group, prepare:
- **Engineering**: technical feasibility review, effort estimates, dependency mapping
- **Marketing**: launch timing, messaging needs, content coordination
- **Sales**: impact on pipeline, new capabilities to sell, timeline expectations
- **Leadership**: strategic rationale, resource requirements, expected business impact

### Step 5: Decision Framework
When competing priorities arise, use this framework:
1. Does it serve the product vision?
2. Which strategic pillar does it support?
3. What is the business impact (revenue, retention, acquisition)?
4. What is the cost of delay?
5. Does the team have the capacity?

Document every significant decision in the decision log.

### Step 6: Quarterly Review
At the end of each quarter:
- Score each initiative against its key outcome
- Update the roadmap for the next quarter
- Review and adjust strategic pillars if market conditions changed
- Share the update in Notion and present to stakeholders

## Stack Context
- **Notion**: Roadmap is a Notion database with views for timeline, by-pillar, and by-quarter. Stakeholder updates are Notion pages shared with appropriate access.
- **GitHub**: Major initiatives map to GitHub Milestones. Individual features within initiatives map to GitHub Issues.
- **Vercel**: Preview deployments enable stakeholder review of in-progress work.

## Quality Gate
- [ ] Product vision is documented and shared with all stakeholders
- [ ] 3-4 strategic pillars defined with measurable goals
- [ ] Roadmap covers at least 2 quarters with 2-3 initiatives each
- [ ] Each initiative has a measurable key outcome
- [ ] 20% capacity buffer maintained
- [ ] Quarterly review process established

## Anti-Patterns
- **Feature roadmaps** — a roadmap of features is a to-do list, not a strategy. Lead with outcomes and pillars, not features.
- **Overcommitting** — a roadmap with 10 initiatives per quarter is fiction. Be realistic about capacity.
- **No buffer** — 100% utilization means zero flexibility for urgent work. Always leave 20%.
- **Stakeholder avoidance** — misaligned stakeholders do not go away. Address disagreements early.
- **Static roadmap** — a roadmap that never changes is a plan made with outdated information. Review quarterly.

## Related Skills
- `strategy/product-manager` — tactical PM execution within the strategic framework
- `strategy/agile-product-owner` — sprint-level execution
- `strategy/company-os` — strategic pillars should align with company mission and values
- `advisory/cpo-advisor` — product leadership advisory
- `core/decision-logger` — logging strategic decisions
