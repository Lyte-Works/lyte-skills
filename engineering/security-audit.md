<!-- reconstructed -->
---
name: "security-audit"
description: "OWASP-based security audit — vulnerability assessment, penetration testing checklist, and remediation"
workers: ["security-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Security Audit

## When to Use
- Before launching a new application to production
- Annual or semi-annual security review
- After a security incident
- Before handling sensitive data (PII, financial, health)
- Client requires a security assessment

## Workflow

### Step 1: OWASP Top 10 Checklist
Review the application against the OWASP Top 10:

| # | Risk | Check | Next.js Mitigation |
|---|------|-------|-------------------|
| 1 | Broken Access Control | Auth on all protected routes? Authorization in Server Actions? | NextAuth middleware + server-side auth checks |
| 2 | Cryptographic Failures | Secrets exposed? Data encrypted in transit? | HTTPS (Vercel default), env vars for secrets |
| 3 | Injection | Input validated? Parameterized queries? | Zod validation, Supabase client (parameterized) |
| 4 | Insecure Design | Threat model created? Business logic flaws? | Design review before implementation |
| 5 | Security Misconfiguration | Headers set? Default credentials changed? Debug off? | Security headers in next.config.ts |
| 6 | Vulnerable Components | Dependencies audited? | npm audit, Dependabot |
| 7 | Auth Failures | Brute force protection? Session management? | NextAuth with proper session config |
| 8 | Software/Data Integrity | Dependencies verified? CI/CD secured? | Lock files committed, branch protection |
| 9 | Logging Failures | Security events logged? | Vercel logs, Supabase logs |
| 10 | SSRF | Server-side requests validated? | Validate and allowlist outbound URLs |

### Step 2: Application-Specific Checks
- [ ] All environment variables documented and not committed
- [ ] `.env` in `.gitignore`
- [ ] No `console.log` with sensitive data in production
- [ ] File upload validation (if applicable): type, size, content
- [ ] Rate limiting on authentication endpoints
- [ ] CSRF protection (Next.js Server Actions have built-in CSRF tokens)
- [ ] RLS enabled on all Supabase tables with user data

### Step 3: Infrastructure Checks
- [ ] HTTPS enforced (Vercel handles this)
- [ ] DNS configured correctly (no dangling CNAMEs)
- [ ] Vercel environment variables set per environment (production vs. preview)
- [ ] GitHub branch protection on main
- [ ] Dependabot enabled

### Step 4: Findings Report
Document each finding:
```
## Finding: [Title]
**Severity**: Critical / High / Medium / Low
**Location**: [File path or URL]
**Description**: [What the vulnerability is]
**Impact**: [What could happen if exploited]
**Remediation**: [How to fix it]
**Status**: Open / In Progress / Resolved
```

### Step 5: Remediation Plan
Prioritize findings by severity, create tasks, and track resolution:
1. Critical and High: fix before launch / immediately
2. Medium: fix within 30 days
3. Low: fix within 90 days or accept risk with documentation

## Stack Context
- **Next.js**: Server Actions have built-in CSRF protection. Middleware handles auth and security headers.
- **Vercel**: HTTPS by default. Environment variables per deployment environment.
- **Supabase**: RLS policies are the primary database security mechanism.
- **GitHub**: Dependabot, branch protection, and security advisories.
- **Notion**: Audit findings and remediation tracking documented in Notion.

## Quality Gate
- [ ] OWASP Top 10 checklist completed
- [ ] All critical and high findings resolved before launch
- [ ] Findings documented with severity, impact, and remediation
- [ ] Remediation plan with timelines and owners
- [ ] Re-audit after remediation confirms findings are resolved

## Anti-Patterns
- **Audit without remediation** — a report gathering dust is not security.
- **One-time audit** — security degrades as code changes. Audit regularly.
- **Automated tools only** — scanners miss business logic flaws. Manual review is essential.
- **Ignoring low-severity findings** — attackers chain low-severity issues into high-impact exploits.
- **Security theater** — checking boxes without understanding the risks.

## Related Skills
- `engineering/security-engineer` — implementing security measures
- `engineering/secops` — responding to incidents
- `engineering/gdpr-compliance` — privacy-specific audit
- `engineering/dependency-audit` — component-specific audit
