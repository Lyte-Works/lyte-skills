<!-- reconstructed -->
---
name: "cicd-pipeline"
description: "CI/CD pipeline architecture with GitHub Actions — automated testing, building, and deployment to Vercel"
workers: ["devops-engineer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# CI/CD Pipeline

## When to Use
- Setting up automated testing and deployment for a new project
- Adding new checks to an existing pipeline
- Troubleshooting failed deployments
- Optimizing build times

## Workflow

### Step 1: Pipeline Architecture
```
Push/PR → Lint → Type Check → Unit Tests → Build → E2E Tests → Deploy
```

### Step 2: Core Pipeline
```yaml
# .github/workflows/ci.yml
name: CI/CD Pipeline
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  lint-and-typecheck:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: 'npm'
      - run: npm ci
      - run: npm run lint
      - run: npx tsc --noEmit

  test:
    runs-on: ubuntu-latest
    needs: lint-and-typecheck
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: 'npm'
      - run: npm ci
      - run: npm test -- --coverage
      - uses: actions/upload-artifact@v4
        with:
          name: coverage
          path: coverage/

  e2e:
    runs-on: ubuntu-latest
    needs: test
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: 'npm'
      - run: npm ci
      - run: npx playwright install --with-deps
      - run: npx playwright test
      - uses: actions/upload-artifact@v4
        if: always()
        with:
          name: playwright-report
          path: playwright-report/
```

### Step 3: Branch Protection
Configure on GitHub:
- Require PR reviews before merge
- Require status checks to pass (lint, typecheck, test)
- Require branches to be up to date
- Do not allow bypassing settings

### Step 4: Vercel Integration
Vercel auto-deploys are triggered by GitHub:
- Push to `main` → production deployment
- Push to any branch → preview deployment
- PR open → preview URL added as PR comment

No additional CI config needed for deployment — Vercel handles it.

### Step 5: Pipeline Optimization
- **Caching**: Use `actions/setup-node` with `cache: 'npm'` to cache node_modules
- **Parallelization**: Run lint and typecheck in parallel with tests
- **Skip unnecessary work**: Use path filters to skip CI for docs-only changes
- **Artifacts**: Upload test reports and coverage as artifacts

```yaml
# Path filter example
on:
  push:
    paths-ignore:
      - '**.md'
      - 'docs/**'
```

## Stack Context
- **GitHub Actions**: CI/CD platform. Free for public repos, generous free tier for private.
- **Vercel**: Deployment triggered by GitHub pushes. No additional deployment step needed in CI.
- **Next.js**: `npm run build` verifies the application compiles correctly.
- **Playwright**: E2E tests run in CI with browser installation.

## Quality Gate
- [ ] Pipeline runs on every PR
- [ ] Lint, type-check, and tests must pass before merge
- [ ] Branch protection configured on main
- [ ] Pipeline completes in under 5 minutes (for most projects)
- [ ] Artifacts preserved for test reports
- [ ] Caching enabled for node_modules

## Anti-Patterns
- **No CI** — deploying without automated checks is gambling.
- **Slow pipelines** — a 30-minute pipeline discourages frequent PRs. Optimize.
- **Flaky tests** — intermittently failing tests erode trust in the pipeline. Fix flakes immediately.
- **Skipping CI** — `[skip ci]` in commit messages should be rare. If you are skipping CI often, the pipeline is too slow.
- **No branch protection** — anyone can push directly to main without review or checks.

## Related Skills
- `engineering/devops` — broader deployment and infrastructure
- `engineering/tdd` — tests that run in the pipeline
- `engineering/playwright-e2e` — E2E test configuration
- `engineering/pr-review` — PR workflow that the pipeline supports
