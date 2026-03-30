<!-- reconstructed -->
---
name: "devops"
description: "DevOps engineering for Vercel — deployment configuration, environment management, monitoring, and infrastructure"
workers: ["devops-engineer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# DevOps Engineer

## When to Use
- Setting up a new project's deployment pipeline
- Configuring environment variables across environments
- Setting up monitoring and alerting
- Optimizing build and deployment performance
- Managing multiple environments (preview, staging, production)

## Workflow

### Step 1: Project Setup
```bash
# Initialize Next.js project
npx create-next-app@latest my-project --typescript --tailwind --app --src-dir=false

# Link to Vercel
npx vercel link

# Set up environment variables
npx vercel env add RESEND_API_KEY production
npx vercel env add NEXT_PUBLIC_SUPABASE_URL production preview
```

### Step 2: Environment Strategy
| Environment | Branch | Purpose | URL |
|------------|--------|---------|-----|
| Production | main | Live site | yourdomain.com |
| Preview | any branch | PR review | *.vercel.app |
| Development | local | Development | localhost:3000 |

Environment variables by scope:
- `production` — only production deployment
- `preview` — only preview deployments
- `development` — only local development

### Step 3: Vercel Configuration
```json
// vercel.json
{
  "framework": "nextjs",
  "regions": ["iad1"],
  "crons": [
    {
      "path": "/api/cron/daily",
      "schedule": "0 8 * * *"
    }
  ],
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        { "key": "X-Frame-Options", "value": "SAMEORIGIN" },
        { "key": "X-Content-Type-Options", "value": "nosniff" }
      ]
    }
  ]
}
```

### Step 4: GitHub Actions CI
```yaml
# .github/workflows/ci.yml
name: CI
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  quality:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: 'npm'
      - run: npm ci
      - run: npm run lint
      - run: npm run type-check
      - run: npm test -- --passWithNoTests
```

### Step 5: Monitoring
- **Vercel Analytics**: Page views, web vitals, custom events
- **Vercel Logs**: Function execution logs, errors
- **Vercel Speed Insights**: Core Web Vitals monitoring
- **Supabase Dashboard**: Database health, query performance
- **External uptime monitor**: Verify site is accessible

### Step 6: Deployment Checklist
Before first production deployment:
- [ ] Environment variables set for production
- [ ] Custom domain configured and verified
- [ ] SSL certificate active (Vercel auto-provisions)
- [ ] Security headers configured
- [ ] Analytics enabled
- [ ] Error monitoring active
- [ ] CI pipeline green
- [ ] README updated with setup instructions

## Stack Context
- **Vercel**: Primary deployment platform. Push-to-deploy from GitHub. Preview deployments for every PR.
- **GitHub**: Source code, CI/CD via GitHub Actions, branch protection.
- **Supabase**: Database monitoring via Supabase dashboard.
- **Next.js**: Build output optimized for Vercel's edge network.

## Quality Gate
- [ ] CI pipeline runs lint, type-check, and tests
- [ ] Environment variables properly scoped
- [ ] Branch protection enabled on main
- [ ] Monitoring active for production
- [ ] Deployment documented in README

## Anti-Patterns
- **Manual deployments** — push-to-deploy via GitHub is the standard. No manual Vercel deploys.
- **Environment variable sprawl** — document all env vars in README (without values). Undocumented env vars cause deployment failures.
- **No preview testing** — always test on the Vercel preview before merging to main.
- **Over-engineering infrastructure** — Vercel handles most infrastructure concerns. Do not add complexity unless Vercel is insufficient.
- **No CI** — deploying code that has not been linted and type-checked is reckless.

## Related Skills
- `engineering/cicd-pipeline` — detailed CI/CD configuration
- `engineering/release-manager` — release process
- `engineering/performance-profiler` — performance monitoring
- `engineering/security-engineer` — deployment security
