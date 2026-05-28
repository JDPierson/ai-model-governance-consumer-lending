# 08 — ISO 42001 Alignment

## What Is ISO 42001?

ISO 42001 is the first international standard for Artificial Intelligence Management Systems (AIMS), published December 2023. It establishes requirements for organizations that develop, provide, or use AI systems — covering governance, risk management, transparency, and continuous improvement.

For consumer lending platforms, ISO 42001 matters because:

1. **Enterprise partner qualification** — institutional investors, bank partners, and enterprise customers are beginning to require ISO 42001 alignment as a condition of partnership
2. **Regulatory horizon** — CFPB and FTC are increasingly focused on AI accountability; ISO 42001 provides a defensible governance framework ahead of formal requirements
3. **EU AI Act** — consumer lending AI is classified as high-risk under the EU AI Act, which requires conformity assessments aligned with standards like ISO 42001 for EU market access

---

## ISO 42001 Requirements → Implementation Mapping

| ISO 42001 Requirement | What It Requires | Implementation | Status |
|----------------------|-----------------|----------------|--------|
| AI policy and governance | Documented organizational policy for AI | This framework as formal policy document | Draft — formalize |
| Leadership commitment | Executive accountability for AI governance | Named executive owner; governance committee | Action required |
| AI risk assessment | Identify and evaluate AI-specific risks | Section 05 regulatory mapping + Section 03 fairness analysis | Partial — formalize as risk register |
| Transparency and explainability | AI decisions explainable to affected parties | Section 02 reason code requirements; adverse action documentation | Partial — reason code build required |
| Bias and fairness | Controls to identify and mitigate unfair outcomes | Section 03 disparate impact testing program | Build required |
| Data governance | Data quality, lineage, and governance for AI inputs | Section 01 input classification + Section 04 GLBA governance | Partial — input audit required |
| Human oversight | Define where human oversight is required | Section 02 human review triggers and override procedures | Build required |
| Change management | Controlled process for AI system changes | Section 06 model change management | Build required |
| Incident management | Process for AI-related incidents | Section 06 model incident response | Build required |
| Continuous monitoring | Ongoing monitoring of AI performance | Section 03 fairness testing cadence + Section 07 evidence architecture | Build required |
| Third-party AI governance | Governance of AI in the supply chain | Section 04 vendor oversight (extend to non-NPI AI vendors) | Partial |
| Performance evaluation | Measure AI governance program effectiveness | Section 07 evidence review cadence | Partial — add ISO KPIs |

---

## ISO 42001 vs. Existing Compliance Programs

| ISO 42001 Gap Area | SOC 2 / NIST CSF Coverage | What's Missing |
|-------------------|--------------------------|----------------|
| AI risk assessment | CC3 risk assessment; NIST ID.RA | AI-specific and ECOA-specific risk register |
| Transparency / explainability | None | Reason code capability; decision documentation |
| Bias and fairness | None | Disparate impact testing methodology |
| AI incident response | CC7 incident management | AI model incident triggers and playbook |
| Human oversight | None explicit | Documented human review boundaries |
| AI supply chain governance | CC9 vendor risk | AI-specific vendor governance |

---

## ISO 42001 Implementation Roadmap

**Phase 1 — Foundation (Months 1-3)**
- Formalize this framework as official organizational policy
- Assign named executive owner and governance committee
- Complete input data classification audit (Section 01)
- Build reason code library and capability (Section 02)

**Phase 2 — Controls Build (Months 3-6)**
- Implement disparate impact testing methodology (Section 03)
- Complete vendor / service provider agreement audit and gap closure (Section 04)
- Build model change management process (Section 06)
- Implement model incident response playbook (Section 06)

**Phase 3 — Monitoring & Evidence (Months 6-9)**
- Implement continuous fairness monitoring architecture
- Complete first full evidence cycle under framework
- Extend AI vendor governance beyond NPI handlers
- First internal audit against ISO 42001

**Phase 4 — Certification Readiness (Months 9-12)**
- Gap assessment against full ISO 42001 standard
- Remediation of identified gaps
- External readiness assessment
- Certification audit

---

## EU AI Act — Consumer Lending Horizon

The EU AI Act classifies AI systems used to evaluate creditworthiness as **high-risk AI systems**. For platforms with EU consumer exposure:

| EU AI Act Requirement | Implication | Timeline |
|----------------------|-------------|---------|
| Conformity assessment | Third-party audit of AI system compliance | Phased — high-risk systems by 2026 |
| Technical documentation | Detailed documentation of AI system design and testing | Build now |
| Human oversight measures | Documented human oversight capability | Section 02 of this framework |
| Transparency to deployers | Information about AI system capabilities and limitations | AI system documentation |
| Accuracy and robustness | Testing and monitoring requirements | Section 03 and 06 of this framework |
| Registration | High-risk AI systems registered in EU database | Monitor for implementation guidance |

Building toward ISO 42001 certification now provides the governance foundation required for EU AI Act compliance.

---

*Previous: [07 — Evidence Architecture](./07-evidence-architecture.md)*
*Back to: [README](./README.md)*
