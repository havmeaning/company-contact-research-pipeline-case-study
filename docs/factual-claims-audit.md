# Factual Claims Audit

Audit date: 2026-07-19

## Supplied baseline metrics

| Claim | Audited value | Status |
|---|---:|---|
| Approximate full workload | 499 records | Matches supplied context |
| Controlled sample | 30 companies | Matches supplied context |
| Baseline runtime | 425.46 seconds | Matches supplied metric |
| Baseline search requests | 90 | Matches supplied metric |
| Baseline page requests | 115 | Matches supplied metric |
| Correct websites | 2/30 | Matches supplied metric |
| Correct telephone numbers | 9/30 | Matches supplied metric |
| Correct email addresses | 5/30 | Matches supplied metric |
| Harmful false-positive records | 24/30 | Matches supplied metric |
| Incorrect high-confidence results | 21 | Matches supplied metric |
| Baseline unresolved records | 4/30 | Matches supplied metric |
| Header defect | Reproduced | Matches supplied context |

## Supplied V2.1 metrics

| Claim | Audited value | Status |
|---|---:|---|
| Harmful false-positive records | 0/30 | Matches supplied metric |
| Harmful high-confidence errors | 0 | Matches supplied metric |
| Invalid portal publications | 0 | Matches supplied metric |
| Unbound contact fields | 0 | Matches supplied metric |
| Mixed source domains | 0 | Matches supplied metric |
| Header errors | 0 | Matches supplied metric |
| Replay and regression tests | 17/17 passed | Matches supplied metric |
| Unresolved records | 25/30 | Matches supplied metric |

## Claim-boundary audit

| Prohibited inference | Repository status |
|---|---|
| Representative estimate for all records | Not claimed; explicitly disclaimed |
| Production readiness or deployment success | Not claimed; explicitly disclaimed |
| V2.1 runtime improvement | Not claimed |
| Financial savings or commercial impact | Not claimed |
| User adoption or stakeholder endorsement | Not claimed |
| Independent validation | Not claimed; explicitly disclaimed |
| Successful resolution of all records | Not claimed; 25/30 unresolved is prominent |

## Required status language

The repository describes V2.1 as a validated intermediate release tested against a controlled, risk-based regression sample. Major result sections repeat the sample limitation.

## Portfolio claim calculation

The 80% baseline statement is the supplied record-level fraction expressed as a percentage: 24 harmful false-positive records divided by 30 sampled records. The denominator is always identified as the controlled, risk-based sample.

## Conclusion

**Pass.** Numerical claims match the supplied evidence, and unsupported performance, deployment, impact, or generalization claims were not introduced.
