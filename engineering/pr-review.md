<!-- reconstructed -->
---
name: "pr-review"
description: "GitHub Pull Request review workflow — PR structure, review automation, and merge criteria"
workers: ["code-reviewer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# PR Review

## When to Use
- Reviewing GitHub Pull Requests
- Establishing PR standards for a project
- Automating PR checks and reviews
- Ensuring PRs are ready for merge

## Workflow

### Step 1: PR Structure Standard
Every PR should include:
- **Title**: Brief, descriptive (e.g., "Add contact form with Resend integration")
- **Description**: What changed and why
- **Linked issue**: Reference the GitHub Issue or Notion ticket
- **Screenshots**: For UI changes, before/after screenshots
- **Testing**: How was this tested?
- **Deployment notes**: Any environment variables, migrations, or config needed

### Step 2: Automated Checks
Configure GitHub Actions to run automatically on every PR:
```yaml
# .github/workflows/pr-check.yml
name: PR Checks
on: pull_request
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 20 }
      - run: npm ci
      - run: npm run lint
      - run: npm run type-check

  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 20 }
      - run: npm ci
      - run: npm test
```

### Step 3: Review Workflow
1. **Automated checks pass** — lint, type-check, tests green
2. **Preview deployment** — verify the feature works on the Vercel preview URL
3. **Code review** — apply the code review checklist
4. **Approval** — at least one approval required
5. **Merge** — squash and merge to main (triggers production deploy)

### Step 4: Review Priorities
Focus review time on:
1. **Security**: Secrets exposed? Input validation missing? Auth bypassed?
2. **Correctness**: Does it work? Edge cases handled?
3. **Architecture**: Right patterns used? Future maintainability?
4. **Performance**: Unnecessary client JS? N+1 queries?
5. **Style**: Last priority — if the linter passes, style is fine.

### Step 5: Merge Criteria
A PR is ready to merge when:
- [ ] All automated checks pass
- [ ] Preview deployment works correctly
- [ ] At least one review approval
- [ ] No unresolved "must fix" comments
- [ ] PR description is complete

## Stack Context
- **GitHub**: PRs, reviews, and checks all on GitHub. Use branch protection rules on `main`.
- **Vercel**: Every PR gets a preview deployment automatically. Use the preview URL for testing.
- **GitHub Actions**: Automated linting, type-checking, and testing on every PR.
- **Next.js**: Vercel preview builds the app exactly as it would deploy to production.

## Quality Gate
- [ ] PR template established in the repo (`.github/pull_request_template.md`)
- [ ] Automated checks configured (lint, type-check, test)
- [ ] Branch protection enabled on main
- [ ] Reviews required before merge
- [ ] Preview deployment reviewed for UI/UX changes

## Anti-Patterns
- **Merging without review** — even solo developers benefit from self-review. Never merge directly to main.
- **Mega PRs** — PRs with 50+ files are unreviewable. Keep PRs small and focused.
- **Ignoring preview deploys** — the preview exists for a reason. Click through the feature.
- **No automated checks** — manual linting and type-checking is unreliable. Automate it.
- **"LGTM" reviews** — an approval without reading the code is worse than no review.

## Related Skills
- `engineering/code-review` — detailed review checklist
- `engineering/tdd` — tests that should pass in CI
- `engineering/cicd-pipeline` — the pipeline that runs checks
- `engineering/devops` — deployment configuration
