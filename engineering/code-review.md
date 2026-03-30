<!-- reconstructed -->
---
name: "code-review"
description: "Structured code review — quality checklists, review workflow, and feedback patterns"
workers: ["code-reviewer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Code Review

## When to Use
- Reviewing code before merge (PR review)
- Auditing existing codebase for quality issues
- Establishing code review standards for a team
- Onboarding a new developer to the codebase

## Workflow

### Step 1: Review Checklist
For every code review, check these categories:

**Correctness**
- [ ] Does the code do what the spec/ticket says?
- [ ] Are edge cases handled?
- [ ] Are error states handled gracefully?

**Architecture**
- [ ] Server Components used by default? `"use client"` only where needed?
- [ ] Business logic separated from UI components?
- [ ] No duplicated logic — shared utilities used?
- [ ] Files are in the right directories (following project conventions)?

**TypeScript**
- [ ] No `any` types
- [ ] Props and return types defined
- [ ] Zod or equivalent for runtime validation of external data

**Styling**
- [ ] Tailwind only — no CSS modules, inline styles, or styled-components
- [ ] Responsive design (mobile-first)
- [ ] Consistent spacing and typography

**Performance**
- [ ] No unnecessary client-side JS (Server Components where possible)
- [ ] Images use `next/image`
- [ ] No N+1 queries or unnecessary data fetching
- [ ] Dynamic imports for heavy client components

**Security**
- [ ] No secrets in client-side code
- [ ] Input validation on all endpoints
- [ ] RLS policies on database tables
- [ ] No SQL injection vectors

**Testing**
- [ ] Critical paths have tests
- [ ] Tests are meaningful (not just checking that code runs)

### Step 2: Review Process
1. Read the PR description and linked ticket first
2. Skim all changed files for high-level understanding
3. Review each file in detail using the checklist
4. Write feedback — be specific, reference line numbers
5. Approve, request changes, or comment

### Step 3: Feedback Patterns
**Good feedback:**
- "This Server Action is missing input validation. Consider adding a Zod schema. See `/app/actions/contact.ts` for an example." (Specific, actionable, references existing patterns)

**Bad feedback:**
- "This doesn't look right." (Vague, not actionable)
- "I would have done this differently." (Not a review, it's a preference)

**Categories:**
- **Must fix**: Security issues, bugs, missing error handling
- **Should fix**: Code quality, naming, architecture
- **Suggestion**: Style preferences, minor improvements
- **Question**: Asking for clarification, understanding the approach

### Step 4: Self-Review Checklist
Before submitting a PR for review, the author should:
- [ ] Run the code locally and test manually
- [ ] Run existing tests
- [ ] Review your own diff as if reviewing someone else's code
- [ ] Write a clear PR description

## Stack Context
- **GitHub**: Reviews happen on GitHub PRs. Use GitHub's review feature (approve, request changes, comment).
- **Vercel**: Review the preview deployment — does the feature work in the deployed environment?
- **Next.js**: Enforce App Router patterns, Server Component defaults, and Tailwind-only styling.
- **TypeScript**: Strict mode compliance. No `any`. All types explicit.

## Quality Gate
- [ ] Checklist applied to every review (not freestyle opinions)
- [ ] Feedback is specific and actionable
- [ ] Feedback categorized (must fix / should fix / suggestion)
- [ ] Preview deployment tested
- [ ] No unresolved "must fix" items at merge time

## Anti-Patterns
- **Rubber stamping** — approving without reading. If you approve, you share responsibility.
- **Style policing** — if it is not in the linter or formatter config, it is not a review comment. Do not argue about semicolons.
- **Blocking on preferences** — "I would have done it differently" is not a reason to block a PR.
- **No context** — reviewing code without reading the ticket or PR description leads to irrelevant feedback.
- **Delayed reviews** — PRs that sit unreviewed for days slow the entire team. Review within 24 hours.

## Related Skills
- `engineering/pr-review` — GitHub PR-specific workflow
- `engineering/tdd` — tests as part of the review
- `engineering/security-engineer` — security review focus
- `engineering/dependency-audit` — reviewing dependencies
