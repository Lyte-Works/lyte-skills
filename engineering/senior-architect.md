<!-- reconstructed -->
---
name: "senior-architect"
description: "System architecture design — application structure, scaling decisions, integration patterns, and technical leadership"
workers: ["systems-architect"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Senior Architect

## When to Use
- Designing a new application from scratch
- Making decisions that affect the entire system
- Evaluating whether to add new technology to the stack
- Scaling an application beyond its current architecture
- Technical due diligence for a client

## Workflow

### Step 1: Requirements Analysis
Document:
- **Functional requirements**: What does the system need to do?
- **Non-functional requirements**: Performance, scalability, security, availability
- **Constraints**: Budget, timeline, team capability, existing systems
- **Assumptions**: Traffic volume, data volume, growth expectations

### Step 2: Architecture Decision Records (ADRs)
For every significant architectural decision:
```markdown
# ADR-001: Use Next.js App Router with Vercel

## Status: Accepted
## Date: 2026-03-29

## Context
We need a framework for building the client's web application.

## Decision
Use Next.js with App Router, deployed to Vercel.

## Rationale
- Server Components reduce client JS and improve performance
- Vercel deployment is zero-config with preview deployments
- TypeScript support is first-class
- Team has existing Next.js experience

## Consequences
- Vendor lock-in to Vercel for deployment (mitigatable, Next.js runs elsewhere)
- Must use App Router patterns (no Pages Router)
- Serverless function limitations (10s default timeout)

## Alternatives Considered
- Remix: Similar capabilities but smaller ecosystem
- Astro: Better for content-heavy sites but less suited for interactive apps
- Custom React + Express: More flexibility but higher maintenance burden
```

### Step 3: System Design
```
┌─────────────────────────────────────────┐
│              Vercel Edge Network          │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐ │
│  │  Static  │  │ Server  │  │   API   │ │
│  │  Assets  │  │Components│  │ Routes  │ │
│  └─────────┘  └────┬────┘  └────┬────┘ │
└──────────────────── │ ────────── │ ──────┘
                      │            │
              ┌───────▼────────────▼───────┐
              │        Supabase            │
              │  ┌──────┐  ┌───────────┐  │
              │  │Postgres│  │   Auth    │  │
              │  └──────┘  └───────────┘  │
              └───────────────────────────┘
                      │
              ┌───────▼───────┐
              │   External     │
              │   Services     │
              │ Resend, Stripe │
              └───────────────┘
```

### Step 4: Scaling Decisions
| Challenge | Default Approach | When to Escalate |
|-----------|-----------------|-----------------|
| Traffic spikes | Vercel auto-scales | Sustained >1M requests/day |
| Database performance | Supabase connection pooling | >10K concurrent connections |
| File storage | Supabase Storage | >100GB or CDN needed |
| Background jobs | Vercel Cron + API routes | Long-running (>60s) jobs |
| Real-time features | Supabase Realtime | >10K concurrent connections |

### Step 5: Integration Patterns
```typescript
// Pattern: Service layer abstraction
// lib/services/email.ts
export async function sendEmail(params: EmailParams) {
  // Abstract over Resend — if we ever switch providers, change here only
  return resend.emails.send(params);
}

// lib/services/payment.ts
export async function createCheckout(params: CheckoutParams) {
  // Abstract over Stripe
  return stripe.checkout.sessions.create(params);
}
```

### Step 6: Technology Evaluation Criteria
When asked to add a new technology:
1. **Does it solve a real problem?** (not "it would be cool to use")
2. **Can our stack already do this?** (avoid redundancy)
3. **What is the maintenance cost?** (another dependency, another service to monitor)
4. **Is it mature and supported?** (avoid bleeding-edge in production)
5. **Can we remove it later?** (avoid deep coupling)

## Stack Context
- **Next.js App Router**: Server-first architecture. Server Components for reads, Server Actions for mutations.
- **Vercel**: Serverless deployment with auto-scaling. Edge network for global performance.
- **Supabase**: Managed Postgres with auth, storage, and realtime. Reduces infrastructure management.
- **GitHub**: Source code and CI/CD. One repo per client project.

## Quality Gate
- [ ] Requirements documented (functional, non-functional, constraints)
- [ ] ADRs written for significant decisions
- [ ] System diagram created
- [ ] Scaling strategy defined for known growth scenarios
- [ ] Integration points abstracted behind service layers
- [ ] No unnecessary technology added

## Anti-Patterns
- **Resume-driven architecture** — choosing technology because it looks good on a resume, not because it solves the problem.
- **Over-engineering** — building for 10M users when you have 100. Design for current needs with a plan for growth.
- **No ADRs** — decisions made without documentation are decisions that will be re-litigated.
- **Tight coupling** — direct calls to external services scattered throughout the codebase. Wrap in service layers.
- **Ignoring constraints** — an architecture that requires a dedicated DevOps team when the client has 2 developers is not fit for purpose.

## Related Skills
- `engineering/saas-scaffolder` — bootstrapping a SaaS application
- `engineering/database-designer` — database architecture
- `engineering/devops` — infrastructure and deployment
- `advisory/cto-advisor` — technical leadership advisory
