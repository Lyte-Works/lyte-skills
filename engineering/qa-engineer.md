<!-- reconstructed -->
---
name: "qa-engineer"
description: "Quality assurance strategy — test planning, test case design, bug tracking, and release quality gates"
workers: ["systems-architect", "qa-engineer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# QA Engineer

## When to Use
- Defining a testing strategy for a project
- Writing test cases for a feature
- Bug tracking and triage
- Pre-release quality verification
- Improving overall code quality processes

## Workflow

### Step 1: Test Strategy
Define the testing pyramid:
```
         /  E2E  \          ← Few, slow, expensive (Playwright)
        / Integration \      ← Some, medium speed (Vitest)
       /   Unit Tests   \    ← Many, fast, cheap (Vitest)
```

| Layer | Tool | What to Test | Count |
|-------|------|-------------|-------|
| Unit | Vitest | Pure functions, utilities, business logic | Many |
| Component | Vitest + RTL | UI components, user interactions | Moderate |
| Integration | Vitest | Server Actions, API routes with mocked deps | Moderate |
| E2E | Playwright | Critical user flows end-to-end | Few |

### Step 2: Test Case Design
For each feature, write test cases covering:

**Positive tests** (happy path):
- Standard usage with valid inputs
- All expected variations

**Negative tests** (error handling):
- Invalid inputs (empty, too long, wrong type)
- Unauthorized access
- Network failures

**Edge cases**:
- Empty states (no data)
- Boundary values (min, max)
- Concurrent operations
- Unicode and special characters

### Step 3: Test Case Template
```
Test Case ID: TC-[feature]-[number]
Title: [Descriptive title]
Preconditions: [Setup required]
Steps:
  1. [Action]
  2. [Action]
Expected Result: [What should happen]
Priority: Critical / High / Medium / Low
```

### Step 4: Bug Tracking
Bug report template (GitHub Issue):
```markdown
## Bug Report

**Environment**: Production / Preview / Local
**Browser**: Chrome 120 / Safari 17 / Firefox 121
**URL**: [page where bug occurs]

**Steps to Reproduce**:
1. [Step]
2. [Step]

**Expected**: [What should happen]
**Actual**: [What actually happens]

**Screenshots/Video**: [attach]
**Console errors**: [if any]

**Severity**: Critical / High / Medium / Low
```

### Step 5: Release Quality Gate
Before any release:
- [ ] All unit tests pass
- [ ] All integration tests pass
- [ ] E2E tests pass for critical flows
- [ ] No open Critical or High bugs
- [ ] Manual smoke test completed on preview deployment
- [ ] Performance meets budget (Core Web Vitals green)
- [ ] Security checklist completed

### Step 6: Smoke Test Checklist
Manual verification on preview deployment:
- [ ] Homepage loads correctly
- [ ] Navigation works on all pages
- [ ] Forms submit successfully
- [ ] Mobile layout is correct
- [ ] Images load and are optimized
- [ ] External links work
- [ ] Contact/signup flows complete end-to-end

## Stack Context
- **Vitest**: Unit and integration tests.
- **React Testing Library**: Component tests.
- **Playwright**: E2E tests.
- **GitHub Issues**: Bug tracking.
- **Vercel**: Preview deployments for testing before production.
- **Notion**: Test plans and QA documentation.

## Quality Gate
- [ ] Test strategy defined (pyramid approach)
- [ ] Test cases written for all critical features
- [ ] Bug tracking process established
- [ ] Release quality gate defined and enforced
- [ ] Smoke test checklist available for manual verification

## Anti-Patterns
- **Testing everything E2E** — E2E tests are slow and fragile. Use the pyramid.
- **No test plan** — ad-hoc testing misses edge cases. Plan tests before writing them.
- **Bug reports without reproduction steps** — "it doesn't work" is not a bug report.
- **Quality gate bypassed for deadlines** — shipping known bugs creates more work later.
- **Only automated tests** — some things need human eyes. Manual smoke tests catch what automation misses.

## Related Skills
- `engineering/tdd` — test-driven development
- `engineering/playwright-e2e` — E2E test implementation
- `engineering/code-review` — code quality during review
- `engineering/release-manager` — release process quality
