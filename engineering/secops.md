<!-- reconstructed -->
---
name: "secops"
description: "Security operations — incident response, monitoring, alerting, and security event management"
workers: ["security-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# SecOps

## When to Use
- Responding to a security incident
- Setting up security monitoring and alerting
- Building an incident response plan
- Post-incident review and improvement
- Ongoing security operations for a production application

## Workflow

### Step 1: Incident Response Plan
Define a response plan before incidents happen:

| Phase | Actions | Owner |
|-------|---------|-------|
| **Detection** | Monitor alerts, user reports, dependency warnings | Security Analyst |
| **Triage** | Assess severity, scope, and impact | Security Analyst |
| **Containment** | Stop the bleeding — disable affected features, rotate keys | Backend Developer |
| **Eradication** | Fix the root cause | Engineering team |
| **Recovery** | Restore service, verify fix | DevOps + Engineering |
| **Post-mortem** | Document what happened, what we learned, what changes | All |

### Step 2: Severity Classification
| Level | Description | Response Time | Example |
|-------|-------------|--------------|---------|
| **Critical** | Data breach, full system compromise | Immediate | Database exposed, auth bypass |
| **High** | Active exploitation, service down | Within 1 hour | XSS in production, API key leaked |
| **Medium** | Vulnerability discovered, not exploited | Within 24 hours | Dependency vulnerability, missing validation |
| **Low** | Improvement opportunity, no active risk | Within 1 week | Security header missing, audit finding |

### Step 3: Monitoring Setup
For a Vercel-deployed Next.js application:
- **Vercel Logs**: Monitor for unusual error patterns
- **Supabase Logs**: Watch for failed auth attempts, unusual queries
- **GitHub**: Dependabot alerts for dependency vulnerabilities
- **Uptime monitoring**: External service to verify site availability

### Step 4: Incident Response Checklist
When an incident occurs:
1. [ ] Classify severity (Critical/High/Medium/Low)
2. [ ] Notify stakeholders (based on severity)
3. [ ] Contain: disable affected features or rotate compromised credentials
4. [ ] Document: start an incident log with timestamps
5. [ ] Investigate: identify root cause
6. [ ] Fix: implement and deploy the fix
7. [ ] Verify: confirm the fix resolves the issue
8. [ ] Communicate: update stakeholders and affected users
9. [ ] Post-mortem: document lessons learned

### Step 5: Common Incident Playbooks

**Leaked API Key:**
1. Immediately rotate the key in the service dashboard
2. Update environment variables in Vercel
3. Search git history for the commit that leaked it
4. If committed to GitHub, consider the key compromised even if the commit is removed
5. Audit logs for unauthorized usage during the exposure window

**Dependency Vulnerability:**
1. Assess: is the vulnerability exploitable in our usage?
2. Update the dependency to a patched version
3. If no patch exists, evaluate mitigation or replacement
4. Run tests, deploy via preview, verify, merge

**Unauthorized Access Attempt:**
1. Review Supabase auth logs for the attempt
2. If successful: immediately revoke sessions, rotate keys, investigate scope
3. If unsuccessful: evaluate whether defenses held, improve if needed
4. Consider rate limiting or IP blocking if pattern is systematic

### Step 6: Post-Mortem Template
```
# Incident Post-Mortem — [Date] — [Title]

## Summary
[One paragraph: what happened, impact, resolution]

## Timeline
[Timestamped events from detection to resolution]

## Root Cause
[What caused the incident]

## Impact
[Who was affected, what data was exposed, what service was disrupted]

## Resolution
[What was done to fix it]

## Lessons Learned
- What went well
- What could be improved
- Action items with owners and deadlines
```

## Stack Context
- **Vercel**: Deployment logs, function logs, and analytics for monitoring.
- **Supabase**: Auth logs, database logs, and query logs.
- **GitHub**: Dependabot for dependency monitoring. Security advisories for codebase vulnerabilities.
- **Notion**: Incident logs, post-mortems, and the incident response plan stored in Notion.
- **Resend**: Notify stakeholders via email during incidents.

## Quality Gate
- [ ] Incident response plan documented and accessible
- [ ] Severity classification defined
- [ ] Monitoring active for critical services
- [ ] At least one playbook exists for common incidents
- [ ] Post-mortem conducted within 48 hours of resolution
- [ ] Action items from post-mortems tracked to completion

## Anti-Patterns
- **No plan** — creating a response plan during an incident is too late.
- **Blame culture** — post-mortems identify system failures, not individual failures.
- **Ignoring low-severity findings** — low-severity issues compound into high-severity incidents.
- **No post-mortem** — without learning from incidents, you repeat them.
- **Over-reacting** — not every alert is a critical incident. Triage before escalating.

## Related Skills
- `engineering/security-engineer` — preventive security measures
- `engineering/security-audit` — proactive vulnerability assessment
- `engineering/devops` — deployment and infrastructure monitoring
