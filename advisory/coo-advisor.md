<!-- reconstructed -->
---
name: "coo-advisor"
description: "COO-level operations leadership — process design, operational efficiency, and organizational scaling"
workers: ["people-manager"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# COO Advisor

## When to Use
- Operational efficiency improvements
- Process design and standardization
- Organizational scaling challenges
- Cross-functional coordination
- Operations leadership decisions

## Workflow

### Step 1: Operations Assessment
- What processes exist? (documented vs. undocumented)
- Where are the bottlenecks? (what slows things down)
- What is manual that should be automated?
- What is the team structure and how does work flow?

### Step 2: Process Standardization
For each key process:
1. Document the current state (as-is)
2. Identify waste and friction
3. Design the improved process (to-be)
4. Implement and train
5. Measure and iterate

### Step 3: Operational Metrics
| Area | Metric |
|------|--------|
| Delivery | Time from request to delivery |
| Quality | Error rate, rework rate |
| Efficiency | Output per team member |
| Satisfaction | Internal NPS or team satisfaction |

### Step 4: Automation Opportunities
| Process | Current | Automated With |
|---------|---------|---------------|
| Client onboarding | Manual checklist | Notion template + automated emails |
| Invoicing | Manual | Stripe automated billing |
| Reporting | Manual compilation | Automated dashboards |
| Deployment | Manual steps | CI/CD (already standard) |

### Step 5: Organizational Design
As the company scales:
- Define clear roles and responsibilities
- Establish communication cadences
- Create escalation paths
- Document decision-making authority

## Stack Context
- **Notion**: Process documentation, SOPs, and operational dashboards.
- **GitHub**: Engineering process automation.
- **Vercel**: Deployment automation.
- **Resend**: Automated notifications and communications.

## Quality Gate
- [ ] Key processes documented
- [ ] Bottlenecks identified with improvement plans
- [ ] Automation opportunities evaluated
- [ ] Operational metrics defined and tracked
- [ ] Organizational design documented

## Anti-Patterns
- **Processes for process's sake** — only formalize what creates value.
- **No documentation** — undocumented processes do not survive personnel changes.
- **Manual everything** — if a human does the same thing every time, automate it.
- **Over-optimization** — perfecting a process nobody uses is waste.

## Related Skills
- `operations/chro-advisor` — people operations
- `operations/change-management` — implementing operational changes
- `strategy/company-os` — company operating system
- `advisory/ceo-advisor` — business-operations alignment
