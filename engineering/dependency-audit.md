<!-- reconstructed -->
---
name: "dependency-audit"
description: "Audit npm dependencies for vulnerabilities, outdated packages, license issues, and bloat"
workers: ["code-reviewer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Dependency Audit

## When to Use
- Before a release or deployment
- Security alert from GitHub Dependabot
- Regular maintenance schedule (monthly)
- Evaluating whether to add a new dependency
- Application bundle size seems too large

## Workflow

### Step 1: Vulnerability Scan
```bash
npm audit
```
Review results by severity: critical > high > moderate > low.

For each vulnerability:
1. Is there a patch version available? → Update
2. Is it in a dev dependency only? → Lower priority but still fix
3. Is it unfixable? → Evaluate whether the dependency can be replaced

### Step 2: Outdated Check
```bash
npm outdated
```
Categorize updates:
- **Patch updates** (1.0.0 → 1.0.1): Safe to update, usually bug fixes
- **Minor updates** (1.0.0 → 1.1.0): Usually safe, new features
- **Major updates** (1.0.0 → 2.0.0): May have breaking changes, review changelog

### Step 3: Bundle Analysis
```bash
npx @next/bundle-analyzer
```
Check for:
- Dependencies that are larger than expected
- Duplicate packages (same library at multiple versions)
- Server-only dependencies leaking into client bundles

### Step 4: New Dependency Evaluation
Before adding any new dependency, assess:
| Criteria | Check |
|----------|-------|
| **Necessity** | Can we do this with what we already have? |
| **Size** | What does it add to the bundle? |
| **Maintenance** | Is it actively maintained? (last commit, open issues) |
| **Popularity** | Weekly downloads, GitHub stars (proxy for community support) |
| **License** | MIT, Apache 2.0, ISC = safe. GPL = check compatibility. |
| **Type support** | Does it have TypeScript types? |
| **Alternatives** | Are there lighter or better-maintained alternatives? |

### Step 5: Document and Act
Create a Notion page "Dependency Audit — [Date]" with:
- Vulnerabilities found and actions taken
- Outdated packages and update plan
- Bundle analysis findings
- Any dependencies recommended for removal or replacement

## Stack Context
- **npm**: Package manager. Use `npm audit` and `npm outdated` for scanning.
- **Next.js**: `@next/bundle-analyzer` for bundle analysis.
- **GitHub**: Dependabot alerts for automated vulnerability detection. Configure in `.github/dependabot.yml`.
- **Vercel**: Deployments may fail if dependencies have issues. Catch them in audit, not in deployment.

## Quality Gate
- [ ] No critical or high vulnerabilities in production dependencies
- [ ] No dependencies more than 2 major versions behind
- [ ] Bundle size within acceptable limits for the project
- [ ] All dependencies have compatible licenses
- [ ] Audit documented with date and findings

## Anti-Patterns
- **Ignoring audit results** — "npm audit found 47 vulnerabilities" should not be a permanent state.
- **Update everything at once** — update one dependency at a time, test, commit. Bulk updates make debugging hard.
- **No lockfile** — always commit `package-lock.json`. Without it, builds are not reproducible.
- **Dependency for everything** — a 2KB utility function does not need a dependency. Write it yourself.
- **Ignoring licenses** — GPL dependencies in a commercial project can create legal issues. Check licenses.

## Related Skills
- `engineering/code-review` — dependency changes in PRs
- `engineering/security-engineer` — broader security posture
- `engineering/tech-debt-tracker` — outdated dependencies as technical debt
- `engineering/cicd-pipeline` — automated audit in CI
