# AI Model Governance & Decision Substantiation Framework
## Consumer Lending & Fintech Platforms

> **Role context:** Designed as Head of Compliance thinking through AI governance architecture for consumer lending and fintech platforms that use AI/ML underwriting engines to make credit decisions. No prior AI governance framework existed for this intersection of ECOA, CFPB, GLBA, and ISO 42001. Everything below was designed from first principles against the applicable regulatory surface.

---

## Overview

This repository documents a compliance architecture framework for AI-powered consumer lending platforms — specifically those that use machine learning underwriting engines to make credit decisions for consumers across products including:

- Buy Now Pay Later (BNPL)
- Personal loans and lines of credit
- Auto financing
- Student lending
- Earned wage access (EWA)
- Marketplace lending platforms

The framework addresses a critical gap in published compliance guidance: most AI governance frameworks address ECOA fairness **or** data privacy **or** model risk management in isolation. Consumer lending platforms face all three simultaneously — and the interaction effects between algorithmic credit decisioning, consumer financial protection law, and emerging AI governance standards create unique compliance surface area that generic frameworks don't address.

---

## Problem Statement

AI-powered consumer lending sits at a uniquely complex regulatory intersection:

**ECOA / Reg B** — AI-driven credit decisions must not have disparate impact on protected classes. The model must generate human-readable reason codes for every adverse decision. "The algorithm decided" is not a compliant explanation.

**CFPB oversight** — UDAAP risk applies to any AI decisioning that is unfair, deceptive, or abusive. The CFPB has issued supervisory guidance on algorithmic underwriting and has made clear that complexity does not exempt lenders from adverse action notice requirements.

**GLBA / FTC Safeguards Rule** — Consumer financial data used in AI underwriting is subject to the Gramm-Leach-Bliley Act and the updated FTC Safeguards Rule (effective 2023), which requires a comprehensive information security program protecting nonpublic personal information (NPI).

**FCRA** — Where credit bureau data feeds the underwriting model, the Fair Credit Reporting Act governs permissible purpose, accuracy, and adverse action requirements.

**ISO 42001** — The first international AI Management Systems standard (December 2023) is increasingly required by enterprise partners, investors, and regulators as evidence of responsible AI governance. Consumer lending platforms using AI underwriting are precisely the systems this standard targets.

**State law overlay** — CCPA/CPRA (California), New York DFS cybersecurity regulation, Illinois BIPA (if biometric data), and a growing patchwork of state AI and consumer protection laws create a 50-state compliance surface.

The compliance challenge: **the evidence that proves each of these obligations is being met must be the natural output of the operational system, not a separate documentation effort.** This framework designs that evidence architecture from the ground up.

---

## Framework Structure

| Section | Contents |
|---------|----------|
| [01 — Model Purpose & Scope](./01-model-purpose-scope.md) | Decision types, data input classification by regulatory treatment, out-of-scope definitions, product-specific considerations |
| [02 — Decision Flow Documentation](./02-decision-flow.md) | Stage-by-stage compliance checkpoints, human review triggers, override procedures, reason code requirements |
| [03 — Fairness & Disparate Impact Controls](./03-fairness-controls.md) | Protected class mapping, proxy variable analysis, disparate impact testing methodology, Reg B adverse action requirements, continuous monitoring architecture |
| [04 — Data Governance & GLBA Compliance](./04-data-governance-glba.md) | NPI classification, FTC Safeguards Rule requirements, FCRA permissible purpose, data lineage, subcontractor chain governance |
| [05 — Regulatory Mapping](./05-regulatory-mapping.md) | Full matrix: ECOA/Reg B, CFPB UDAAP, GLBA/FTC Safeguards, FCRA, state laws, ISO 42001, EU AI Act horizon |
| [06 — Model Change Management & Incident Response](./06-change-management-incident-response.md) | Change review process, model incident triggers, response playbook, regulatory notification obligations |
| [07 — Evidence Architecture](./07-evidence-architecture.md) | Evidence type, frequency, system of record, and artifact format for every compliance requirement |
| [08 — ISO 42001 Alignment](./08-iso-42001-alignment.md) | Standard requirements mapped to framework sections with implementation status and certification roadmap |

---

## Regulatory Surface Summary

| Regulation | Applicability | Primary Risk |
|------------|--------------|--------------|
| ECOA / Reg B | AI credit decisions across all product types | Disparate impact on protected classes; adverse action notice requirements |
| CFPB UDAAP | Consumer-facing terms, decisioning, and servicing | Unfair, deceptive, or abusive AI-driven practices |
| CFPB Supervisory Guidance on AI | Algorithmic underwriting and adverse action | Model explainability; reason code adequacy |
| GLBA / FTC Safeguards Rule (2023) | NPI used in underwriting and servicing | Information security program; vendor oversight; incident response |
| FCRA | Credit bureau data as underwriting input | Permissible purpose; accuracy; adverse action |
| CCPA / CPRA | California consumer data | Consumer rights; data sale restrictions; sensitive data handling |
| NY DFS Cybersecurity Regulation | NY-chartered or licensed entities | Cybersecurity program requirements; incident reporting |
| Illinois BIPA | Biometric data (if used) | Consent; retention limits; private right of action |
| State AI Laws (emerging) | CO, TX, IL, and others with AI bias requirements | Disparate impact testing; impact assessments |
| ISO 42001 | AI Management System | Enterprise partner qualification; responsible AI governance |
| EU AI Act (horizon) | High-risk AI systems for EU consumers | Conformity assessment; transparency; human oversight |

---

## Key Design Principles

**1. Evidence as operational output**
Every compliance artifact is designed as the natural output of a well-designed operational process. Decision logs, fairness test results, and change records are generated automatically and are simultaneously the operational record and the regulatory defense artifact.

**2. Reason codes are not optional**
The CFPB has made clear that AI complexity does not exempt lenders from Reg B adverse action notice requirements. The model must generate specific, human-readable reason codes for every adverse decision. This framework treats reason code capability as a foundational requirement, not a feature.

**3. Proxy variables are the primary fairness risk**
The greater compliance risk in AI underwriting is not direct use of protected class data but proxy variables — facially neutral inputs that correlate with protected class membership. This framework requires documented proxy variable analysis for every input variable.

**4. The subcontractor chain is a first-class compliance obligation**
GLBA and the FTC Safeguards Rule require vendor oversight programs that extend through the data supply chain. Any vendor receiving nonpublic personal information requires a service provider agreement with appropriate security and privacy obligations.

**5. Fairness testing is continuous, not periodic**
Disparate impact in AI underwriting doesn't announce itself. This framework requires monthly fairness testing on production models and immediate testing on any model change — generating a documented evidence trail that regulators and auditors can examine.

**6. ISO 42001 as the governance horizon**
The framework is designed with ISO 42001 certification as the target state. Enterprise partners and regulators are increasingly requiring AI governance certification. Building toward the standard from day one is more efficient than retrofitting.

---

## Product-Specific Considerations

### Buy Now Pay Later (BNPL)
BNPL has been a CFPB priority since 2022. Key considerations:
- CFPB has indicated BNPL products may be subject to Reg Z (Truth in Lending) requirements
- Repeat use patterns and data sharing between BNPL providers create unique FCRA questions
- CFPB supervisory spotlight means heightened UDAAP scrutiny

### Earned Wage Access (EWA)
- Regulatory classification unsettled — some states treat EWA as lending; others as wage payment
- CFPB has issued guidance treating some EWA products as consumer credit
- State-by-state analysis required before deployment

### Marketplace Lending
- True lender doctrine — ensure the platform, not just the bank partner, is analyzing its compliance obligations
- Bank partner agreement must address AI underwriting standards and ECOA compliance
- Secondary market investors may require compliance representations

---

## Relationship to Existing Compliance Programs

Platforms with mature SOC 2 + NIST CSF programs have significant coverage of the FTC Safeguards Rule requirements already in place. The genuine build items for a consumer lending AI program are concentrated in areas that SOC 2 and NIST CSF don't address:

- AI fairness testing and adverse action documentation (ECOA/Reg B-specific)
- Reason code capability (CFPB-specific)
- Proxy variable analysis (ECOA-specific)
- ISO 42001 AI governance (emerging standard)
- Consumer rights procedures (FCRA/CCPA-specific)
- GLBA privacy notice and opt-out procedures

This framework is designed to sit alongside — not replace — an existing SOC 2 / NIST CSF program.

---

## Related Framework

For healthcare fintech platforms operating at the intersection of HIPAA, patient financing, and AI underwriting, see the companion framework:
[AI Model Governance — Healthcare Fintech](https://github.com/JDPierson/ai-model-governance-healthcare-fintech)

---

## Contact

**James Pierson**
Compliance & GRC Executive | Open to opportunities
[LinkedIn: linkedin.com/in/jpierson] · [jpierson@seanet.com]

> *This repository is a generalized compliance architecture framework. No proprietary data, customer information, or platform-specific details are included. Regulatory analysis and framework design are original work.*
