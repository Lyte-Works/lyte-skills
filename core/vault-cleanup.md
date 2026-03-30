<!-- reconstructed -->
---
name: "vault-cleanup"
description: "Knowledge base hygiene — audit, clean, organize, and maintain documentation and knowledge repositories"
workers: ["knowledge-manager"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Vault Cleanup

## When to Use
- Knowledge base (Notion workspace) is disorganized or outdated
- Onboarding new team members reveals documentation gaps
- Quarterly documentation health check
- After a project completes (archive and clean)

## Workflow

### Step 1: Audit
Inventory all documentation:
| Document | Location | Last Updated | Owner | Status |
|----------|----------|-------------|-------|--------|
| [Name] | [Notion page/section] | [Date] | [Who] | Current / Outdated / Orphaned |

### Step 2: Categorize
| Category | Action |
|----------|--------|
| **Current and useful** | Keep, verify accuracy |
| **Outdated but needed** | Update with current information |
| **Outdated and unneeded** | Archive (do not delete — move to Archive section) |
| **Orphaned** (no owner, no links) | Assign owner or archive |
| **Duplicate** | Merge into single source, redirect |

### Step 3: Organize
Establish a consistent structure:
```
Notion Workspace
├── Active Projects
│   └── [Project Name]
│       ├── Strategy (positioning, research, plans)
│       ├── Content (copy, blog posts, emails)
│       ├── Engineering (specs, ADRs, tech docs)
│       └── Operations (contracts, invoices, plans)
├── Knowledge Base
│   ├── Processes (how we do things)
│   ├── Templates (reusable starting points)
│   └── Reference (industry knowledge, research)
├── Archive
│   └── [Completed projects, old docs]
└── Team
    ├── Meeting Notes
    └── Decisions Log
```

### Step 4: Clean Up
For each document that stays:
- [ ] Title is clear and descriptive
- [ ] Content is accurate and current
- [ ] Owner is assigned
- [ ] Last updated date is visible
- [ ] Links to related documents work
- [ ] No placeholder or draft content presented as final

### Step 5: Establish Maintenance Cadence
| Frequency | Action |
|-----------|--------|
| Monthly | Review active project docs for accuracy |
| Quarterly | Full vault audit (this skill) |
| Per project completion | Archive completed project docs |
| Per hire/departure | Review and reassign document ownership |

### Step 6: Documentation Standards
Create a "How We Document" page:
- Naming conventions
- Required sections for each document type
- Template links
- Ownership expectations
- Archive policy

## Stack Context
- **Notion**: Primary knowledge base. All documentation lives here.
- **GitHub**: Code documentation (READMEs, ADRs) lives in GitHub repos.
- **Notion + GitHub**: Cross-link between Notion strategy docs and GitHub technical docs.

## Quality Gate
- [ ] All documents inventoried
- [ ] Outdated documents updated or archived
- [ ] Orphaned documents assigned or archived
- [ ] Duplicates merged
- [ ] Consistent folder structure established
- [ ] Maintenance cadence defined
- [ ] Documentation standards published

## Anti-Patterns
- **Deleting instead of archiving** — old documents may be useful for reference. Archive, do not delete.
- **Cleaning without standards** — cleanup without establishing standards means you will clean again in 3 months.
- **No ownership** — documents without owners become outdated. Every document needs an owner.
- **One-time effort** — vault cleanup is a recurring process, not a one-time project.

## Related Skills
- `core/decision-logger` — structured decision documentation
- `strategy/company-os` — organizational documentation
- `core/scrum-master` — project documentation in sprint context
