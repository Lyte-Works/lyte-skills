# Skill Authoring Standard

Every skill in this repository follows a consistent format to ensure clarity, actionability, and stack alignment.

## Template

```markdown
---
name: "skill-name"
description: "One-line description with trigger keywords"
workers: ["worker1", "worker2"]
stack: "aligned"
source: "Original repo attribution"
---

# Skill Name

## When to Use
[Trigger patterns — what kind of request or situation activates this skill]

## Workflow
[Step-by-step process with numbered steps, clear inputs and outputs]

## Stack Context
[How this skill applies within the default stack: Next.js App Router, TypeScript, Tailwind CSS, Vercel, Resend, Supabase, Notion, GitHub]

## Quality Gate
[Output verification checklist — what must be true before the skill's output is considered complete]

## Anti-Patterns
[What NOT to do — common mistakes, misapplications, and traps]

## Related Skills
[Cross-references to other skills in this repository]
```

## Rules for All Skills

1. **Code examples** use TypeScript, Next.js App Router, and Tailwind CSS
2. **Deployment** targets Vercel (push-to-deploy from GitHub main branch)
3. **Analytics** uses Vercel Analytics as primary; GA4 is optional and secondary
4. **Database** uses Supabase (Postgres + Row Level Security) when a database is needed
5. **Email** uses Resend for all transactional and marketing email
6. **Project management** uses Notion for strategy docs, plans, and content
7. **Version control** uses GitHub with one repo per client project
8. **Styling** uses Tailwind CSS exclusively — no CSS modules, no styled-components
9. **Server-first** — prefer Server Components and Server Actions; Client Components are opt-in
10. **Opinionated and actionable** — every skill provides steps, not suggestions

## Alignment Principles

Every skill embodies these principles:

- **AI-first where it serves** — if a process can be handled by an agent, it should be. But the human must always understand, override, and direct.
- **Transparency over mystification** — never make AI seem more magical or capable than it is.
- **No obscured systems** — do not build things the client cannot understand.
- **Minimal data retention** — do not collect or retain client data beyond what the work requires.
- **Honest capabilities** — do not promise outcomes that current technology cannot deliver.
- **Clear AI disclosure** — do not build systems that deceive end users about what they are interacting with.
