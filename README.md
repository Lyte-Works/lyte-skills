# Lyte Skills

Curated skills for the Lyte Workers Digital Agency. Each skill is a structured workflow that workers load and execute when a task matches their domain.

## What This Is

A library of 105 actionable skills organized by domain, written for the Lyte Workers Digital Agency stack:

- **Next.js** (App Router, TypeScript, Server Components)
- **Tailwind CSS** (only styling method)
- **Vercel** (deployment, analytics, edge network)
- **Supabase** (database, auth, storage)
- **Resend** (email)
- **Notion** (project management, strategy docs)
- **GitHub** (version control, CI/CD)

## Skill Count by Domain

| Domain | Skills | Focus |
|--------|--------|-------|
| `strategy/` | 17 | Positioning, research, product management, UX |
| `engineering/` | 29 | Frontend, backend, security, DevOps, architecture |
| `communications/` | 37 | SEO, content, copywriting, CRO, ads, social |
| `operations/` | 9 | Sales, finance, HR, change management |
| `advisory/` | 10 | C-level advisory, board prep, M&A |
| `core/` | 3 | Knowledge management, decisions, scrum |
| **Total** | **105** | |

## How Skills Work

Each skill follows the format defined in `format.md`:

1. **When to Use** — trigger patterns that activate the skill
2. **Workflow** — step-by-step process with inputs and outputs
3. **Stack Context** — how the skill applies to our specific tech stack
4. **Quality Gate** — checklist to verify the output is complete
5. **Anti-Patterns** — what NOT to do
6. **Related Skills** — cross-references to other skills

## Usage with Lyte Workers

Workers load skills during their boot sequence based on the task:

1. Observer reads the task
2. Observer matches the task to a worker (via `router.md`)
3. Worker boots and loads relevant skills
4. Worker executes the skill workflow
5. Output is delivered to the appropriate destination (GitHub, Notion, Resend)

## Authoring

See `format.md` for the skill authoring standard. All skills follow the same structure and rules.

## Alignment

Every skill embodies the agency's alignment principles:

- AI-first where it serves
- Transparency over mystification
- No obscured systems
- Minimal data retention
- Honest capabilities

## License

MIT. See `LICENSE`.

## Attribution

These skills were curated and rewritten from multiple open-source skill repositories. See `ATTRIBUTION.md` for full credits.
