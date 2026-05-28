# 01 — Model Purpose & Scope

## What the AI Underwriting Model Does

AI-powered consumer lending platforms use machine learning engines to make credit decisions across a range of product types. The compliance obligations vary by decision type — the first task is precisely defining what decisions the model makes.

### Decision Type Inventory

| Decision Type | Description | Primary Regulatory Framework |
|--------------|-------------|------------------------------|
| Credit approval | Does the consumer qualify for credit? | ECOA / Reg B; FCRA |
| Credit limit setting | What credit limit is appropriate? | ECOA / Reg B |
| Pricing / rate setting | What interest rate or fee applies? | ECOA / Reg B; CFPB UDAAP |
| Adverse action | Why was credit denied or terms worse than requested? | ECOA / Reg B — reason codes required |
| Credit line increase / decrease | Should existing credit be adjusted? | ECOA / Reg B |
| Account suspension / closure | Should an account be restricted? | ECOA / Reg B |
| Collections / workout terms | What repayment arrangement is offered? | CFPB UDAAP; FDCPA if in collections |
| Fraud scoring | Is this transaction or application fraudulent? | FCRA if using credit report data |

Each decision type must be individually analyzed. A model that makes approval decisions and pricing decisions simultaneously may have different disparate impact profiles for each — they must be tested separately.

---

## Data Input Classification

Every input variable in the underwriting model must be classified by its regulatory treatment before deployment. This is the foundational compliance task — it determines which obligations apply and what evidence must be maintained.

### Input Classification Framework

| Input Category | Regulatory Treatment | Compliance Obligation | Evidence Required |
|----------------|---------------------|----------------------|-------------------|
| Credit bureau data (tradelines, scores, inquiries) | FCRA-regulated | Permissible purpose required; adverse action notice if used in denial | Permissible purpose documentation; FCRA adverse action notice |
| Income / employment data | ECOA proxy risk (income correlates with protected classes) | Proxy variable analysis; document business necessity | Proxy variable mapping |
| Geographic data (ZIP code, address) | High ECOA proxy risk (race, national origin) | Proxy variable analysis; census tract demographic correlation analysis | Proxy variable mapping; fairness test results |
| Demographic data | ECOA — protected class | Cannot use race, color, religion, national origin, sex, marital status, age, receipt of public assistance | Input exclusion documentation |
| Payment history (non-credit bureau) | FCRA if from consumer reporting agency | Source determines treatment; document each source | Data lineage log |
| Bank account / cash flow data | GLBA NPI if from financial institution | Service provider agreement required; FTC Safeguards Rule applies | Vendor agreement; data lineage |
| Alternative data (rent, utilities, subscriptions) | FCRA if from consumer reporting agency; ECOA proxy risk | Source classification; proxy variable analysis | Data lineage; proxy variable mapping |
| Device / behavioral data | State privacy laws (CCPA, etc.); ECOA proxy risk | Privacy notice; proxy variable analysis | Privacy notice; proxy variable mapping |
| Biometric data (if used) | Illinois BIPA; state biometric laws | Consent; retention limits | Consent records; retention policy |
| Social media / public data | ECOA proxy risk; state privacy laws | Proxy variable analysis; privacy notice | Proxy variable mapping |

### The Alternative Data Question

Alternative data — rent payment history, utility payments, subscription data, cash flow patterns — is increasingly used in AI underwriting to expand credit access. The compliance analysis is nuanced:

1. **FCRA classification:** If the data comes from a consumer reporting agency, FCRA applies. If collected directly, FCRA may not apply but ECOA and state privacy laws still do.
2. **Proxy variable risk:** Alternative data sources often correlate strongly with race, national origin, and income — requiring rigorous proxy variable analysis.
3. **CFPB position:** The CFPB has expressed support for responsible use of alternative data to expand credit access, while emphasizing that ECOA compliance is non-negotiable.
4. **Documentation requirement:** Document the business necessity for each alternative data source and the proxy variable analysis conducted before deployment.

---

## What Is Explicitly Out of Scope

| Out-of-Scope Item | Why It Matters |
|-------------------|---------------|
| Employment decisions | ECOA protections heightened; confirm model outputs not used by downstream parties for employment |
| Insurance underwriting | Separate regulatory framework; document explicitly if platform touches insurance-adjacent products |
| Tenant screening | FCRA applies; separate adverse action requirements; document if platform data used for tenant screening |
| Government benefit eligibility | Separate regulatory framework; document explicitly |

---

## Product-Specific Scope Considerations

### BNPL
- Determine whether product is subject to Reg Z (Truth in Lending) — CFPB has signaled BNPL products may qualify as credit cards under Reg Z
- Document the regulatory classification analysis and legal sign-off
- Repeat use data and cross-platform data sharing create FCRA questions — document data sharing arrangements

### Earned Wage Access
- State-by-state regulatory classification required before deployment
- Document whether product is structured as a loan, wage advance, or other product in each state
- CFPB supervisory guidance treats some EWA products as consumer credit — monitor for updates

### Marketplace Lending / Bank Partnership Models
- True lender analysis required — document which entity (platform or bank partner) is the true lender for regulatory purposes
- Bank partner agreement must address AI underwriting standards, ECOA compliance, and adverse action procedures
- Ensure AI underwriting decisions made by platform are covered by bank partner's ECOA compliance program or platform maintains its own

---

## Minimum Data Retention Requirements

| Data Type | Minimum Retention | Legal Basis | Notes |
|-----------|------------------|-------------|-------|
| Credit application records | 25 months | Reg B | From date of action taken |
| Adverse action notices | 25 months | Reg B | Copy of notice + delivery confirmation |
| Credit report used in decision | Duration of relationship + 2 years | FCRA | |
| Model decision logs | 25 months minimum; longer if litigation hold | Reg B; litigation risk | Tamper-evident storage required |
| Fairness test results | Indefinite | Regulatory defense | Version-controlled |
| GLBA privacy notices | Duration of relationship | GLBA | |

---

## Version Control

This section must be reviewed and updated:
- Annually as part of the AI governance review cycle
- Upon any change to model inputs or decision types
- When new regulatory guidance is issued
- Before any geographic expansion to new states

| Version | Date | Changes | Reviewed By |
|---------|------|---------|-------------|
| 1.0 | [Date] | Initial framework | [Name] |

---

*Next: [02 — Decision Flow Documentation](./02-decision-flow.md)*
