<div align="center">

```
╔══════════════════════════════════════════════════════════════════════╗
║            COLLABORATION — TERMS & CONTRIBUTION PROTOCOL            ║
║            Ciprian Stefan Plesca // Xolo Go OÜ                     ║
╚══════════════════════════════════════════════════════════════════════╝
```

</div>

---

## `// COLLABORATION PHILOSOPHY`

This ecosystem is not a community project. It is a professional technical practice with open-source components. Collaboration is selective, structured, and governed by the same engineering discipline that applies to every system in this ecosystem.

That said — if your contribution meets the bar, it will be welcomed, credited, and merged.

---

## `// CONTRIBUTION STANDARDS`

### What is accepted

```
✦ Bug reports with reproduction steps and environmental context
✦ Security vulnerability reports (see SECURITY.md first)
✦ Documentation corrections with source citations
✦ Performance improvements with benchmark evidence
✦ Feature proposals aligned with the repository's threat model
```

### What is not accepted

```
✗ Features that increase attack surface without proportional value
✗ Dependencies that introduce supply chain risk
✗ Changes that reduce audit trail capability
✗ "Simplifications" that bypass governance controls
✗ Style changes without functional substance
```

---

## `// CONTRIBUTION PROTOCOL`

### Step 1: Before opening an issue or PR

- Read the repository's README and PHILOSOPHY.md
- Verify your change aligns with the architecture principles in `docs/ARCHITECTURE-PRINCIPLES.md`
- For security-related contributions: read `SECURITY.md` before disclosing

### Step 2: Issues

Use the appropriate template. Provide:
- Clear title (not "bug" or "issue")
- Context: what you were doing, what you expected, what happened
- Environment: OS, version, relevant configuration
- Reproduction steps: numbered, specific, reproducible

### Step 3: Pull Requests

```
PR REQUIREMENTS:
  ├── Linked to an open issue (open the issue first)
  ├── Atomic: one concern per PR
  ├── Documented: update relevant docs alongside code changes
  ├── Clean: no debug output, commented-out code, or unrelated changes
  ├── Tested: evidence of testing in PR description
  └── Signed commits preferred (GPG signing)

PR TITLE FORMAT:
  [TYPE] Brief description
  Types: FIX / FEAT / DOCS / PERF / SECURITY / REFACTOR

EXAMPLE:
  [FIX] Correct audit log timestamp precision to millisecond
  [FEAT] Add role-based rate limiting to inference endpoint
  [DOCS] Update threat model with AI-specific vectors
```

---

## `// INTELLECTUAL PROPERTY`

By submitting a contribution, you agree that:

1. Your contribution is your original work or you have the right to submit it
2. You grant Xolo Go OÜ — Ciprian-Stefan Plesca a perpetual, irrevocable licence to use your contribution under the terms of this repository's licence
3. You have not included any third-party material that would restrict these rights
4. Your contribution does not introduce licence-incompatible dependencies

---

## `// RECOGNITION`

Significant contributors are acknowledged in:
- Repository commit history (always)
- CONTRIBUTORS.md (for substantive contributions)
- Public acknowledgement (at contributor's discretion)

---

## `// CODE OF CONDUCT`

This is a professional technical environment. The standard is simple:

**Engage as a professional.** Substantive, technical, respectful communication is the norm. Personal attacks, low-effort submissions, and noise are not tolerated and will result in removal from collaboration.

Questions are welcome. Sloppy questions cost everyone time — ask with context.

---

*Maintained by Ciprian Stefan Plesca / Xolo Go OÜ (EE102156920)*
*📧 stefanowien777@gmail.com · 🌐 localpulse.pro*
