<!-- reconstructed -->
---
name: "release-manager"
description: "Release process management — versioning, changelogs, release notes, and deployment coordination"
workers: ["devops-engineer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Release Manager

## When to Use
- Shipping a new version of a product or feature
- Coordinating a multi-feature release
- Generating changelogs and release notes
- Managing versioning strategy

## Workflow

### Step 1: Versioning Strategy
Use Semantic Versioning (SemVer): `MAJOR.MINOR.PATCH`
- **MAJOR**: Breaking changes
- **MINOR**: New features, backward compatible
- **PATCH**: Bug fixes, backward compatible

For most client projects: track version in `package.json`.

### Step 2: Release Checklist
Before releasing:
- [ ] All PRs for this release are merged to main
- [ ] CI pipeline is green
- [ ] Preview deployment tested and approved
- [ ] Changelog updated
- [ ] Version bumped in package.json
- [ ] Release notes drafted
- [ ] Stakeholders notified

### Step 3: Changelog Format
```markdown
# Changelog

## [1.2.0] - 2026-03-29
### Added
- Contact form with email notifications via Resend
- Blog section with dynamic routing

### Changed
- Improved mobile navigation responsiveness
- Updated pricing page layout

### Fixed
- Form validation error on empty submission
- Image optimization for hero section
```

### Step 4: GitHub Release
Create a GitHub Release:
```bash
# Tag the release
git tag -a v1.2.0 -m "Release 1.2.0"
git push origin v1.2.0

# Create release via gh CLI
gh release create v1.2.0 --title "v1.2.0" --notes-file RELEASE_NOTES.md
```

### Step 5: Post-Release
- Verify production deployment on Vercel
- Monitor Vercel Analytics for anomalies
- Notify stakeholders of the release
- Update Notion project status

## Stack Context
- **GitHub**: Tags and Releases for version tracking. `gh` CLI for release creation.
- **Vercel**: Push to main triggers production deployment. Tags do not trigger separate deploys (Vercel deploys on push, not tag).
- **Notion**: Release tracking and stakeholder communication.
- **npm**: Version tracked in `package.json`.

## Quality Gate
- [ ] Version follows SemVer
- [ ] Changelog updated with all changes
- [ ] GitHub Release created with notes
- [ ] Production deployment verified
- [ ] Stakeholders notified

## Anti-Patterns
- **No versioning** — without version numbers, you cannot communicate what changed.
- **No changelog** — "what changed in the last release?" should never be answered with "I don't remember."
- **Big bang releases** — smaller, more frequent releases are lower risk.
- **No post-release verification** — always check that production works after deployment.

## Related Skills
- `engineering/devops` — deployment infrastructure
- `engineering/cicd-pipeline` — automated pipeline that supports releases
- `engineering/pr-review` — PRs that make up a release
