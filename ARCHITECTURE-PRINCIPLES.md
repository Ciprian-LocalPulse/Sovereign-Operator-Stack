<div align="center">

```
╔══════════════════════════════════════════════════════════════════════╗
║            ARCHITECTURE PRINCIPLES — ENGINEERING AXIOMS             ║
║            Ciprian Stefan Plesca // Xolo Go OÜ                     ║
╚══════════════════════════════════════════════════════════════════════╝
```

</div>

---

> These principles are not preferences.
> They are the engineering laws that govern every system built under this practice.
> Systems that violate these principles are not accepted as engagements.

---

## `// PRINCIPLE SET`

---

### P-01 · SOVEREIGNTY BEFORE CONVENIENCE

```
PRINCIPLE:
  No critical capability may depend on infrastructure that cannot be
  owned, controlled, and operated independently of the vendor.

IMPLICATION:
  Every system is designed to function in a degraded external dependency
  environment. Sovereign operation is the baseline, not the fallback.

VIOLATION PATTERN:
  "We use Vendor X for this — it works great and we can't run without it."
  This is a trust transfer, not a capability. Identify it and engineer around it.

CORRECT PATTERN:
  External services are integrations, not dependencies.
  You can use them. You cannot require them.
```

---

### P-02 · THREAT MODEL PRECEDES DESIGN

```
PRINCIPLE:
  No system may be designed before its threat model is documented.
  Architecture without a threat model is optimism dressed as engineering.

IMPLICATION:
  Every engagement begins with: Who are the adversaries? What are the assets?
  What are the attack vectors? What are the acceptable failure modes?

THREAT MODELLING FRAMEWORK:
  ├── STRIDE  — Spoofing, Tampering, Repudiation, Info Disclosure, DoS, Elevation
  ├── PASTA   — Process for Attack Simulation and Threat Analysis
  └── LINDDUN — Linkability, Identifiability, Non-repudiation, Detectability,
                Disclosure, Unawareness, Non-compliance

VIOLATION PATTERN:
  "We'll add security once we've built the MVP."
  Security retrofitted is security theatre.
```

---

### P-03 · IDENTITY IS THE PERIMETER

```
PRINCIPLE:
  Access decisions are made on verified identity + device posture +
  contextual policy — never on network location alone.

IMPLICATION:
  Internal networks are not trusted. Remote access via VPN is not sufficient.
  Every access request requires: authentication, authorisation, and audit.

IMPLEMENTATION:
  ├── Every principal has a unique, non-shared identity
  ├── Every device has a verifiable trust posture before access is granted
  ├── Every access decision is logged with sufficient metadata
  └── Access rights are reviewed and recertified on a defined schedule

VIOLATION PATTERN:
  "If you're on the VPN, you can access the internal systems."
  This is a 2003 security model. The threat landscape has changed.
```

---

### P-04 · AUDIT BY DEFAULT

```
PRINCIPLE:
  Every significant system action produces an immutable, timestamped log entry.
  Logging is not a feature. It is a design constraint.

IMPLICATION:
  If you cannot reconstruct the state of a system at any point in time from its
  logs, the system does not meet minimum governance standards.

LOG ENTRY REQUIREMENTS:
  ├── Actor         — Who performed the action (named principal, not "system")
  ├── Action        — What was done (specific, not generic)
  ├── Target        — What was affected
  ├── Timestamp     — When (UTC, millisecond precision)
  ├── Outcome       — Success or failure with reason
  └── Context       — Sufficient metadata for forensic reconstruction

VIOLATION PATTERN:
  "We log errors." Error logs are not audit logs. Audit logs record everything.
```

---

### P-05 · LEAST PRIVILEGE AT EVERY LAYER

```
PRINCIPLE:
  Every component, service, user, and automated process receives only the
  permissions required to perform its defined function — nothing more.

IMPLICATION:
  Overpermissioning is a vulnerability. Admin accounts used for routine
  operations are a design flaw, not a convenience.

IMPLEMENTATION LAYERS:
  ├── Network     — Components communicate only on required ports and protocols
  ├── Identity    — Users access only what their role requires
  ├── Service     — APIs expose only what is required for integration
  ├── Data        — Processes access only the data fields they need
  └── Automation  — Automated actions are bounded by explicit policy

VIOLATION PATTERN:
  "It's easier to give admin access — we can restrict later."
  Permissions, once granted, are rarely revoked.
```

---

### P-06 · FAIL SECURE

```
PRINCIPLE:
  When a system fails, it must fail in the direction of security — denying
  access rather than granting it, stopping rather than continuing.

IMPLICATION:
  Every failure mode must be identified, tested, and documented.
  An undocumented failure mode is an undocumented attack vector.

FAILURE MODE CATALOGUE (per system):
  ├── What happens when authentication fails?
  ├── What happens when a dependent service is unavailable?
  ├── What happens when storage is full?
  ├── What happens when network partitions occur?
  └── What happens when configuration is invalid?

VIOLATION PATTERN:
  "If the auth service is down, we fall back to local access."
  This is a secure system with an insecure bypass. The bypass is the vulnerability.
```

---

### P-07 · ZERO EXTERNAL TRUST

```
PRINCIPLE:
  All external dependencies — APIs, packages, services, CDNs, SaaS platforms —
  are treated as untrusted until explicitly validated.

IMPLICATION:
  Supply chain security is not a separate consideration.
  It is embedded in every dependency decision.

DEPENDENCY GOVERNANCE:
  ├── Every external package has a verified author and licence
  ├── Package integrity is verified at install time (lockfiles, hashes)
  ├── External APIs have documented data handling and retention policies
  ├── CDN dependencies have fallback strategies
  └── SaaS platforms have documented exit strategies

VIOLATION PATTERN:
  "We use an npm package for this — it has 10M weekly downloads so it must be safe."
  Popularity is not a security guarantee. xz-utils had millions of users.
```

---

### P-08 · COMPLIANCE AS ENGINEERING

```
PRINCIPLE:
  Regulatory compliance requirements are engineering constraints,
  not documentation exercises. They are implemented in code, not in Word documents.

IMPLICATION:
  GDPR data retention policies are enforced by automated deletion jobs —
  not by a policy document in a shared drive.
  NIS2 incident response requirements are implemented in runbooks —
  not acknowledged in a risk register.

FRAMEWORKS OPERATED AGAINST:
  ├── ISO/IEC 27001    — Information security management
  ├── NIST CSF 2.0     — Cybersecurity framework
  ├── GDPR (EU)        — Data protection & privacy
  ├── NIS2 (EU)        — Network & information systems security
  ├── DORA (EU)        — Digital operational resilience
  └── CIS Benchmarks   — Secure configuration baselines

VIOLATION PATTERN:
  "We're GDPR compliant — we have a privacy policy."
  A privacy policy is a legal document. GDPR compliance is an engineering discipline.
```

---

### P-09 · DOCUMENTATION IS ARCHITECTURE

```
PRINCIPLE:
  Documentation that does not match the system's actual behaviour is
  a security liability, not a compliance asset.

IMPLICATION:
  Architecture diagrams are maintained as living documents.
  Runbooks are tested, not filed.
  READMEs describe what the system does, not what it was intended to do.

DOCUMENTATION HIERARCHY:
  ├── Architecture Decision Records (ADRs) — why decisions were made
  ├── System architecture diagrams        — what was built
  ├── Threat model documentation          — what was considered
  ├── Operational runbooks                — how to operate and recover
  └── Incident response playbooks         — what to do when it fails

VIOLATION PATTERN:
  "The documentation is a bit out of date — the engineers know how it works."
  Undocumented systems cannot be audited, transferred, or secured.
```

---

### P-10 · COMMERCIAL READINESS IS A SECURITY PROPERTY

```
PRINCIPLE:
  A system that cannot survive technical due diligence is a system with
  hidden liabilities — security, legal, or operational.

IMPLICATION:
  Every system is built as if an acquirer will review it next week.
  Licensing is clear. Dependencies are documented. Secrets are not in repositories.
  Architecture decisions are recorded. Compliance posture is demonstrable.

COMMERCIAL READINESS CHECKLIST:
  ├── No secrets, credentials, or PII in version history
  ├── Licence is specified and commercially appropriate
  ├── All dependencies are listed with versions and licences
  ├── Architecture is documented and matches implementation
  ├── Security controls are documented and testable
  └── Compliance posture is demonstrable without supplemental briefings

VIOLATION PATTERN:
  "We'll clean this up before the due diligence."
  Technical due diligence finds what you didn't clean up.
```

---

<div align="center">

```
╔══════════════════════════════════════════════════════════════════╗
║                                                                  ║
║   These principles are not aspirational.                         ║
║   They are operational constraints applied to every system       ║
║   built under this practice.                                     ║
║                                                                  ║
║   Engagements that require violating them are not accepted.      ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

→ [Philosophy](../PHILOSOPHY.md) · [Threat Model](THREAT-MODEL.md) · [Services](../SERVICES.md)

</div>
