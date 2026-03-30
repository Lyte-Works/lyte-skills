<!-- reconstructed -->
---
name: "soc2-compliance"
description: "SOC 2 compliance framework — trust service criteria, controls, evidence collection, and audit preparation"
workers: ["security-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# SOC 2 Compliance

## When to Use
- SaaS client requires SOC 2 certification
- Enterprise customers request security documentation
- Building a compliance program from scratch
- Preparing for a SOC 2 audit

## Workflow

### Step 1: Understand the Trust Service Criteria
SOC 2 covers five trust service criteria:

| Criteria | Focus | Key Controls |
|----------|-------|-------------|
| **Security** (required) | Protection against unauthorized access | Access controls, encryption, monitoring |
| **Availability** | System uptime and reliability | SLAs, incident response, backups |
| **Processing Integrity** | Data processed correctly | Validation, error handling, audit trails |
| **Confidentiality** | Data protection | Encryption, access controls, classification |
| **Privacy** | Personal data handling | GDPR-like controls, consent, retention |

### Step 2: Map Controls to Stack
| Control | Implementation |
|---------|---------------|
| Access control | NextAuth + Supabase RLS |
| Encryption in transit | HTTPS (Vercel default) |
| Encryption at rest | Supabase (encrypted by default) |
| Change management | GitHub PRs, branch protection, code review |
| Monitoring | Vercel logs, Supabase logs |
| Incident response | SecOps incident response plan |
| Backup and recovery | Supabase automatic backups |
| Vulnerability management | npm audit, Dependabot, security audit |

### Step 3: Evidence Collection
SOC 2 auditors need evidence. Collect:
- **Access reviews**: Who has access to what? Document in Notion.
- **Change logs**: GitHub commit history, PR reviews, deployment logs.
- **Incident logs**: Post-mortems and incident responses.
- **Security configurations**: Security headers, RLS policies, auth setup.
- **Policies**: Documented security, access, and incident response policies.

### Step 4: Policy Documentation
Create these policies in Notion:
1. **Information Security Policy** — overall security approach
2. **Access Control Policy** — who gets access to what, how access is granted/revoked
3. **Change Management Policy** — how code changes are reviewed and deployed
4. **Incident Response Policy** — how security incidents are handled
5. **Data Classification Policy** — how data is categorized and protected
6. **Acceptable Use Policy** — how systems and data should be used

### Step 5: Gap Analysis
Compare current state against SOC 2 requirements:
| Control | Required | Current State | Gap | Remediation |
|---------|----------|--------------|-----|-------------|
| MFA on all admin accounts | Yes | No | Gap | Enable MFA on GitHub, Vercel, Supabase |
| Access reviews quarterly | Yes | Never done | Gap | Schedule quarterly access reviews |
| Encrypted backups | Yes | Supabase default | Met | Document |

### Step 6: Remediation and Maintenance
- Fix all gaps identified in Step 5
- Schedule recurring reviews (quarterly access reviews, annual policy reviews)
- Maintain evidence collection as an ongoing process, not a pre-audit scramble

## Stack Context
- **GitHub**: Change management evidence — PRs, reviews, branch protection.
- **Vercel**: Deployment logs, access controls, HTTPS enforcement.
- **Supabase**: Database encryption, RLS policies, automatic backups, auth logs.
- **Notion**: Policy documentation, access reviews, and evidence tracking.
- **NextAuth**: Authentication controls and session management.

## Quality Gate
- [ ] Trust service criteria mapped to stack controls
- [ ] All required policies documented
- [ ] Gap analysis completed
- [ ] Critical gaps remediated
- [ ] Evidence collection process established
- [ ] Recurring reviews scheduled

## Anti-Patterns
- **Compliance theater** — writing policies nobody follows. Policies must reflect actual practice.
- **Pre-audit panic** — SOC 2 requires ongoing evidence. You cannot fake 12 months of controls in 2 weeks.
- **Over-engineering** — SOC 2 Type I (point-in-time) is achievable for startups. Do not try to implement every possible control at once.
- **Ignoring people controls** — SOC 2 is not just technology. Access reviews, training, and policies matter.

## Related Skills
- `engineering/security-engineer` — implementing technical controls
- `engineering/security-audit` — vulnerability assessment
- `engineering/gdpr-compliance` — privacy-specific compliance
- `engineering/secops` — incident response capability
