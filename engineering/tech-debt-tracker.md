<!-- reconstructed -->
---
name: "tech-debt-tracker"
description: "Identify, prioritize, and plan technical debt reduction — code quality, architecture, and maintenance"
workers: ["code-reviewer", "systems-architect"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Tech Debt Tracker

## When to Use
- Codebase is slowing down development velocity
- Frequent bugs in the same areas of code
- Onboarding new developers takes too long
- Before a major feature that will touch legacy code
- Regular quarterly health check

## Workflow

### Step 1: Identify Debt
Scan the codebase for common debt patterns:

| Pattern | Signal | Severity |
|---------|--------|----------|
| TODO/FIXME comments | `grep -r "TODO\|FIXME\|HACK"` | Medium |
| `any` types in TypeScript | Type safety holes | Medium |
| Large files (500+ lines) | Components that do too much | Low-Medium |
| Duplicated code | Same logic in multiple places | Medium |
| Outdated dependencies | `npm outdated` | Medium-High |
| Missing tests for critical paths | No safety net for changes | High |
| Inconsistent patterns | Mix of Pages Router and App Router patterns | High |
| Hardcoded values | Magic numbers, inline URLs, non-env config | Low |
| No error handling | Try/catch missing on async operations | High |
| CSS modules alongside Tailwind | Mixed styling approaches | Low |

### Step 2: Catalog Debt
Create a Notion database "Tech Debt Register" with columns:
- **Item**: Description of the debt
- **Location**: File paths or component names
- **Type**: Code quality / Architecture / Dependencies / Testing / Security
- **Severity**: Critical / High / Medium / Low
- **Effort**: S / M / L / XL
- **Impact**: What problems does this debt cause?
- **Proposed fix**: How to resolve it
- **Status**: Open / In Progress / Resolved

### Step 3: Prioritize
Use this formula:
> Priority = Severity x (1 / Effort)

High-severity, low-effort items go first. These are quick wins.

Categories:
1. **Fix now**: Critical severity, any effort
2. **Fix this sprint**: High severity, small effort
3. **Plan for next sprint**: High severity, large effort
4. **Backlog**: Medium/low severity, any effort

### Step 4: Allocate Capacity
Reserve 15-20% of each sprint for tech debt reduction. Do not let debt pile up waiting for a "tech debt sprint" that never comes.

### Step 5: Track Progress
Update the debt register after each sprint:
- Items resolved
- New items discovered
- Trend: is debt increasing or decreasing?

Report to stakeholders monthly: "We resolved X items, discovered Y new items. Debt trend: [improving/stable/worsening]."

## Stack Context
- **Notion**: Tech debt register lives in Notion as a database.
- **GitHub**: Debt items can be linked to GitHub Issues for sprint planning.
- **Next.js**: Common debt patterns include mixed Router patterns, missing metadata, `any` types.
- **Tailwind**: Debt includes mixed styling approaches (CSS modules + Tailwind).
- **TypeScript**: `any` types and missing type definitions are trackable debt.

## Quality Gate
- [ ] Tech debt register exists and is maintained
- [ ] All items have severity, effort, and proposed fix
- [ ] Critical items have a resolution timeline
- [ ] 15-20% sprint capacity allocated to debt reduction
- [ ] Monthly trend reported to stakeholders
- [ ] No new critical debt accepted without a resolution plan

## Anti-Patterns
- **Ignoring debt** — technical debt compounds. Small issues become large ones.
- **"Tech debt sprint"** — a dedicated sprint for debt rarely happens. Allocate 15-20% every sprint instead.
- **Cataloging without fixing** — a beautiful debt register with zero resolution is documentation theater.
- **Debt without context** — "refactor this" is not a debt item. Include the impact and proposed fix.
- **Treating all debt equally** — a missing test on the checkout flow is more important than a TODO comment in a utility function.

## Related Skills
- `engineering/code-review` — catching debt during reviews
- `engineering/dependency-audit` — dependency-related debt
- `engineering/security-audit` — security debt
- `engineering/performance-profiler` — performance debt
