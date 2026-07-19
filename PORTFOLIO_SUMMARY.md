# Portfolio Summary

## LinkedIn project description

I audited and redesigned a Python-based company-contact research workflow that had initially appeared to be primarily a runtime problem. A controlled review showed that the more important risk was evidence integrity: candidate discovery and verification were conflated, fields could lose their source context, and third-party portals could be treated as official company sources.

I introduced a staged architecture for identity and domain verification, source classification, field-level provenance, domain isolation, confidence gating, deterministic replay, regression testing, SHA-256 integrity checks, and separate private/public-safe packaging.

In a deliberately risk-based 30-company regression sample, harmful false-positive assignments fell from 24/30 to 0/30, harmful high-confidence errors fell from 21 to 0, and 17/17 deterministic checks passed. The redesign intentionally favored precision over recall: 25/30 records remained unresolved when evidence did not meet the publication threshold.

The sample was not representative of the full dataset, and the intermediate release was not production deployed. The project demonstrates systems analysis, data-quality engineering, evidence governance, confidence calibration, and privacy-aware technical communication.

## Resume bullet

> Redesigned and validated a Python-based company-contact research pipeline, reducing harmful false-positive assignments from 80% to 0% in a controlled 30-company risk-based regression sample while introducing source-level traceability, domain isolation, confidence gates, and 17 deterministic regression tests.

## Portfolio card

**Reliable Company Contact Research Pipeline**  
An anonymized data-quality case study showing how source binding, entity verification, domain isolation, and conservative confidence gates prevented targeted harmful contact attribution in a controlled risk-based regression sample. V2.1 passed 17/17 deterministic checks while deliberately leaving uncertain records unresolved.

## Interview explanation

The project started as an investigation into a slow workflow processing roughly 499 company records. Instead of optimizing immediately, I built a controlled risk-based sample and reproduced the existing behavior. The audit showed that incorrect attribution was more serious than runtime: a page could mention the right company while being operated by a directory or portal, and fields from different domains could be merged.

I redesigned the workflow around separate evidence claims. Discovery produced candidates; identity checks established which organization a page referred to; operator and domain checks established who controlled it; field-level source binding established where each contact came from; and a confidence gate decided whether the evidence was sufficient to publish. Deterministic replay and integrity checks made regression testing repeatable, while private and public-safe packaging protected confidential material.

On the deliberately difficult 30-record regression sample, harmful false-positive records moved from 24 to zero and 17 tests passed. The trade-off was that 25 records remained unresolved. I would not call that production proof—the next step is a larger shadow test—but it demonstrated that the redesigned controls prevented the failure classes they targeted.

## 30-second verbal summary

I audited a slow company-contact research workflow and found that its main risk was not speed but evidence attribution. It could combine fields across domains or publish portal-owned contact details with high confidence. I redesigned it around identity verification, official-domain checks, field-level source binding, conservative confidence gates, and deterministic tests. In a risk-based 30-company regression sample, harmful false positives fell from 24 to zero and all 17 tests passed, with the honest trade-off that 25 records remained unresolved. It was a validated intermediate release, not a production-readiness claim.

## Evidence qualification

All portfolio versions refer to a deliberately risk-based 30-record sample. None should be used to imply representative full-dataset accuracy, production deployment, commercial impact, or independent validation.
