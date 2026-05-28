# 05 — Regulatory Mapping

## Full Regulatory Surface Matrix

| Regulation | Applicability | Primary Risk | Key Obligation | Evidence Artifact |
|------------|--------------|--------------|----------------|-------------------|
| ECOA / Reg B | All AI credit decisions | Disparate impact; inadequate adverse action notices | Disparate impact testing; specific reason codes; 30-day notice | Fairness Testing Log; adverse action records |
| CFPB UDAAP | Consumer-facing decisioning and terms | Unfair, deceptive, or abusive AI practices | Plain language; consistent application; no hidden terms | Disclosure templates; term consistency audit |
| CFPB AI Supervisory Guidance | Algorithmic underwriting | Model explainability; reason code adequacy | Specific reason codes; human oversight documentation | Reason code library; override log |
| GLBA / FTC Safeguards Rule (2023) | NPI in AI pipeline | Unauthorized access to consumer financial data | Comprehensive information security program; vendor oversight | Security program documentation; vendor agreement inventory |
| FCRA | Credit bureau data as input | Impermissible purpose; adverse action deficiency | Permissible purpose; FCRA adverse action notice | Permissible purpose documentation; adverse action records |
| CCPA / CPRA | California consumer NPI | Consumer rights violations | Privacy notice; rights procedures; data sale opt-out | Privacy notice; consumer rights request log |
| NY DFS Cybersecurity Regulation | NY-chartered/licensed entities | Cybersecurity program deficiency | Cybersecurity program; incident reporting | Program documentation; incident reports |
| Illinois BIPA | Biometric data if used | Consent violations; private right of action | Written consent; retention limits | Consent records; retention policy |
| State AI Laws (CO, IL, TX, NY) | AI credit decisions | Disparate impact; inadequate disclosure | Impact assessments; bias testing; disclosure | Fairness tests; state-specific disclosures |
| Reg Z / TILA | If product is open-end credit (BNPL) | Disclosure deficiency | APR disclosure; billing rights | Disclosure records |
| FDCPA | Delinquent account servicing | Improper debt collection communications | Communication rules; dispute rights | Servicing communication log |
| ISO 42001 | AI Management System | Enterprise partner qualification | AI governance framework; risk management | This framework; fairness logs; change log |
| EU AI Act (horizon) | High-risk AI for EU consumers | Non-compliance with conformity assessment | Impact assessment; transparency; human oversight | Impact assessment; this framework |

---

## State Licensing Matrix Framework

Consumer lending platforms may trigger licensing requirements that vary by state and product type:

| License Type | Trigger | Key States |
|-------------|---------|-----------|
| Consumer Lender / Finance Company License | Making consumer loans | Most states |
| Money Transmitter License | Transmitting funds | Most states |
| Debt Collector License | Collecting delinquent accounts | Most states |
| Credit Services Organization | Arranging credit for others | Select states |
| Mortgage Broker / Lender | If mortgage products offered | All states — federal + state |
| Student Loan Servicer License | Student loan servicing | CA, IL, MD, WA, and others |

**Recommended approach:**
1. Legal memo for each state of operation before launch
2. Living licensing matrix: state, license type, number, expiration, renewal lead time, owner
3. Quarterly review and before any geographic expansion
4. Monitor state legislative activity for new requirements

---

*Previous: [04 — Data Governance & GLBA Compliance](./04-data-governance-glba.md)*
*Next: [06 — Model Change Management & Incident Response](./06-change-management-incident-response.md)*
