# Lyte Skills

Curated skills for Lyte Workers. Each skill is a structured workflow that workers load during boot step 4.5 (Skill Resolution) when a task matches their domain.

## Stack

All skills are written for:

- **Next.js** (App Router, TypeScript, Server Components)
- **Tailwind CSS** (only styling method)
- **Vercel** (deployment, analytics)
- **Supabase** (database, auth — when needed)
- **Resend** (email)
- **Notion** (project management, strategy docs)
- **GitHub** (version control, CI/CD)

## Skills Map

### Strategy (18 skills)

| Skill | Workers | Triggers |
|-------|---------|----------|
| [positioning](strategy/positioning.md) | Business Strategist | positioning, value proposition, differentiation |
| [competitive-teardown](strategy/competitive-teardown.md) | Business Strategist, Research Analyst | competitive analysis, competitor teardown |
| [competitor-alternatives](strategy/competitor-alternatives.md) | Business Strategist | competitor positioning, alternatives |
| [launch-strategy](strategy/launch-strategy.md) | Business Strategist, Marketing Strategist | launch, go-to-market, GTM |
| [pricing-strategy](strategy/pricing-strategy.md) | Business Strategist, Product Manager | pricing, plans, tiers, monetization |
| [company-os](strategy/company-os.md) | Business Strategist | operating model, decision framework |
| [customer-research](strategy/customer-research.md) | Research Analyst, Product Manager | customer research, interviews, surveys, personas |
| [market-research-30day](strategy/market-research-30day.md) | Research Analyst | market research, trends, market scanning |
| [reddit-insights](strategy/reddit-insights.md) | Research Analyst | reddit, community sentiment |
| [marketing-psychology](strategy/marketing-psychology.md) | Research Analyst, Marketing Strategist | psychology, behavioral, persuasion |
| [daily-briefing](strategy/daily-briefing.md) | Research Analyst | daily briefing, market intelligence |
| [product-manager](strategy/product-manager.md) | Product Manager | user stories, product specs, backlog |
| [senior-pm](strategy/senior-pm.md) | Product Manager | product roadmap, product strategy |
| [agile-product-owner](strategy/agile-product-owner.md) | Product Manager | sprint planning, backlog grooming, agile |
| [product-analytics](strategy/product-analytics.md) | Product Manager, Research Analyst | product metrics, funnel analysis |
| [ux-researcher](strategy/ux-researcher.md) | Product Manager, UI Designer | usability testing, UX research |
| [ux-designer](strategy/ux-designer.md) | UI Designer, Product Manager | wireframes, user flows, interaction design |
| [site-assessment](strategy/site-assessment.md) | Research Analyst, Marketing Strategist, Business Strategist, Systems Architect | site assessment, website audit, competitor website |

### Engineering (29 skills)

| Skill | Workers | Triggers |
|-------|---------|----------|
| [frontend](engineering/frontend.md) | Frontend Developer | components, pages, UI, React, frontend |
| [fullstack](engineering/fullstack.md) | Frontend Developer, Backend Developer | full stack, end-to-end feature |
| [backend](engineering/backend.md) | Backend Developer | API routes, server actions, backend logic |
| [landing-page-generator](engineering/landing-page-generator.md) | Frontend Developer, UI Designer | landing page, marketing page |
| [playwright-e2e](engineering/playwright-e2e.md) | Frontend Developer, Code Reviewer | E2E testing, Playwright |
| [stripe-integration](engineering/stripe-integration.md) | Frontend Developer, Backend Developer | payments, Stripe, checkout |
| [database-designer](engineering/database-designer.md) | Backend Developer, Systems Architect | database schema, data model, migrations |
| [rag-architect](engineering/rag-architect.md) | Backend Developer, Systems Architect | RAG, embeddings, vector search |
| [agent-designer](engineering/agent-designer.md) | Backend Developer, Systems Architect | AI agent, agent architecture |
| [mcp-server-builder](engineering/mcp-server-builder.md) | Backend Developer | MCP, Model Context Protocol |
| [code-review](engineering/code-review.md) | Code Reviewer | code review, quality check |
| [pr-review](engineering/pr-review.md) | Code Reviewer | PR review, pull request |
| [tdd](engineering/tdd.md) | Code Reviewer, Frontend Developer, Backend Developer | TDD, test driven, test coverage |
| [dependency-audit](engineering/dependency-audit.md) | Code Reviewer, Security Analyst | dependencies, vulnerability scan, npm audit |
| [tech-debt-tracker](engineering/tech-debt-tracker.md) | Code Reviewer, Systems Architect | tech debt, refactor priorities |
| [security-engineer](engineering/security-engineer.md) | Security Analyst | application security, secure coding |
| [secops](engineering/secops.md) | Security Analyst | incident response, security operations |
| [security-audit](engineering/security-audit.md) | Security Analyst | security audit, vulnerability assessment, OWASP |
| [gdpr-compliance](engineering/gdpr-compliance.md) | Security Analyst, Legal Advisor | GDPR, privacy, data protection |
| [soc2-compliance](engineering/soc2-compliance.md) | Security Analyst, Legal Advisor | SOC 2, security compliance |
| [iso27001](engineering/iso27001.md) | Security Analyst | ISO 27001, ISMS |
| [devops](engineering/devops.md) | DevOps Engineer | deployment, infrastructure, CI/CD |
| [cicd-pipeline](engineering/cicd-pipeline.md) | DevOps Engineer | pipeline, GitHub Actions |
| [release-manager](engineering/release-manager.md) | DevOps Engineer | release, versioning, changelog |
| [performance-profiler](engineering/performance-profiler.md) | DevOps Engineer, Frontend Developer | performance, Core Web Vitals, Lighthouse |
| [senior-architect](engineering/senior-architect.md) | Systems Architect | system design, architecture |
| [saas-scaffolder](engineering/saas-scaffolder.md) | Systems Architect, Frontend Developer | SaaS scaffold, new project, bootstrap |
| [qa-engineer](engineering/qa-engineer.md) | Systems Architect, Code Reviewer | QA strategy, test planning |
| [ui-designer](engineering/ui-designer.md) | UI Designer | design specs, visual design, design system |

### Communications (38 skills)

| Skill | Workers | Triggers |
|-------|---------|----------|
| [seo-audit](communications/seo-audit.md) | Marketing Strategist | SEO audit, search optimization |
| [ai-seo](communications/ai-seo.md) | Marketing Strategist, Content Writer | AI SEO, GEO, LLM optimization |
| [ai-discoverability-audit](communications/ai-discoverability-audit.md) | Marketing Strategist, Research Analyst | AI discoverability, ChatGPT mentions |
| [content-strategy](communications/content-strategy.md) | Marketing Strategist, Content Writer | content strategy, editorial calendar |
| [site-architecture](communications/site-architecture.md) | Marketing Strategist, Systems Architect | site architecture, URL structure |
| [schema-markup](communications/schema-markup.md) | Marketing Strategist, Frontend Developer, Content Writer | JSON-LD, structured data, rich results |
| [programmatic-seo](communications/programmatic-seo.md) | Marketing Strategist, Frontend Developer | programmatic SEO, pages at scale |
| [analytics-tracking](communications/analytics-tracking.md) | Marketing Strategist, DevOps Engineer | analytics, tracking, events |
| [free-tool-strategy](communications/free-tool-strategy.md) | Marketing Strategist | free tool, lead magnet, calculator |
| [marketing-ideas](communications/marketing-ideas.md) | Marketing Strategist | marketing ideas, brainstorm |
| [growth-marketer](communications/growth-marketer.md) | Marketing Strategist | growth strategy, acquisition |
| [linkedin-authority](communications/linkedin-authority.md) | Marketing Strategist, PR Manager | LinkedIn strategy, LinkedIn authority |
| [content-idea-generator](communications/content-idea-generator.md) | Marketing Strategist, Content Writer | content ideas, blog topics |
| [copywriting](communications/copywriting.md) | Content Writer | copywriting, headlines, web copy |
| [copy-editing](communications/copy-editing.md) | Content Writer | copy editing, proofread, tone |
| [email-sequences](communications/email-sequences.md) | Content Writer, Marketing Strategist | email sequence, drip campaign |
| [cold-email](communications/cold-email.md) | Content Writer, Sales Lead | cold email, outreach email |
| [social-content](communications/social-content.md) | Content Writer, Marketing Strategist | social media post, social content |
| [newsletter](communications/newsletter.md) | Content Writer | newsletter, email newsletter |
| [voice-extractor](communications/voice-extractor.md) | Content Writer, Brand Designer | brand voice, writing style |
| [de-ai-ify](communications/de-ai-ify.md) | Content Writer | sounds like AI, humanize copy |
| [content-humanizer](communications/content-humanizer.md) | Content Writer | humanize content, authentic tone |
| [case-study-builder](communications/case-study-builder.md) | Content Writer, Sales Lead | case study, client story, success story |
| [testimonial-collector](communications/testimonial-collector.md) | Content Writer, Sales Lead | testimonial, social proof |
| [paid-ads](communications/paid-ads.md) | Performance Marketer | paid ads, Google Ads, PPC |
| [ad-creative](communications/ad-creative.md) | Performance Marketer, Brand Designer | ad creative, ad copy |
| [page-cro](communications/page-cro.md) | Performance Marketer, Marketing Strategist | landing page optimization, CRO |
| [signup-flow-cro](communications/signup-flow-cro.md) | Performance Marketer | signup optimization |
| [onboarding-cro](communications/onboarding-cro.md) | Performance Marketer, Product Manager | onboarding optimization |
| [form-cro](communications/form-cro.md) | Performance Marketer, Frontend Developer | form optimization |
| [popup-cro](communications/popup-cro.md) | Performance Marketer | popup optimization |
| [paywall-cro](communications/paywall-cro.md) | Performance Marketer | paywall, upgrade flow |
| [ab-test-setup](communications/ab-test-setup.md) | Performance Marketer, Marketing Strategist | A/B test, experiment |
| [referral-program](communications/referral-program.md) | Performance Marketer, Marketing Strategist | referral program, viral loop |
| [churn-prevention](communications/churn-prevention.md) | Performance Marketer, Product Manager | churn, retention |
| [social-card-gen](communications/social-card-gen.md) | Brand Designer, UI Designer | OG image, social card |
| [linkedin-profile-optimizer](communications/linkedin-profile-optimizer.md) | PR Manager, Marketing Strategist | LinkedIn profile |
| [meeting-prep](communications/meeting-prep.md) | PR Manager, Sales Lead, Business Strategist | meeting prep, call prep |

### Operations (9 skills)

| Skill | Workers | Triggers |
|-------|---------|----------|
| [sales-engineer](operations/sales-engineer.md) | Sales Lead | technical sales, demo, POC |
| [sales-enablement](operations/sales-enablement.md) | Sales Lead | sales collateral, battle cards |
| [cold-outreach-sequence](operations/cold-outreach-sequence.md) | Sales Lead | outreach sequence, prospecting |
| [contract-writer](operations/contract-writer.md) | Sales Lead, Legal Advisor | contract, proposal, SOW |
| [revops](operations/revops.md) | Sales Lead, Marketing Strategist | revenue operations, pipeline |
| [financial-analyst](operations/financial-analyst.md) | Financial Analyst | financial model, budget, forecast |
| [saas-metrics](operations/saas-metrics.md) | Financial Analyst, Product Manager | SaaS metrics, MRR, CAC, LTV |
| [chro-advisor](operations/chro-advisor.md) | People Manager | HR strategy, hiring plan, culture |
| [change-management](operations/change-management.md) | People Manager | organizational change, restructuring |

### Advisory (10 skills)

| Skill | Workers | Triggers |
|-------|---------|----------|
| [ceo-advisor](advisory/ceo-advisor.md) | Business Strategist | CEO-level, strategic decision |
| [cto-advisor](advisory/cto-advisor.md) | Systems Architect | CTO-level, tech strategy |
| [cfo-advisor](advisory/cfo-advisor.md) | Financial Analyst | CFO-level, financial strategy |
| [cmo-advisor](advisory/cmo-advisor.md) | Marketing Strategist | CMO-level, marketing leadership |
| [cro-advisor](advisory/cro-advisor.md) | Performance Marketer, Sales Lead | CRO-level, revenue strategy |
| [cpo-advisor](advisory/cpo-advisor.md) | Product Manager | CPO-level, product leadership |
| [coo-advisor](advisory/coo-advisor.md) | People Manager | COO-level, operations leadership |
| [ciso-advisor](advisory/ciso-advisor.md) | Security Analyst | CISO-level, security strategy |
| [board-deck-builder](advisory/board-deck-builder.md) | Business Strategist, Financial Analyst | board deck, investor deck |
| [ma-playbook](advisory/ma-playbook.md) | Business Strategist | M&A, acquisition |

### Core (3 skills)

| Skill | Workers | Triggers |
|-------|---------|----------|
| [vault-cleanup](core/vault-cleanup.md) | Knowledge Manager | knowledge cleanup, audit knowledge |
| [decision-logger](core/decision-logger.md) | Knowledge Manager, Systems Architect | decision log, ADR |
| [scrum-master](core/scrum-master.md) | Product Manager | sprint ceremonies, standup, retro |

## How Skills Load

Workers load skills at boot step 4.5 (Skill Resolution):

1. The manifest (`.lyte/skills/manifest.md` in the agency repo) is scanned for skills matching the worker AND the task
2. If a match is found, the skill is fetched from this repo
3. Only **primary** skills load by default. **Secondary** skills load if primary doesn't cover the sub-task
4. Maximum 3 skills per task
5. If no skills match, the worker proceeds with innate skills only
6. If the worker needs methodology not in the manifest, browse this map

## Format

See [format.md](format.md) for the skill authoring standard.

## License

MIT. See [LICENSE](LICENSE).

## Attribution

Curated and rewritten from open-source skill repos. See [ATTRIBUTION.md](ATTRIBUTION.md).
