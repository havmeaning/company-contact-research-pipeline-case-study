# Case Study

## 1. Executive Summary

A private company-contact research workflow was audited and redesigned after repeated quality failures. The initial hypothesis was that several-hour runtimes and repeated retrievals were the main problem. A controlled 30-company regression sample showed a more consequential issue: the workflow could publish contact details belonging to unrelated sites, directories, portals, or other organizations, sometimes with unjustified high confidence.

V2.1 reorganized the workflow around evidence integrity. Candidate discovery became separate from identity verification; domains were isolated; source operators were classified; each contact field remained bound to its source; and publication required explicit evidence gates. In the controlled, deliberately risk-based sample, harmful false-positive records fell from 24/30 to 0/30 and harmful high-confidence errors fell from 21 to 0. Seventeen deterministic replay and regression tests passed.

The gain was precision, not coverage. V2.1 left 25/30 records unresolved when evidence was insufficient. The sample is not representative of the complete approximately 499-record workload, and V2.1 is a validated intermediate release rather than a production-ready system.

## 2. Operating Context

The workflow accepted company records, searched the web, retrieved candidate pages, extracted company contact information, and exported results to a spreadsheet. At approximately 499 records, a complete run took several hours. That made runtime and database performance visible concerns, but the exported data was also used as an asserted contact dataset. A wrong value therefore carried a greater cost than a missing value.

The project was evaluated as a systems problem spanning input handling, web-source volatility, entity resolution, evidence provenance, confidence semantics, spreadsheet publication, and release governance.

## 3. Initial Assumption

The initial assumption centered on speed: repeated searches, page downloads, and possible database inefficiencies appeared to explain the operational pain. That assumption was reasonable because long-running research automation often accumulates redundant I/O and persistence overhead.

The audit changed the priority. Runtime mattered, but evidence integrity and incorrect contact attribution were the dominant risks. Optimizing the existing path without addressing attribution could have produced incorrect answers faster.

## 4. What the Audit Revealed

The baseline frequently treated search discovery as verification. A page mentioning a company could be mistaken for a page operated by that company. A directory could reproduce a correct company name and address while exposing portal-owned telephone or email details. Candidate fields from multiple domains could then be combined into one published record.

Confidence compounded the problem. It could rise when multiple fields were present even when those fields lacked strong source ownership evidence. The audit also reproduced a spreadsheet-header defect that caused the first company record to be skipped.

These are common failure modes in research automation. Workflows often grow from small scripts; candidate discovery and verification become conflated; extracted fields lose their connection to the source; and confidence scores measure field availability instead of evidence quality. This pattern reflects architectural growth and ambiguous evidence rules, not individual incompetence.

## 5. Baseline Design

A 30-company sample was selected deliberately for risk rather than statistical representativeness. It emphasized ambiguous names, directory-heavy results, domain uncertainty, and other conditions likely to expose attribution defects. A private answer key recorded expected outcomes and evidence for controlled comparison.

The original workflow was replayed without correction. The evaluation recorded runtime, request counts, field correctness, harmful false positives, unjustified high-confidence results, unresolved outcomes, and the spreadsheet-header behavior. This created a reproducible failure baseline while protecting the full private dataset.

## 6. Root Causes

### Discovery and verification were conflated

Search rank or page relevance was allowed to stand in for organizational identity and source ownership.

### Evidence provenance was not preserved at field level

Extracted contact values could become detached from their originating page and domain before publication.

### Candidate domains were allowed to mix

Values gathered from different sites could be merged into one company record without a single verified source boundary.

### Source classes were not treated differently

Official sites, directories, public registers, municipal pages, social platforms, PDFs, and unrelated sites have different evidentiary value. A uniform extraction path obscured those differences.

### Confidence represented completeness more than proof

Available fields could generate high confidence even when operator and ownership claims were weak.

### Publication lacked a conservative evidence gate

The workflow favored returning a value over explicitly recording that no reliable result was available.

### Input and spreadsheet contracts were fragile

Header handling was not sufficiently validated, allowing the first company to be skipped.

## 7. Architectural Redesign

V2.1 separated the workflow into explicit stages:

1. Validate the input contract.
2. Discover candidate sources.
3. Classify each source.
4. Verify company identity.
5. Verify official domain and site operator.
6. Retrieve relevant contact pages.
7. Extract candidate fields without cross-domain mixing.
8. Bind every candidate field to its source.
9. Validate field plausibility and ownership.
10. Apply evidence-based confidence and publication gates.
11. Publish supported values or mark the record unresolved.
12. Produce an audit output.

This design treats evidence as a first-class data product. A telephone number or email address is not merely a string; it is a claim associated with a source, a domain, an operator classification, an organization identity decision, and a publication decision.

## 8. Validation Strategy

The same risk-based sample was used for regression comparison. Deterministic replay fixtures reduced dependence on changing live search results. Regression checks covered harmful false positives, portal publication, source binding, mixed domains, header behavior, and other defined acceptance criteria. SHA-256 checks verified artifact integrity so the tested fixtures and packaged outputs could be identified consistently.

Private evidence and public-safe documentation were packaged separately. The public materials preserve the architecture, definitions, decisions, and aggregate measurements while excluding confidential records and reconstructive implementation detail.

## 9. Results

The baseline produced harmful false-positive records in 24/30 cases and 21 incorrect high-confidence results. V2.1 produced zero harmful false-positive records and zero harmful high-confidence errors in the same controlled sample. It also produced zero invalid portal publications, unbound contact fields, mixed source domains, and header errors. All 17 deterministic replay and regression tests passed.

Coverage decreased: unresolved records rose from 4/30 to 25/30. This was intentional. The new publication standard preferred “no reliable result” to unsupported contact attribution.

These results apply only to the deliberately risk-based 30-company regression sample. They do not estimate performance across all approximately 499 records, demonstrate production readiness, or constitute independent validation.

## 10. Trade-offs

- **Precision over recall:** safer publication created more unresolved outcomes.
- **Auditability over convenience:** source binding and explicit gates increased process structure.
- **Determinism over live realism:** replay fixtures made tests repeatable but cannot fully model web volatility.
- **Conservative confidence over apparent completeness:** fewer fields were published, but confidence became evidence-based.
- **Privacy over reproducibility by outsiders:** confidential evidence remains private, so public readers can inspect methodology and aggregate outcomes but cannot replay private cases.

## 11. Limitations

The sample was intentionally risk-selected and contained only 30 records. Twenty-five V2.1 records remained unresolved. Search and website content change over time. V2.1 was not production deployed, performance optimization remained incomplete, and the work did not establish commercial impact. A larger shadow evaluation is necessary before broader readygeneralization. Manual review remains appropriate where evidence is uncertain.

## 12. Lessons Learned

Research automation needs a distinction between finding information and proving that it belongs to the intended entity. Confidence must be calibrated to evidence quality, not populated-field count. An unresolved result can be the correct result. Deterministic tests and integrity checks are especially valuable when external sources are volatile. Finally, confidentiality controls belong inside the technical design because an accurate system that leaks private evidence is not a high-quality system.

## 13. Next Phase

The next phase is a larger shadow test with a separately designed sample, structured manual-review feedback, resolution-reason analysis, confidence calibration, and performance profiling. Optimization should follow evidence-safety preservation, with regression gates preventing speed improvements from reintroducing harmful attribution.

## 14. Professional Relevance

The project demonstrates how to reframe an apparent performance problem as a broader reliability system. It combines root-cause analysis, entity resolution, evidence provenance, risk-based testing, confidence design, privacy governance, and honest limitation reporting. Those capabilities apply to knowledge operations, data enrichment, compliance-sensitive research, and other automation that converts uncertain public information into asserted records.
