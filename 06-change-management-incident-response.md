# 06 — Model Change Management & Incident Response

## Model Change Management

All model changes require compliance review before production deployment.

### Change Classification

| Change Type | Compliance Review | Fairness Test | Sign-off Level |
|-------------|------------------|---------------|----------------|
| Retraining (same architecture, new data) | Yes | Yes — within 30 days | Compliance |
| Input variable addition | Yes — input classification required | Yes — immediate pre/post | Compliance + Legal |
| Input variable removal | Yes | Yes — confirm improvement | Compliance |
| Decision threshold adjustment | Yes | Yes — immediate pre/post | Compliance |
| Architecture change | Yes | Yes — immediate pre/post | Compliance + Legal + Data Science |
| Reason code library update | Yes | Spot check | Compliance |
| Bug fix (no behavior change) | Notify compliance | Spot check | Compliance awareness |

### Change Review Process

```
Model Change Request
--------------------
Change ID:          [UUID]
Requested by:       [Name, Team]
Date:               [ISO date]
Change Type:        [from table above]
Description:        [plain language]
Product Types Affected: [list]
Decision Types Affected: [list]
Expected Impact:    [higher/lower approval rates, pricing changes, etc.]
Input Variable Changes: [additions/removals]
Proxy Variable Analysis: [completed? attach if yes]
Disparate Impact Pre-Assessment: [completed? attach if yes]
FCRA Data Changes: [any changes to credit bureau data use?]

Compliance Review:
  Reviewer:         [Name]
  Date:             [ISO date]
  Decision:         [ ] Approved  [ ] Approved with conditions  [ ] Rejected
  Conditions:       [if applicable]
  Sign-off:         _________________

Deployment:
  Deployed by:      [Name]
  Date:             [ISO date]
  Model Version:    [X.X.X]

Post-Deployment:
  Fairness test due: [ISO date]
  Fairness test ref: [link when complete]
```

---

## Model Incident Response

### Incident Triggers

| Trigger | Severity | Immediate Action |
|---------|----------|-----------------|
| Fairness test below 80% threshold | High | Suspend affected decision type; notify compliance leadership |
| Regulatory inquiry about AI decisions | High | Preserve all logs; notify Legal immediately |
| Consumer complaint pattern — protected class | Medium-High | Compliance investigation; targeted fairness analysis |
| FCRA dispute revealing data accuracy issue | Medium-High | FCRA dispute process; assess model input accuracy |
| Data source change affecting model inputs | Medium | Input classification review; fairness test |
| Model drift (feature importance shift) | Medium | Compliance notification; fairness spot check |
| Data breach involving model inputs/outputs | High | FTC Safeguards Rule incident response; state breach notification |
| Reason code inadequacy identified | Medium | Immediate reason code review; adverse action notice audit |

### Incident Response Playbook

**Step 1 — Contain**
- Suspend affected decision type if risk is acute
- Preserve all relevant logs (do not delete or overwrite)
- Document: incident description, trigger, date/time, accounts potentially affected

**Step 2 — Assess**
- Quantify scope: decisions affected, time period, consumer population
- Run fairness analysis on affected population
- Regulatory notification obligations:
  - ECOA / CFPB: voluntary disclosure if pattern of disparate impact?
  - FTC Safeguards Rule: data breach notification if NPI compromised?
  - State breach notification: assess by state of affected consumers
  - FCRA: dispute process if credit report accuracy affected?
- Consumer remediation: corrected decisions, updated adverse action notices?

**Step 3 — Remediate**
- Model adjustment, retraining, or override procedure
- Affected consumers reprocessed if feasible
- Root cause documented and addressed

**Step 4 — Notify**
- Regulatory notification if required (document decision either way)
- Consumer notification if adverse decisions identified as erroneous
- Internal: leadership, Legal, Data Science, Engineering

**Step 5 — Document**
- Full incident record as regulatory defense artifact
- Post-incident review: what failed, what changed
- Framework updated if gap identified

---

*Previous: [05 — Regulatory Mapping](./05-regulatory-mapping.md)*
*Next: [07 — Evidence Architecture](./07-evidence-architecture.md)*
