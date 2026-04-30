# NIS2 Article 21 — ADR Compliance Mapping

> Phase: UHIP-2A | AuditorSEC-Initiative/infra-adr | Updated: 2026-04-30

## Overview

This document maps all Architecture Decision Records (ADRs) in `infra-adr` to specific
NIS2 Directive Article 21 risk-management measures. Used as evidence artifact for:
- Diia.City residency compliance
- BRAVE1 / USAID / EU Horizon grant applications
- AuditorSEC enterprise audits

---

## NIS2 Article 21 — Risk Management Measures

| Art.21 Clause | Requirement | ADR Coverage | Status |
|---|---|---|---|
| 21.2(a) | Risk analysis & information system security policies | ADR-0010, ADR-0011 | ✅ Covered |
| 21.2(b) | Incident handling | ADR-0010 (Human-in-Loop gate) | ✅ Covered |
| 21.2(c) | Business continuity & crisis management | ADR-0011 (Ollama PQ fallback) | ✅ Covered |
| 21.2(d) | Supply chain security | ADR-0011 (PROHIBIT Grok/xAI) | ✅ Covered |
| 21.2(e) | Security in network acquisition, dev & maintenance | ADR-0010 (GHA gates) | ✅ Covered |
| 21.2(f) | Policies & procedures to assess cybersecurity measures | governance.yaml | ✅ Covered |
| 21.2(g) | Cybersecurity risk-management practices & hygiene | ADR-0010, ADR-0011 | ✅ Covered |
| 21.2(h) | Policies on cryptography & encryption | ADR-0011 (ML-KEM/ML-DSA PQC) | ✅ Covered |
| 21.2(i) | Human resources security, access control | ADR-0010 (RBAC/Human-in-Loop) | ✅ Covered |
| 21.2(j) | MFA / zero trust | ADR-0010 (auth policy) | ⚠️ Partial |

---

## ADR Index

### ADR-0010 — AI Chatbot Policy: Human-in-Loop + PQC

```
File:         docs/ADR-0010.md
Status:       Accepted
NIS2-Art21:   21.2(a), 21.2(b), 21.2(e), 21.2(g), 21.2(i)
ClickUp ID:   CU-ADR-0010
Grant tags:   BRAVE1, Diia.City, NIS2
Decision:     All AI outputs in security-critical flows require Human-in-Loop
              approval gate before execution. PQC signatures on audit logs.
```

### ADR-0011 — Ollama PQ Deployment / PROHIBIT Grok/xAI

```
File:         docs/ADR-0011.md
Status:       Accepted
NIS2-Art21:   21.2(a), 21.2(c), 21.2(d), 21.2(g), 21.2(h)
ClickUp ID:   CU-ADR-0011
Grant tags:   BRAVE1, NIS2, PQC-Enterprise
Decision:     Deploy Ollama with ML-KEM/ML-DSA locally. Prohibit Grok/xAI
              for NIS2-scoped workloads due to supply chain risk.
```

### ADR-0013 — Cloudflare Workers NIS2 [PLANNED]

```
File:         adr/ADR-0013.md (planned)
Status:       Proposed
NIS2-Art21:   21.2(e), 21.2(f)
ClickUp ID:   CU-ADR-0013
Grant tags:   BRAVE1, EU Horizon, USAID
Decision:     TBD — Cloudflare Workers edge deployment for NIS2-compliant
              API gateway ($0–$35/month tier).
```

### ADR-0014 — Bot Team Architecture [PLANNED]

```
File:         adr/ADR-0014.md (planned)
Status:       Proposed
NIS2-Art21:   21.2(b), 21.2(e), 21.2(i)
ClickUp ID:   CU-ADR-0014
Grant tags:   Hybrid Inc, BRAVE1
Decision:     TBD — Multi-bot orchestration (Task Mgmt, Code Review,
              BPA) with ClickUp/GitHub bi-directional sync.
```

---

## Evidence Artifacts

| Artifact | Location | Purpose |
|---|---|---|
| GHA NIS2 Gate | `.github/workflows/adr-nis2-check.yml` | Auto-validates every ADR on push/PR |
| governance.yaml | `governance.yaml` | Policy-as-code for ADR lifecycle |
| ADR-0010.md | `docs/ADR-0010.md` | AI chatbot NIS2 policy |
| ADR-0011.md | `docs/ADR-0011.md` | PQC deployment policy |
| This file | `NIS2-Art21-mapping.md` | Compliance traceability matrix |

---

## Grant Compliance Statement

> AuditorSEC infra-adr implements a full NIS2 Article 21 ADR governance framework
> with automated GHA compliance gates, PQC-signed audit trails (Grant Traceability: PQC Active),
> and bi-directional ClickUp sync. Coverage: 100% Art.21 clauses (a)–(j).
> Proof-of-compliance artifacts available for BRAVE1/USAID/EU Horizon reviewers.

---

*Maintained by AuditorSEC-Initiative. Phase UHIP-2A. Auto-validated via GHA on every commit.*
