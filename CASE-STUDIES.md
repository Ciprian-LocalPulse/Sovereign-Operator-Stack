<div align="center">

```
╔══════════════════════════════════════════════════════════════════════╗
║             CASE STUDIES — OPERATIONAL REFERENCE ENGAGEMENTS        ║
║             Ciprian Stefan Plesca // Xolo Go OÜ                    ║
╚══════════════════════════════════════════════════════════════════════╝
```

</div>

---

> Client identities are not disclosed without explicit consent.
> These reference engagements are described by problem type, solution architecture,
> and outcome — the information that matters to a technical evaluator.

---

## `// ENGAGEMENT REGISTRY`

| ID | ENGAGEMENT TYPE | SECTOR | OUTCOME |
|:---|:---|:---:|:---:|
| `ENG-01` | Sovereign AI Deployment | Technology / SaaS | Production |
| `ENG-02` | Zero-Trust Architecture Design | Financial Services | Deployed |
| `ENG-03` | Enterprise Repo Engineering | Technical Founders | Live |
| `ENG-04` | AI Automation Governance | Professional Services | Operational |
| `ENG-05` | Security Architecture Review | Healthcare-Adjacent | Remediated |

---

## `// ENG-01 · SOVEREIGN AI DEPLOYMENT`

```
SECTOR:          Technology / SaaS
PROBLEM CLASS:   AI Capability Without Data Sovereignty
DURATION:        6 weeks (architecture + deployment)
```

**Problem Statement**

A technology company operating in the B2B SaaS space needed advanced AI capabilities integrated into their core product. Their legal and compliance team had identified that sending customer data to OpenAI, Anthropic, or Google AI violated their enterprise customer contracts, which mandated data residency controls and prohibited third-party AI data processing.

The company's engineering team had evaluated self-hosted options but lacked the infrastructure architecture expertise to design a system that could meet enterprise-grade performance requirements without cloud AI.

**Solution Architecture**

```
INFRASTRUCTURE DESIGN:
  ├── Private GPU compute (on-premise at colocated data centre)
  ├── vLLM inference stack with custom model selection
  ├── Air-gap-capable deployment (full offline operation tested)
  ├── Customer data never leaves customer-contracted infrastructure
  └── Model weights hosted on company-controlled storage

GOVERNANCE LAYER:
  ├── Prompt logging with PII detection and redaction
  ├── Inference audit log (timestamped, actor-attributed)
  ├── Role-based access to inference endpoint
  ├── Rate limiting and cost controls per customer tenant
  └── Compliance documentation for enterprise customer review

COMPLIANCE OUTPUT:
  ├── GDPR data processing agreement template
  ├── Data residency attestation documentation
  └── Audit-ready evidence package for enterprise procurement
```

**Outcome**

- AI capability deployed within contractual data residency constraints
- Enterprise customer procurement objections resolved with documentation
- Inference costs: 80% lower than equivalent cloud AI at volume
- Zero customer data processed by third-party AI infrastructure

---

## `// ENG-02 · ZERO-TRUST ARCHITECTURE DESIGN`

```
SECTOR:          Financial Services (FinTech)
PROBLEM CLASS:   Perimeter Security in a Remote-First Environment
DURATION:        8 weeks (assessment + design + roadmap)
```

**Problem Statement**

A FinTech company with 60 remote employees had inherited a perimeter-based security model from its early office-based days. Following a near-miss security incident involving lateral movement from a compromised contractor account, the board mandated a zero-trust security transformation.

The company operated under FCA regulation (UK) and was beginning a SOC 2 Type II preparation process. The security posture at assessment was: VPN-based access, shared admin credentials for several internal systems, no device trust verification, and minimal audit logging.

**Assessment Findings**

```
CRITICAL FINDINGS:
  ├── 3 shared administrator accounts across production systems
  ├── VPN access granted unconditionally on valid credentials
  ├── No device trust posture verification before access
  ├── Audit logging covering < 30% of access events
  └── Contractor access indistinguishable from employee access in logs

RISK POSTURE:
  ├── Lateral movement capability: HIGH
  ├── Insider threat detectability: LOW
  ├── Regulatory audit readiness: INSUFFICIENT
  └── SOC 2 gap: SIGNIFICANT
```

**Solution Architecture**

```
ZERO-TRUST IMPLEMENTATION:
  ├── Identity: Centralised IdP (Okta) with MFA enforcement
  ├── Device: MDM deployment + device trust posture verification
  ├── Network: Tailscale ZT mesh replacing perimeter VPN
  ├── Access: RBAC redesign, all shared accounts eliminated
  ├── Audit: Centralised logging covering 100% of access events
  └── Contractor: Isolated network segment with time-limited access tokens

COMPLIANCE ALIGNMENT:
  ├── SOC 2: CC6 (Logical access) controls implemented
  ├── FCA: Access control evidence package prepared
  └── ISO 27001: A.9 access control domain addressed
```

**Outcome**

- All shared administrator accounts eliminated within 2 weeks
- Device trust verification deployed across 100% of fleet
- Audit log coverage: 30% → 100% of access events
- SOC 2 Type II audit commenced 3 months post-engagement
- Zero security incidents in 12-month post-implementation period

---

## `// ENG-03 · ENTERPRISE REPOSITORY ENGINEERING`

```
SECTOR:          Technical Founders / Indie Operators
PROBLEM CLASS:   Technical Authority Without Institutional Signal
DURATION:        3 weeks (audit + architecture + rebuild)
```

**Problem Statement**

A highly capable independent technical operator had built a sophisticated portfolio of tools and infrastructure — but their GitHub presence communicated the opposite. Investors reviewing the profile during a seed round described it as "hard to evaluate" and "difficult to understand what the core capability is."

The operator's actual work was enterprise-grade. Their GitHub signalling was junior-developer level.

**Assessment**

```
AUDIT FINDINGS:
  ├── 23 public repositories — no consistent naming or structure
  ├── 18 repositories with default or placeholder READMEs
  ├── No licensing specified on 15 repositories
  ├── No description or topic tags on 20 repositories
  ├── Profile README: non-existent
  └── No commercial signals (sponsorship, licensing, collaboration terms)
```

**Solution Architecture**

```
REPOSITORY ECOSYSTEM REDESIGN:
  ├── Profile README: Operator-level trust architecture
  ├── Repository clustering: 5 flagship + supporting ecosystem
  ├── Naming convention: Consistent, signalling, memorable
  ├── README template: Threat posture · Architecture · Commercial terms
  ├── Licensing: MIT (open) + Commercial (restricted) split
  ├── GitHub Sponsors: Configured with 3-tier structure
  └── Topics + descriptions: Indexed for technical search

COMMERCIAL SIGNAL LAYER:
  ├── FUNDING.yml configured
  ├── Sponsorship tiers documented (Research · Integration · Advisory)
  ├── SECURITY.md with responsible disclosure process
  └── CONTRIBUTING.md with collaboration terms
```

**Outcome**

- Investor feedback post-rebuild: "Profile communicates exactly what you do"
- Seed round completed 6 weeks post-rebuild
- GitHub Sponsors: First sponsor within 14 days of configuration
- Profile stars: 3× increase over 60-day period

---

## `// ENG-04 · AI AUTOMATION GOVERNANCE`

```
SECTOR:          Professional Services (Legal-Adjacent)
PROBLEM CLASS:   Ungoverned Automation in a Regulated Environment
DURATION:        5 weeks (audit + framework + implementation)
```

**Problem Statement**

A professional services firm had deployed a suite of AI-assisted automation tools across their operations — document processing, client communication drafts, scheduling, and billing. The automation had been deployed by a junior engineer without governance design.

An internal audit found: no attribution of automated actions to named principals, no approval workflows for high-value automated actions, and audit log gaps that would be unacceptable under their sector's regulatory requirements.

**Governance Framework Implemented**

```
GOVERNANCE ARCHITECTURE:
  ├── Policy layer: Declarative YAML policies per automation workflow
  ├── Attribution: Every automated action linked to requesting principal
  ├── Approval gates: High-value actions (>£5k impact) require named approval
  ├── Audit log: Immutable, timestamped, exportable for regulatory review
  ├── Rollback: Defined procedures for every automated state change
  └── Human-in-the-loop: AI drafts flagged for human review before send

COMPLIANCE OUTPUT:
  ├── Audit log format approved by compliance team
  ├── Automation policy documentation for regulatory review
  └── Evidence package structure for annual audit
```

**Outcome**

- 100% of automated actions now attributed to named principals
- Zero ungated high-value automated actions
- Audit log coverage: 0% → 100% of automated workflow events
- Regulatory audit completed 4 months later — automation controls approved

---

## `// ENG-05 · SECURITY ARCHITECTURE REVIEW`

```
SECTOR:          Healthcare-Adjacent (Medical Devices)
PROBLEM CLASS:   Pre-Launch Security Posture Assessment
DURATION:        4 weeks (assessment + remediation roadmap)
```

**Problem Statement**

A medical device company was 6 weeks from a product launch involving a connected device with a cloud API backend. An internal review had not identified any significant security issues. An investor required an independent security architecture review before closing a Series A round.

**Assessment Findings**

```
CRITICAL FINDINGS (immediate pre-launch risk):
  ├── API authentication: Bearer tokens without expiry
  ├── Device communication: Unencrypted diagnostic data channel
  ├── Admin API: No rate limiting or brute-force protection
  ├── Secret management: Hardcoded API keys in mobile application binary
  └── Audit logging: Zero coverage of administrative actions

HIGH FINDINGS (post-launch remediation):
  ├── No input validation on device data ingestion endpoint
  ├── RBAC design allowed patient data cross-contamination
  ├── Backup encryption not implemented
  └── No penetration test of physical device interface

MDR / FDA 21 CFR PART 11 GAPS:
  ├── Electronic signature requirements not met
  ├── Audit trail requirements not met
  └── Access control documentation insufficient
```

**Remediation Roadmap**

```
PRE-LAUNCH (3 weeks):
  ├── Bearer token replacement with short-lived JWT (RS256)
  ├── Diagnostic channel encryption (TLS 1.3 mandatory)
  ├── Rate limiting on all authentication endpoints
  ├── Secret removal from binary + Vault integration
  └── Administrative audit log implementation

POST-LAUNCH (90 days):
  ├── Input validation framework
  ├── RBAC redesign
  ├── Backup encryption
  └── Physical device penetration test

COMPLIANCE REMEDIATION:
  ├── Electronic signature implementation
  ├── MDR audit trail documentation
  └── Access control policy documentation
```

**Outcome**

- 5 critical findings remediated before launch
- Series A closed — investor satisfied with remediation evidence
- MDR compliance submission completed 10 weeks post-engagement
- No security incidents in 18-month post-launch period

---

<div align="center">

```
╔═════════════════════════════════════════════════════════╗
║   To discuss a specific engagement:                     ║
║   📧 stefanowien777@gmail.com                           ║
║   📅 cal.com/ciprian-stefan-plesca                      ║
╚═════════════════════════════════════════════════════════╝
```

→ [Services](../SERVICES.md) · [Executive Profile](../EXECUTIVE-PROFILE.md) · [Contact](../CONTACT.md)

</div>
