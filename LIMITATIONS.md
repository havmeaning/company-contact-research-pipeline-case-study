# Limitations

## Validation design

- The validation sample was deliberately risk-based, not random or representative.
- Only 30 records were used in the controlled regression test.
- The results cannot estimate performance across the full approximately 499-record workload.
- Validation was internal rather than independent third-party review.

## Resolution and recall

- V2.1 left 25/30 records unresolved.
- The unresolved rate reflects a deliberate preference for supported results over apparent completeness.
- The validation demonstrates prevention of targeted harmful outcomes in the sample; it does not demonstrate high coverage.

## External-source volatility

- Live web search is volatile.
- Rankings, pages, domain ownership signals, and contact details may change over time.
- Deterministic replay improves regression repeatability but cannot replace periodic live evaluation.

## Operational maturity

- V2.1 was not production deployed.
- Performance optimization remained incomplete.
- No validated V2.1 runtime comparison is available.
- No financial savings, user adoption, stakeholder endorsement, or commercial impact is claimed.
- No conclusion is made about operational behavior at full scale.

## Generalization

Broader generalization requires a larger shadow test designed separately from the regression sample. That evaluation should measure safe resolution, harmful attribution, confidence calibration, review burden, source-class behavior, runtime, and failure recovery without weakening existing safety gates.

## Human review

Manual review remains appropriate for uncertain cases, ambiguous ownership, conflicting sources, and evidence near the publication threshold. Automation should prioritize and document those cases rather than conceal uncertainty.

## Status statement

V2.1 is a validated intermediate release tested against a controlled, risk-based 30-company regression sample. It is not presented as production-ready, independently validated, or proven across all approximately 499 records.
