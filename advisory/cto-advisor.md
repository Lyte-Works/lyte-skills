<!-- reconstructed -->
---
name: "cto-advisor"
description: "CTO-level technical leadership — architecture decisions, team scaling, build-vs-buy, and technical strategy"
workers: ["systems-architect"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# CTO Advisor

## When to Use
- Technical architecture decisions with business impact
- Build vs. buy decisions
- Scaling the engineering team
- Technical due diligence
- Aligning technical strategy with business goals

## Workflow

### Step 1: Technical Strategy Assessment
- **Current architecture**: What is the tech stack? What works? What does not?
- **Technical debt**: What is slowing the team down?
- **Scaling bottlenecks**: What breaks first at 10x current usage?
- **Team capabilities**: What skills exist? What is missing?
- **Build vs. buy**: What should be custom-built vs. off-the-shelf?

### Step 2: Build vs. Buy Framework
| Factor | Build | Buy |
|--------|-------|-----|
| Core to your value proposition? | Yes → Build | No → Buy |
| Competitive advantage? | Yes → Build | No → Buy |
| Off-the-shelf solution exists? | No → Build | Yes → Buy |
| Maintenance burden? | High → Consider Buy | Low → Either |
| Time-to-market? | Slow → Consider Buy | N/A → Either |

### Step 3: Architecture Decision Records
For every significant technical decision, create an ADR (see `engineering/senior-architect`).

### Step 4: Team Scaling Guidance
| Team Size | Structure | CTO Focus |
|-----------|----------|-----------|
| 1-3 engineers | Flat, CTO codes | Architecture + coding |
| 4-8 engineers | Tech lead + ICs | Architecture + code review |
| 9-20 engineers | Multiple teams | Strategy + hiring + process |
| 20+ engineers | Engineering managers | Strategy + leadership + culture |

### Step 5: Technical Metrics
| Metric | Why It Matters |
|--------|---------------|
| Deployment frequency | How often can you ship? |
| Lead time for changes | How long from idea to production? |
| Change failure rate | How often do deployments cause problems? |
| Mean time to recovery | How fast can you fix production issues? |
| Developer experience | Is the team productive and happy? |

### Step 6: Technology Radar
Maintain a technology radar:
- **Adopt**: Use in production (Next.js, TypeScript, Tailwind, Vercel)
- **Trial**: Testing in non-critical projects
- **Assess**: Evaluating, not yet testing
- **Hold**: Not recommended for new projects

## Stack Context
- **Next.js / Vercel / Supabase**: Default stack. CTO advisor ensures architecture decisions align with this stack.
- **GitHub**: Engineering process (PRs, reviews, CI/CD).
- **Notion**: ADRs, technology radar, and team documentation.

## Quality Gate
- [ ] Technical strategy documented
- [ ] Build vs. buy decisions explicit
- [ ] ADRs for significant decisions
- [ ] Team scaling plan aligned with growth
- [ ] Technical metrics tracked (DORA metrics)
- [ ] Technology radar maintained

## Anti-Patterns
- **Building everything** — not everything needs to be custom-built. Use SaaS tools for non-core functions.
- **Technology for technology's sake** — new tools must solve real problems, not satisfy curiosity.
- **No documentation** — undocumented architecture decisions lead to re-litigation.
- **CTO still coding at 20+ engineers** — the job changes as the team grows.

## Related Skills
- `engineering/senior-architect` — system architecture
- `advisory/ceo-advisor` — aligning technical and business strategy
- `engineering/devops` — deployment and infrastructure
- `engineering/tech-debt-tracker` — technical debt management
