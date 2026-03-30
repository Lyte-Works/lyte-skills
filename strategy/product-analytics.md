<!-- reconstructed -->
---
name: "product-analytics"
description: "Measure product performance — funnel analysis, feature adoption, retention, and data-driven product decisions"
workers: ["product-manager", "research-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Product Analytics

## When to Use
- Measuring feature adoption after a launch
- Understanding user funnels and drop-off points
- Tracking retention and engagement metrics
- Making data-driven prioritization decisions
- Client asks "is this feature working?"

## Workflow

### Step 1: Define Key Metrics
Identify the metrics that matter for the product:

**North Star Metric**: One metric that best captures the value the product delivers.
- For SaaS: Weekly Active Users, or a product-specific engagement metric
- For e-commerce: Revenue per visitor
- For content: Engaged reading time

**Supporting Metrics** (pick 3-5):
| Category | Metric | How to Measure |
|----------|--------|---------------|
| Acquisition | New signups/visitors | Vercel Analytics |
| Activation | First key action completed | Custom event tracking |
| Retention | Return rate (day 1, 7, 30) | Supabase user activity |
| Revenue | MRR / conversion rate | Stripe + Vercel Analytics |
| Referral | Invites sent / referral signups | Custom event tracking |

### Step 2: Set Up Tracking
Implement event tracking in the Next.js application:

```typescript
// Use Vercel Analytics for page views (automatic)
// For custom events, use Vercel Analytics custom events:
import { track } from '@vercel/analytics';

// Track key actions
track('signup_completed');
track('feature_used', { feature: 'export' });
track('upgrade_clicked', { plan: 'pro' });
```

For more complex analytics needs:
- Use Supabase to store event data for custom analysis
- Build a simple analytics dashboard as a protected page in the app

### Step 3: Funnel Analysis
Map the user journey and measure conversion at each step:

```
Visit site → Sign up → Complete onboarding → First key action → Return visit → Upgrade
  100%    →   15%   →        60%          →      40%         →    30%      →   5%
```

Identify the biggest drop-off point. That is where optimization effort has the highest leverage.

### Step 4: Feature Adoption Tracking
For each new feature:
- **Discoverability**: What % of users encounter the feature?
- **Adoption**: What % of users who encounter it use it?
- **Retention**: What % of users continue using it after first use?
- **Impact**: Does using the feature correlate with higher retention or revenue?

### Step 5: Reporting Cadence
| Report | Frequency | Content | Audience |
|--------|-----------|---------|----------|
| Dashboard | Always-on | Key metrics, real-time | Team |
| Weekly digest | Weekly | Trends, anomalies | Product + Engineering |
| Monthly review | Monthly | Deep analysis, recommendations | Leadership |
| Feature report | Per feature | Adoption and impact analysis | Product team |

### Step 6: Act on Data
Analytics without action is vanity. For each reporting cycle:
- Identify the top insight (what did we learn?)
- Define the action (what are we going to do about it?)
- Assign the owner (who is responsible?)
- Set the timeline (when will we check the result?)

## Stack Context
- **Vercel Analytics**: Primary analytics tool. Provides page views, unique visitors, top pages, referrers, and custom events. No cookie consent banner needed (privacy-friendly).
- **Next.js**: Custom event tracking implemented in components. Use Server Components for analytics dashboards that query Supabase.
- **Supabase**: Store custom event data for analysis that goes beyond Vercel Analytics. Use SQL queries for funnel analysis and cohort reports.
- **Notion**: Monthly analytics reports and feature adoption reports documented in Notion.

## Quality Gate
- [ ] North Star Metric defined and measurable
- [ ] 3-5 supporting metrics identified with tracking plan
- [ ] Event tracking implemented in the application
- [ ] At least one funnel mapped with conversion rates
- [ ] Reporting cadence established
- [ ] Each report includes an action item, not just numbers

## Anti-Patterns
- **Tracking everything** — more data is not better data. Track what informs decisions.
- **Vanity metrics** — page views without context are meaningless. Focus on metrics tied to business outcomes.
- **Analysis paralysis** — do not wait for perfect data. Act on directional signals.
- **No baseline** — measuring improvement requires a baseline. Establish metrics before making changes.
- **Dashboard without owner** — a dashboard nobody checks is theater. Assign responsibility.

## Related Skills
- `strategy/product-manager` — analytics informs product prioritization
- `communications/analytics-tracking` — implementing tracking across the site
- `communications/ab-test-setup` — testing hypotheses from analytics insights
- `operations/saas-metrics` — SaaS-specific metrics and benchmarks
- `engineering/performance-profiler` — performance metrics complement product analytics
