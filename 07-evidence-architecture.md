# 07 — Evidence Architecture

> **Design principle:** Compliance evidence should be the natural output of well-designed operational processes — not a separate documentation effort. Every model decision generates a structured log that is simultaneously the operational record and the regulatory defense artifact.

---

## Evidence Architecture Table

| Compliance Requirement | Evidence Type | Frequency | System of Record | Owner | Artifact Format | Retention |
|------------------------|--------------|-----------|-----------------|-------|-----------------|-----------|
| ECOA disparate impact | Fairness Testing Log | Monthly + on change | Compliance | Compliance | Signed PDF with data table | Indefinite |
| Reg B adverse action | Notice log + notice copies | Per event | Compliance / Legal | Compliance | Notice copy + delivery confirmation | 25 months (Reg B minimum) |
| FCRA permissible purpose | Permissible purpose log | Per credit pull | Engineering / Compliance | Engineering | Structured log | Duration of relationship + 2 years |
| GLBA privacy notice | Notice delivery log | Per consumer + on change | Compliance | Compliance | Notice copy + delivery confirmation | Duration of relationship |
| FTC Safeguards Rule | Information security program documentation | Annual + on change | GRC | Compliance / Security | Program document (versioned) | Indefinite |
| Vendor oversight | Service provider agreement inventory | On change + annual review | Legal / Compliance | Legal | Agreement inventory + executed agreements | Duration + 2 years |
| Model decision | Decision log | Per decision | Engineering | Engineering | Immutable JSONL | 25 months minimum |
| Model change management | Change log with sign-off | Per change | Compliance / Engineering | Compliance | Change log + sign-off | Indefinite |
| Proxy variable analysis | Proxy variable mapping | Annual + on model change | Compliance | Compliance | Analysis document | Indefinite |
| Fairness testing | Fairness Test Log | Monthly + on change | Compliance | Compliance | Signed PDF | Indefinite |
| Override log | Override log with rationale | Per override | Compliance | Compliance | Structured log | 25 months minimum |
| CCPA consumer rights | Consumer rights request log | Per request | Compliance | Compliance | Request + response log | 2 years |
| State breach notification | Breach incident record | Per incident | Legal / Compliance | Compliance | Incident record + notification copies | Indefinite |
| ISO 42001 AI governance | This framework + supporting logs | Annual + on change | Compliance | Compliance | This document (versioned) | Indefinite |
| Reason code library | Reason code documentation | On change | Compliance | Compliance | Versioned document | Indefinite |

---

## Evidence Review Cadence

| Evidence Type | Cadence | Reviewer | Artifact |
|---------------|---------|---------|---------|
| Fairness test results | Monthly | Compliance + Data Science | Signed review log |
| Adverse action notice sample | Quarterly | Compliance | Sample audit report |
| Decision log integrity | Quarterly | Engineering + Compliance | Integrity check report |
| Vendor agreement inventory | Annual + on change | Legal + Compliance | Updated inventory |
| Override patterns | Quarterly | Compliance | Pattern analysis report |
| Proxy variable mapping | Annual + on model change | Compliance | Updated mapping |
| State licensing matrix | Annual + pre-expansion | Legal | Updated matrix |
| ISO 42001 framework | Annual | Compliance + Legal + Data Science | Updated framework version |

---

*Previous: [06 — Model Change Management & Incident Response](./06-change-management-incident-response.md)*
*Next: [08 — ISO 42001 Alignment](./08-iso-42001-alignment.md)*
