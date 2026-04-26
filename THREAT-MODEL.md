<div align="center">

```
╔══════════════════════════════════════════════════════════════════════╗
║               THREAT MODEL — FRAMEWORK & METHODOLOGY               ║
║               Ciprian Stefan Plesca // Xolo Go OÜ                  ║
╚══════════════════════════════════════════════════════════════════════╝
```

</div>

---

> Threat modelling is not a deliverable. It is a discipline.
> A threat model is not a document you produce at the end of a project.
> It is the lens through which every architecture decision is evaluated
> from the first conversation to the final deployment.

---

## `// THREAT MODELLING PHILOSOPHY`

Most security assessments answer the question: **"What vulnerabilities do we have?"**

Threat modelling answers a different question: **"What are we defending, against whom, and at what cost?"**

This distinction determines whether security investment is effective or theatrical.

```
VULNERABILITY ASSESSMENT LOGIC:
  Find vulnerabilities → Fix vulnerabilities → Repeat
  (Reactive · Infinite · Expensive · Never complete)

THREAT MODELLING LOGIC:
  Define assets → Define adversaries → Map attack paths
  → Implement controls proportional to risk → Verify
  (Proactive · Bounded · Cost-proportional · Auditable)
```

---

## `// THREAT MODELLING METHODOLOGY`

### Stage 1 · ASSET IDENTIFICATION

```
QUESTION: What are we protecting?

ASSET CATEGORIES:
  ├── Data Assets
  │   ├── Customer / user personal data (PII, SPII)
  │   ├── Business-critical data (financial, IP, strategic)
  │   ├── Credentials and secrets (API keys, certificates, passwords)
  │   └── Audit logs and evidence chains
  │
  ├── System Assets
  │   ├── Compute infrastructure (servers, containers, edge)
  │   ├── Network infrastructure (routing, DNS, firewall)
  │   ├── Application layer (APIs, frontends, internal tools)
  │   └── AI infrastructure (models, weights, inference endpoints)
  │
  └── Business Assets
      ├── Operational continuity (uptime, availability)
      ├── Regulatory standing (compliance status, certifications)
      ├── Reputation (customer trust, partner confidence)
      └── Intellectual property (code, models, documentation)
```

---

### Stage 2 · ADVERSARY PROFILING

```
QUESTION: Who might attack, and what do they want?

ADVERSARY CLASSES:
  ├── OPPORTUNISTIC THREAT ACTORS
  │   ├── Motivation: Low-effort financial gain
  │   ├── Capability: Script-kiddie to moderate
  │   ├── Target selection: Opportunistic (misconfigured, exposed)
  │   └── Countermeasure priority: Hardening + exposure reduction
  │
  ├── FINANCIALLY MOTIVATED ACTORS
  │   ├── Motivation: Ransomware, fraud, credential theft
  │   ├── Capability: Moderate to high
  │   ├── Target selection: Sector-specific (finance, healthcare)
  │   └── Countermeasure priority: Backup integrity + incident response
  │
  ├── INSIDER THREATS
  │   ├── Motivation: Financial, ideological, personal grievance
  │   ├── Capability: High (privileged access)
  │   ├── Target selection: Specific, high-value assets
  │   └── Countermeasure priority: Least privilege + audit logging
  │
  ├── NATION-STATE / APT
  │   ├── Motivation: Intelligence, disruption, IP theft
  │   ├── Capability: Very high / persistent
  │   ├── Target selection: Strategic value
  │   └── Countermeasure priority: Defence in depth + zero trust
  │
  └── SUPPLY CHAIN ADVERSARIES
      ├── Motivation: Scale (compromise one, affect many)
      ├── Capability: Varies
      ├── Target selection: High-value dependencies
      └── Countermeasure priority: Dependency governance + integrity verification
```

---

### Stage 3 · ATTACK SURFACE MAPPING

```
QUESTION: How could adversaries reach the assets?

ATTACK SURFACES:
  ├── EXTERNAL FACING
  │   ├── Web applications and APIs (authentication, injection, SSRF)
  │   ├── Email (phishing, BEC, malware delivery)
  │   ├── Remote access (VPN, RDP, SSH)
  │   └── Public repositories (secret exposure, dependency confusion)
  │
  ├── INTERNAL
  │   ├── Lateral movement opportunities (flat networks, shared credentials)
  │   ├── Privileged access abuse (admin accounts, service accounts)
  │   ├── Insider threat vectors (data exfiltration, sabotage)
  │   └── AI systems (prompt injection, model poisoning, output manipulation)
  │
  └── SUPPLY CHAIN
      ├── Third-party software dependencies (npm, pip, etc.)
      ├── SaaS integrations (data access, API keys)
      ├── Managed services (cloud providers, CDNs)
      └── Human supply chain (contractors, vendors, partners)
```

---

### Stage 4 · STRIDE ANALYSIS

For each identified attack surface, apply the STRIDE model:

```
S — SPOOFING
    Can an adversary falsely claim an identity?
    Controls: MFA, certificate pinning, mutual TLS, identity verification

T — TAMPERING
    Can an adversary modify data, code, or configuration?
    Controls: Integrity checksums, signed commits, immutable logs, RBAC

R — REPUDIATION
    Can an actor deny having performed an action?
    Controls: Audit logging, digital signatures, non-repudiation controls

I — INFORMATION DISCLOSURE
    Can an adversary access data they should not see?
    Controls: Encryption at rest/transit, access controls, DLP, data classification

D — DENIAL OF SERVICE
    Can an adversary disrupt service availability?
    Controls: Rate limiting, DDoS protection, circuit breakers, capacity planning

E — ELEVATION OF PRIVILEGE
    Can an adversary gain higher permissions than authorised?
    Controls: Least privilege, PAM, just-in-time access, privilege monitoring
```

---

### Stage 5 · RISK PRIORITISATION

```
RISK SCORE = LIKELIHOOD × IMPACT

LIKELIHOOD FACTORS:
  ├── Adversary capability (Low 1 / Medium 2 / High 3 / Critical 4)
  ├── Attack surface exposure (Unexposed 1 / Limited 2 / Exposed 3 / Open 4)
  └── Existing control effectiveness (Strong 0.25 / Moderate 0.5 / Weak 0.75 / None 1)

IMPACT FACTORS:
  ├── Data sensitivity (Public 1 / Internal 2 / Confidential 3 / Secret 4)
  ├── Operational impact (Negligible 1 / Minor 2 / Significant 3 / Catastrophic 4)
  └── Regulatory exposure (None 1 / Minor 2 / Significant 3 / Critical 4)

RISK TIERS:
  CRITICAL  (Score 9-16): Immediate remediation required
  HIGH      (Score 6-8):  Remediation within 30 days
  MEDIUM    (Score 3-5):  Remediation within 90 days
  LOW       (Score 1-2):  Accept or monitor with scheduled review
```

---

### Stage 6 · CONTROL IMPLEMENTATION

```
CONTROL TYPES (in order of preference):
  1. ELIMINATE   — Remove the attack surface entirely (most effective)
  2. REDUCE      — Minimise exposure (second choice)
  3. TRANSFER    — Shift risk to a better-positioned entity (third choice)
  4. ACCEPT      — Document the risk with a rationale (last resort)

NOTE: "Accept" is a business decision, not an engineering one.
      All accepted risks require named owner, review date, and rationale.
      "We don't have time" is not an acceptable rationale.
```

---

### Stage 7 · THREAT MODEL MAINTENANCE

```
TRIGGER CONDITIONS FOR THREAT MODEL REVIEW:
  ├── New system component added
  ├── Significant architecture change
  ├── New regulatory requirement
  ├── Security incident (internal or sector-relevant)
  ├── New adversary capability disclosed (CVE, threat intelligence)
  └── Annual scheduled review (minimum)

THREAT MODEL ARTEFACTS:
  ├── Asset register (maintained, dated, owner-attributed)
  ├── Adversary profiles (updated against current threat intelligence)
  ├── Attack surface map (version-controlled, reviewed on change)
  ├── STRIDE analysis per surface (documented in ADRs)
  ├── Risk register (scored, owner-attributed, dated)
  └── Control implementation status (linked to tickets/milestones)
```

---

## `// AI-SPECIFIC THREAT MODEL EXTENSIONS`

AI systems introduce threat vectors that do not exist in traditional software:

```
AI-SPECIFIC THREATS:
  ├── PROMPT INJECTION
  │   Definition: Adversarial input that manipulates model behaviour
  │   Impact: Data exfiltration, policy bypass, harmful output generation
  │   Controls: Input validation, output filtering, sandboxed execution
  │
  ├── MODEL POISONING
  │   Definition: Corruption of training data or fine-tuning pipeline
  │   Impact: Systematically biased or backdoored model behaviour
  │   Controls: Data provenance, training pipeline integrity, model testing
  │
  ├── INFERENCE ENDPOINT EXPOSURE
  │   Definition: Unauthorised access to AI inference API
  │   Impact: Cost amplification, data leakage, capability theft
  │   Controls: API authentication, rate limiting, usage monitoring
  │
  ├── DATA EXFILTRATION VIA LLM
  │   Definition: Using LLM as a channel to exfiltrate context data
  │   Impact: Sensitive data exposure through model outputs
  │   Controls: Output filtering, context isolation, data classification
  │
  └── SUPPLY CHAIN (WEIGHTS)
      Definition: Compromised pre-trained model weights
      Impact: Backdoored model with adversary-controlled behaviour
      Controls: Weight verification, trusted sources, behavioural testing
```

---

<div align="center">

```
╔══════════════════════════════════════════════════════════════════╗
║                                                                  ║
║   A threat model is not complete when it is written.             ║
║   It is complete when it is false — replaced by a better one.    ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

→ [Architecture Principles](ARCHITECTURE-PRINCIPLES.md) · [Philosophy](../PHILOSOPHY.md) · [Services](../SERVICES.md)

</div>
