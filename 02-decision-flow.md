# 02 — Decision Flow Documentation

## Core Underwriting Decision Flow

Each credit application moves through the following compliance-checkpointed stages. The compliance checkpoint at each stage generates the evidence artifact — documentation is not a separate step.

---

### Stage 1: Application & Data Collection

**What happens:** Consumer submits application. Platform collects application data and pulls credit bureau or alternative data.

**Compliance checkpoint:**
- GLBA privacy notice delivered to consumer at or before application (or confirm prior delivery)
- FCRA permissible purpose confirmed before pulling credit report — "review of credit application" is standard permissible purpose; document
- Data collected logged with: timestamp, source, fields collected, consumer identifier
- Prohibited inputs screened — confirm no protected class data collected
- State privacy law compliance: CCPA notice at collection if California consumer

**Evidence artifact:** Application log; FCRA permissible purpose record; privacy notice delivery confirmation

---

### Stage 2: Input Processing & Proxy Variable Screening

**What happens:** Input data prepared for underwriting model. Variables screened for protected class and proxy variable risk.

**Compliance checkpoint:**
- Confirm no prohibited inputs present (race, color, religion, national origin, sex, marital status, age, receipt of public assistance)
- Run proxy variable screen against documented proxy variable mapping (Section 03)
- Flag high-correlation proxy variables for compliance review before model run
- Alternative data sources confirmed as FCRA-compliant or non-FCRA with documented analysis

**Evidence artifact:** Input processing log with proxy variable screen results; flagged inputs and disposition

---

### Stage 3: AI Credit Decision

**What happens:** Model processes inputs and generates credit decision and terms.

**Compliance checkpoint:**
- Log: input data snapshot (hashed), model version, decision output, confidence parameters, timestamp
- Generate reason codes for decision — required for adverse action notice if decision is adverse
- Assess decision type: approval, denial, counteroffer, or incomplete application
- If adverse: confirm reason codes are specific and human-readable (not "algorithmic decision")

**Evidence artifact:** Decision log entry (immutable, structured JSON); reason code record

---

### Stage 4: Adverse Action Notice (If Applicable)

**What happens:** If credit denied, terms worse than requested, or counteroffer not accepted — adverse action notice required.

**Compliance checkpoint:**
- Notice delivered within 30 days of decision
- Notice content: action taken; creditor name/address; ECOA statement; federal agency contact; **specific reasons** (up to 5 principal reasons)
- Reason codes translated to plain language — specific to this consumer's application
- Delivery method documented: mail, electronic (with consent), or in person
- Copy of notice retained with delivery confirmation

**Evidence artifact:** Adverse action notice copy; delivery confirmation; reason code mapping

---

### Stage 5: Account Servicing

**What happens:** Approved consumer uses credit product. Servicing events logged.

**Compliance checkpoint:**
- All servicing events logged: event type, timestamp, amount, account identifier
- GLBA NPI in servicing records subject to FTC Safeguards Rule access controls
- Consumer rights requests (FCRA dispute, CCPA access/deletion) routable to compliance
- FDCPA compliance if account reaches delinquency: communication rules, time restrictions, dispute rights

**Evidence artifact:** Servicing event log; consumer rights request log; delinquency handling log

---

### Stage 6: Account Closure & Data Disposition

**What happens:** Account closed, charged off, or transferred. Retention and deletion obligations triggered.

**Compliance checkpoint:**
- Retention period confirmed: Reg B minimum 25 months from action date; FCRA duration of relationship + 2 years; state law may extend
- Data deletion executed per documented retention schedule with certificate
- If account sold or transferred: confirm receiving entity has appropriate service provider agreements

**Evidence artifact:** Account closure record; data retention/deletion log; transfer agreement if applicable

---

## Human Review Triggers

| Trigger | Reason | Required Action |
|---------|--------|-----------------|
| Model confidence below threshold | Higher error and disparate impact risk | Human underwriter review; document rationale |
| High-correlation proxy variable flagged | Protected class proxy risk | Compliance review; document business necessity |
| Adverse action on protected class member | Disparate impact signal | Flag for fairness monitoring; document handling |
| Decision in state with specific AI requirements (CO, IL, TX) | State AI bias law compliance | State-specific review; document |
| Application involves potential FCRA dispute | Accuracy obligation | FCRA dispute process; do not use disputed information |
| Repeat adverse actions — same consumer | Potential ECOA pattern | Compliance review |

---

## Override Procedures

All human overrides of AI decisions must be documented:

**Override log requirements:**
- Reviewer ID and role
- Original AI decision and reason codes
- Override decision
- Override reason (from documented reason code library)
- Date and timestamp
- Supervisor notification if override frequency threshold exceeded

**Override pattern analysis:**
- Quarterly review by compliance
- High override rates on specific consumer segments trigger fairness analysis
- Systematic patterns trigger model review (Section 06)

---

## Decision Log Template

```
Decision Log Entry
------------------
Entry ID:           [UUID]
Timestamp:          [ISO 8601]
Model Version:      [X.X.X]
Product Type:       [BNPL | personal_loan | auto | student | EWA | marketplace]
Decision Type:      [approval | denial | counteroffer | line_increase | line_decrease | closure]
Consumer Ref:       [hashed identifier]
Input Hash:         [SHA-256 of input data snapshot]
Decision Output:    [structured — approved amount/rate/terms or denial]
Confidence Score:   [0.0–1.0]
Reason Codes:       [list — from documented reason code library]
FCRA Data Used:     [yes/no — if yes, CRA name and permissible purpose ref]
Proxy Flag:         [yes/no — if yes, proxy screen result ref]
Human Review:       [yes/no — if yes, reviewer ID and rationale ref]
Override:           [yes/no — if yes, override log ref]
Adverse Action:     [yes/no — if yes, notice ref and delivery date]
State:              [consumer's state of residence]
```

---

*Previous: [01 — Model Purpose & Scope](./01-model-purpose-scope.md)*
*Next: [03 — Fairness & Disparate Impact Controls](./03-fairness-controls.md)*
