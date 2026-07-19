# Validation

## Validation scope

The comparison used the same controlled, deliberately risk-based 30-company regression sample. It was designed to expose known failure modes, not to estimate average performance across the full approximately 499-record workload. V2.1 is a validated intermediate release, not a production-readiness claim.

## Baseline

| Metric | Baseline |
|---|---:|
| Runtime | 425.46 seconds |
| Search requests | 90 |
| Page requests | 115 |
| Correct websites | 2/30 |
| Correct telephone numbers | 9/30 |
| Correct email addresses | 5/30 |
| Harmful false-positive records | 24/30 |
| Incorrect high-confidence results | 21 |
| Unresolved records | 4/30 |

The spreadsheet header defect was also reproduced. The baseline measurements characterize only the controlled sample.

## V2.1

| Metric | V2.1 |
|---|---:|
| Harmful false-positive records | 0/30 |
| Harmful high-confidence errors | 0 |
| Invalid portal publications | 0 |
| Unbound contact fields | 0 |
| Mixed source domains | 0 |
| Header errors | 0 |
| Replay and regression tests | 17/17 passed |
| Unresolved records | 25/30 |

No V2.1 runtime improvement is claimed because a validated comparison was not supplied. No production, financial, adoption, or full-dataset result is inferred.

## Precision–recall trade-off

V2.1 improved precision by accepting lower recall. The baseline resolved more records but frequently published unsupported or wrongly attributed contacts. V2.1 required evidence sufficient to support organization identity, source operation, field ownership, and publication. When those conditions were not met, it returned unresolved.

The increase from 4/30 to 25/30 unresolved records is therefore a visible cost of the safety policy, not a hidden failure. Further work should improve safe resolution without weakening the evidence threshold.

## Before-and-after interpretation

- Harmful false-positive records decreased from 24/30 to 0/30 in the controlled sample.
- Harmful or incorrect high-confidence outcomes decreased from 21 to 0 under the revised evidence rules.
- Source-binding, domain-isolation, portal-publication, and header acceptance criteria recorded zero violations in V2.1.
- Seventeen deterministic replay and regression tests passed.

These findings support the conclusion that the redesign prevented the targeted regression classes in this sample. They do not prove general performance across all 499 records, production readiness, or external commercial impact.

## Evidence quality

The validation was internally controlled rather than independently audited. Deterministic fixtures improved repeatability, and SHA-256 verification supported artifact identity. Live-web volatility remains outside complete deterministic control. A broader shadow test and continued manual adjudication are required for generalization.
