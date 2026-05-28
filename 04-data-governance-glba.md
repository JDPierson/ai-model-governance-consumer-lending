# 04 — Data Governance & GLBA Compliance

> **The structural fact:** Consumer lending platforms receive nonpublic personal information (NPI) from consumers and third-party data sources. The Gramm-Leach-Bliley Act (GLBA) and the updated FTC Safeguards Rule (effective 2023) require a comprehensive information security program protecting that NPI — including through the vendor and data supply chain.

---

## Nonpublic Personal Information (NPI) in the AI Pipeline

### NPI Definition

NPI includes any personally identifiable financial information that a consumer provides to obtain a financial product or service, results from any transaction involving a financial product or service, or is obtained in connection with providing a financial product or service.

In consumer lending AI, NPI typically includes:
- Application data (income, employment, SSN, address)
- Credit bureau data pulled for underwriting
- Bank account / cash flow data
- Payment history
- Account balance and transaction data
- Decision outputs (approval, denial, terms)

### NPI Controls Through the AI Pipeline

| Pipeline Stage | Control Required | Evidence Artifact |
|---------------|-----------------|-------------------|
| Application data collection | Privacy notice delivered; consent documented | Privacy notice delivery log |
| Credit bureau pull | FCRA permissible purpose; access logged | Permissible purpose record; access log |
| Alternative data ingestion | Source classification; vendor agreement | Vendor agreement; data lineage log |
| Model input processing | Access controls; encryption in transit | Access control config; TLS certificate |
| Decision storage | Encryption at rest; access controls; tamper-evident | Encryption config; access log |
| Servicing records | GLBA retention compliance; access controls | Retention policy; access log |
| Data deletion | Certificate of destruction; documented process | Disposal log with certificate |

---

## FTC Safeguards Rule Requirements (2023 Update)

The updated FTC Safeguards Rule requires financial institutions subject to GLBA to implement a comprehensive information security program. Key requirements and their AI-specific implications:

### Required Program Elements

| Requirement | AI-Specific Implication | Evidence Artifact |
|------------|------------------------|-------------------|
| Designated qualified individual | Named owner of AI data governance | Appointment documentation |
| Risk assessment | AI-specific risk assessment covering model inputs, outputs, and data flows | Risk assessment document |
| Safeguards based on risk assessment | Technical controls for AI pipeline NPI | Control documentation |
| Regular testing / monitoring | Include AI model inputs/outputs in penetration testing and monitoring scope | Test results; monitoring logs |
| Employee training | AI data handling training for relevant staff | Training completion records |
| Vendor oversight | Service provider agreements for all NPI-handling vendors in AI pipeline | Vendor agreement inventory |
| Incident response plan | AI-specific incident scenarios included | IRP with AI scenarios |
| Annual reporting to board | AI governance included in annual security report | Board report |

### Vendor Oversight — Service Provider Agreements

Every vendor in the AI pipeline that receives NPI requires a service provider agreement with:
- Security and privacy obligations at least as protective as the platform's own program
- Audit rights
- Incident notification requirements
- Data return / destruction on termination

**AI pipeline vendors requiring service provider agreements:**

| Vendor Type | NPI Exposure | Agreement Required |
|------------|-------------|-------------------|
| Cloud infrastructure (AWS/GCP/Azure) | NPI stored in cloud | Yes — standard DPA/addendum |
| ML pipeline / training vendor | NPI in training data | Yes — data processing agreement |
| Credit bureau | Consumer credit data | Yes — FCRA compliant agreement |
| Alternative data provider | Consumer financial data | Yes — data licensing + security agreement |
| Model monitoring vendor | NPI may appear in input logs | Yes — if NPI-containing inputs logged |
| Analytics / BI platform | NPI in reporting | Yes — if NPI-containing reports |

---

## FCRA Compliance

Where credit bureau data or other consumer report data feeds the underwriting model:

### Permissible Purpose

Permissible purposes for pulling a consumer report include:
- In connection with a credit transaction involving the consumer
- Review of an existing account
- Written instruction of the consumer

**Document the permissible purpose for every credit report pull.** Impermissible pulls create FCRA liability.

### Accuracy Obligations

If the platform uses consumer report data, it has obligations when consumers dispute accuracy:
- Investigate disputes promptly (generally 30 days)
- Correct or delete inaccurate information
- Notify consumer reporting agencies of corrections

### Adverse Action Under FCRA

When a credit report is used in an adverse action decision, FCRA requires:
- Adverse action notice with name/address/phone of consumer reporting agency
- Statement of consumer's right to free credit report within 60 days
- Statement of right to dispute accuracy

This is in addition to (not instead of) the Reg B adverse action notice requirements.

---

## CCPA / CPRA — California Consumer Rights

For California consumers, the CCPA and CPRA add consumer rights obligations on top of GLBA:

| Right | Requirement | AI Implication |
|-------|-------------|----------------|
| Right to know | Disclose categories of NPI collected and purposes | AI input data categories in privacy policy |
| Right to delete | Delete NPI on request (with exceptions for legal obligations) | Deletion workflow that accounts for model training data |
| Right to opt out of sale | Do not sell NPI without opt-out opportunity | Data sharing arrangements with data brokers / alternative data providers |
| Right to limit sensitive NPI use | Limit use of sensitive NPI to necessary purposes | Sensitive data classification in AI inputs |
| Right to non-discrimination | Cannot deny credit for exercising CCPA rights | Document compliance |
| Automated decision-making | Regulations developing — monitor CPRA rulemaking | AI decision disclosure requirements emerging |

---

*Previous: [03 — Fairness & Disparate Impact Controls](./03-fairness-controls.md)*
*Next: [05 — Regulatory Mapping](./05-regulatory-mapping.md)*
