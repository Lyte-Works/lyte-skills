<!-- reconstructed -->
---
name: "churn-prevention"
description: "Customer retention and churn reduction — identify at-risk users, intervene, and improve retention"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Churn Prevention

## When to Use
- Churn rate is above industry benchmarks
- Users are canceling and the reason is unclear
- Building a retention strategy
- Identifying and saving at-risk customers

## Workflow

### Step 1: Understand Churn
Calculate and benchmark:
- **Monthly churn rate**: Users lost / Total users at start of month
- **Revenue churn**: MRR lost / Total MRR at start of month
- SaaS benchmarks: <5% monthly logo churn, <2% monthly revenue churn

### Step 2: Identify Churn Signals
| Signal | Data Source | Risk Level |
|--------|-----------|-----------|
| No login for 14+ days | Supabase auth logs | Medium |
| No login for 30+ days | Supabase auth logs | High |
| Support ticket unresolved | Support system | Medium |
| Downgrade inquiry | Billing | High |
| Feature usage declining | Product analytics | Medium |
| Payment failed | Stripe webhook | Critical |

### Step 3: Churn Survey
When users cancel, ask why (keep it simple):
1. Too expensive
2. Missing features I need
3. Switched to a competitor
4. No longer need the product
5. Hard to use
6. Other: [text field]

Implement as a cancellation flow step (before final cancellation).

### Step 4: Intervention Playbooks

**At-risk (declining usage):**
- Email: "We noticed you haven't used [feature] recently. Here's a quick tip..."
- Offer: schedule a success call

**Pre-cancel (downgrade inquiry):**
- Offer: plan pause instead of cancel
- Offer: temporary discount
- Offer: switch to lower tier (keep them, even at lower revenue)

**Failed payment:**
- Email series: 3 attempts over 7 days
- In-app banner: "Update your payment method"
- Grace period: do not immediately revoke access

**Post-cancel:**
- Exit survey
- "We're sorry to see you go" email with link to reactivate
- 30-day follow-up: "Things have changed — here's what's new"

### Step 5: Proactive Retention
- **Onboarding excellence**: best retention investment
- **Regular value delivery**: ensure users see value every week
- **Check-in emails**: monthly usage summaries showing value delivered
- **Community**: connect users with each other
- **Feature education**: highlight underused features

### Step 6: Measure
Track monthly:
- Churn rate (logo and revenue)
- Churn reasons (from exit survey)
- Save rate (% of at-risk users retained)
- Reactivation rate (% of churned users who return)

## Stack Context
- **Supabase**: User activity tracking, churn signals.
- **Stripe**: Payment failure webhooks, subscription status.
- **Resend**: Retention emails, dunning emails, win-back campaigns.
- **Next.js**: Cancellation flow with exit survey. Usage dashboard.
- **Vercel Analytics**: Track engagement patterns.
- **Notion**: Churn analysis and intervention results.

## Quality Gate
- [ ] Churn rate calculated and benchmarked
- [ ] Churn signals defined and monitored
- [ ] Exit survey implemented
- [ ] At least 3 intervention playbooks active
- [ ] Failed payment dunning sequence running
- [ ] Monthly churn review conducted

## Anti-Patterns
- **Ignoring churn** — focusing only on acquisition while customers leak out is unsustainable.
- **Hard to cancel** — making cancellation difficult creates angry ex-customers, not retained ones.
- **No exit survey** — if you do not know why people leave, you cannot fix it.
- **Only discounting** — discounts temporarily delay churn. Fix the root cause.
- **No dunning** — failed payments are involuntary churn. A simple email sequence recovers most.

## Related Skills
- `communications/onboarding-cro` — prevention starts at onboarding
- `communications/email-sequences` — retention email flows
- `operations/saas-metrics` — churn within SaaS metrics
- `strategy/product-analytics` — usage data for churn prediction
