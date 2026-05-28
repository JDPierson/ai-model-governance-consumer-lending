# 03 — Fairness & Disparate Impact Controls

> **Why this section matters:** Consumer financial data is high-risk for disparate impact in AI underwriting. Income, geography, payment history, and alternative data all correlate with race and national origin. ECOA and Reg B require that AI credit decisions not have disparate impact on protected classes — and the CFPB has repeatedly made clear that algorithmic complexity is not a defense.

---

## Protected Class Mapping

### ECOA Protected Classes

Under ECOA and Reg B, the following cannot be the basis for a credit decision and must be analyzed for disparate impact:

- Race
- Color
- Religion
- National origin
- Sex (including gender identity and sexual orientation under current CFPB guidance)
- Marital status
- Age (provided the applicant has capacity to contract)
- Receipt of public assistance income

### Proxy Variable Analysis

**High-risk proxy variables in consumer lending AI:**

| Variable | Proxy Risk | Protected Class Correlation | Mitigation |
|----------|------------|----------------------------|------------|
| ZIP code / geographic area | High | Race, national origin | Census tract demographic analysis; document business necessity |
| Language preference | High | National origin | Do not use as underwriting input |
| Educational institution | Medium-High | Race, national origin, income | Proxy analysis; consider exclusion |
| Employer / industry | Medium | Race, national origin, income | Monitor in fairness testing |
| Income level | Medium | Race, receipt of public assistance | Include in fairness testing |
| Rent vs. own | Medium | Race, wealth | Proxy analysis |
| Alternative data patterns | Medium | Race, income, geography | Source-specific proxy analysis |
| Device type / OS | Low-Medium | Income, age | Proxy analysis if used |

**Documentation requirement for each input variable:**
1. Correlation with protected class at statistically significant level — yes/no
2. If yes: business necessity justification
3. Less discriminatory alternative considered and evaluated
4. Outcome of evaluation

---

## Disparate Impact Testing Methodology

### The Four-Fifths Rule

```
Favorable Outcome Rate (Group A) = Approvals / Applications (Group A)
Favorable Outcome Rate (Group B) = Approvals / Applications (Group B)

Disparate Impact Ratio = Rate (Group A) / Rate (Group B)

If Ratio < 0.80: Disparate impact indicated → trigger model review
If Ratio ≥ 0.80: No disparate impact indicated (document result)
```

### Testing Scope — All Decision Types

| Decision Type | Metrics to Test |
|--------------|----------------|
| Approval | Approval rate by protected class |
| Pricing | Average APR / fee by protected class |
| Credit limit | Average limit by protected class |
| Adverse action | Denial rate and reason code distribution by protected class |
| Line decrease / closure | Rate by protected class |

### Testing Cadence

| Trigger | Requirement |
|---------|------------|
| Monthly (production) | Full disparate impact test — all protected classes, all decision types |
| Model change | Immediate pre/post deployment test |
| New data source | Test within 30 days |
| Regulatory inquiry | Immediate test; preserve as regulatory defense |
| Consumer complaint pattern | Targeted analysis for affected segment |

---

## Adverse Action Requirements Under Reg B

### When Notice Is Required

- Denial of credit
- Termination of existing credit
- Unfavorable change in terms compared to what was requested
- Counteroffer applicant does not accept
- Incomplete application (notice of incompleteness)

### Timing

- 30 days after receiving complete application
- 30 days after taking adverse action on existing account

### Reason Code Requirements

**Specific reasons required** — up to 5 principal reasons. Examples of compliant reason codes:

- "Insufficient credit history"
- "Too many delinquent accounts"
- "Debt-to-income ratio too high"
- "Insufficient income for requested amount"
- "Length of employment too short"

**Non-compliant reason codes:**
- "Algorithmic decision"
- "Credit score too low" (without specifying which factors drove the score)
- "Risk model output"

**Reason code library requirements:**
- Maintained list of approved codes mapped to model features
- Plain language — no jargon
- Reviewed annually and after model changes
- Each code tested for disparate impact in its own right

---

## State AI Fairness Laws

Several states have enacted or are enacting AI-specific requirements for credit decisions:

| State | Law | Key Requirement |
|-------|-----|----------------|
| Colorado | SB 21-169 (life insurance; watch for expansion) | Impact assessment; bias testing |
| Illinois | Artificial Intelligence Video Interview Act | Consent; bias testing (employment context — monitor for expansion) |
| New York City | Local Law 144 | Bias audit for automated employment decisions (monitor for credit expansion) |
| California | CCPA / CPRA | Right to opt out of automated decision-making (developing) |

Monitor state legislative activity quarterly — this landscape is moving fast.

---

## Fairness Testing Log Template

```
Fairness Test Log
-----------------
Test ID:            [UUID]
Test Date:          [ISO date]
Model Version:      [X.X.X]
Product Type:       [list]
Testing Period:     [start – end date]
Tester:             [Name, Title]
Reviewer:           [Name, Title]

Decision Types Tested:
  [ ] Approval rate
  [ ] Pricing / APR
  [ ] Credit limit
  [ ] Denial rate
  [ ] Line decrease / closure rate

Results by Protected Class:
  ┌─────────────────┬──────────────┬──────────────┬────────┬──────────┐
  │ Protected Class │ Majority Rate│ Minority Rate│  Ratio │  Result  │
  ├─────────────────┼──────────────┼──────────────┼────────┼──────────┤
  │ Race            │              │              │        │ Pass/Fail│
  │ National Origin │              │              │        │ Pass/Fail│
  │ Sex             │              │              │        │ Pass/Fail│
  │ Age (<40 vs 40+)│              │              │        │ Pass/Fail│
  │ Public Assist.  │              │              │        │ Pass/Fail│
  └─────────────────┴──────────────┴──────────────┴────────┴──────────┘

Reason Code Distribution:
  [Top 5 reason codes by protected class — flag disparities]

Proxy Variables Reviewed:
  [list; note new correlations identified]

Remediation Required:  [ ] Yes  [ ] No
  Ticket reference: [link]
  Timeline: [date]

Sign-off:
  Compliance:     _________________ Date: _________
  Data Science:   _________________ Date: _________
  Legal (if fail):_________________ Date: _________
```

---

*Previous: [02 — Decision Flow Documentation](./02-decision-flow.md)*
*Next: [04 — Data Governance & GLBA Compliance](./04-data-governance-glba.md)*
