<!-- reconstructed -->
---
name: "ciso-advisor"
description: "CISO-level security leadership — security strategy, risk management, compliance oversight, and security culture"
workers: ["security-analyst"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# CISO Advisor

## When to Use
- Security strategy at the organizational level
- Risk assessment and prioritization
- Compliance program oversight (SOC 2, GDPR, ISO 27001)
- Security incident executive response
- Building a security culture

## Workflow

### Step 1: Security Posture Assessment
| Area | Status | Priority |
|------|--------|----------|
| Application security | Audit date, findings | |
| Infrastructure security | Vercel, Supabase, GitHub | |
| Data protection | Encryption, access controls, RLS | |
| Compliance | SOC 2, GDPR status | |
| Incident response | Plan exists? Tested? | |
| Security culture | Team awareness | |

### Step 2: Risk Register
| Risk | Likelihood | Impact | Current Controls | Gap | Priority |
|------|-----------|--------|-----------------|-----|----------|
| Data breach | Medium | Critical | RLS, encryption | No monitoring | High |
| Supply chain attack | Low | High | Dependabot | No SCA | Medium |
| Insider threat | Low | High | Access controls | No access reviews | Medium |

### Step 3: Security Roadmap
Prioritize by risk level and effort:
- **Q1**: Address critical and high-risk gaps
- **Q2**: Build monitoring and detection capabilities
- **Q3**: Compliance certification (if needed)
- **Q4**: Advanced protections and automation

### Step 4: Security Metrics
| Metric | Target |
|--------|--------|
| Time to detect | < 24 hours |
| Time to respond | < 4 hours for critical |
| Open vulnerabilities (critical/high) | 0 |
| Security training completion | 100% |
| Compliance audit findings | Decreasing |

### Step 5: Security Culture
- Regular security awareness (quarterly)
- Secure development training for engineers
- Incident response drills
- Celebrate security improvements (not just punish failures)

## Stack Context
- **Vercel**: Infrastructure security managed by Vercel.
- **Supabase**: Database security, RLS policies, encryption.
- **GitHub**: Source code security, Dependabot, branch protection.
- **Notion**: Security documentation, risk register, and compliance tracking.

## Quality Gate
- [ ] Security posture assessed
- [ ] Risk register created and prioritized
- [ ] Security roadmap defined
- [ ] Key security metrics tracked
- [ ] Security culture initiatives active

## Anti-Patterns
- **Security as afterthought** — security built in from the start is cheaper than security bolted on later.
- **Compliance-driven only** — compliance is the floor, not the ceiling. Real security goes beyond checkboxes.
- **Fear-based culture** — teams that fear reporting security issues hide them. Build a blame-free reporting culture.

## Related Skills
- `engineering/security-engineer` — technical security implementation
- `engineering/security-audit` — vulnerability assessment
- `engineering/secops` — incident response
- `engineering/soc2-compliance` — compliance implementation
