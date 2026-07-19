# Methodology

## Evidence boundary

This document describes the validation method without exposing private records, live evidence, or proprietary implementation. V2.1 is a validated intermediate release tested against a controlled, risk-based regression sample.

## Risk-based sample selection

Thirty records were selected to exercise known or plausible failure modes: ambiguous organization identity, uncertain official domains, directory-heavy search results, portal contact details, cross-domain candidates, and fragile input behavior. Selection was intentionally non-random. The sample is useful for regression detection but cannot estimate full-dataset prevalence or accuracy.

## Private ground-truth answer key

A private answer key recorded the expected organization identity, acceptable official sources, supported contact outcomes, and unresolved cases. Review decisions were based on preserved evidence rather than the workflow's own output. The answer key and underlying records are excluded from this repository.

## Evidence URL recording

Private evaluation records retained the source location supporting each judgment. Public documentation omits those locations because they could reveal organizations, identifiers, or confidential research context. Aggregate metrics and decision rules are published instead.

## Baseline reproduction

The original workflow was run against the controlled sample without applying corrections. Runtime, external request counts, field outcomes, confidence decisions, unresolved results, and spreadsheet behavior were recorded. The header defect was reproduced as part of this baseline.

## Metric definitions

### Correct website

A published website verified as operated by the intended organization, rather than merely mentioning it or reproducing its identifying details.

### Correct telephone number

A published telephone value supported as belonging to the intended organization by evidence meeting the evaluation standard.

### Correct email address

A published email value supported as belonging to the intended organization by evidence meeting the evaluation standard.

### Harmful false positive

A published website, telephone number, or email address that belongs to a different organization, portal, municipality, directory operator, or unrelated entity.

The record-level metric counts a record once if it contains one or more such assignments.

### Harmful high-confidence error

A harmful false positive published with a confidence classification that represented it as strongly supported.

### Non-harmful discrepancy

A difference that does not assign another entity's contact information—for example, a formatting variation or a conservative unresolved result. These discrepancies are reviewed but are not counted as harmful false positives.

### Unresolved

No contact value is published because available evidence does not meet the required publication threshold.

### Invalid portal publication

A contact value belonging to a directory, portal, municipal service, or other intermediary that is published as if it belonged directly to the intended company.

### Unbound contact field

A published contact field without a retained relationship to the source record from which it was extracted and evaluated.

### Mixed source domains

A published company record constructed from contact fields originating from different candidate domains without an explicitly verified common ownership basis.

### Header error

An input or output defect caused by treating a data row as a header, treating a header as data, or otherwise shifting the expected record boundary.

### Replay and regression test

A deterministic check run against preserved, non-live fixtures to verify a defined behavior or prevent recurrence of a known failure mode.

## False-positive classification

Review separated harmful attribution from lower-risk discrepancies. The critical question was not whether a value looked plausible, but whether publishing it asserted ownership by the wrong entity. Portal-owned contact details, unrelated sites, and contact values from another organization were classified as harmful.

## Contact-source binding

Every candidate and published field retained a source association through evaluation. Publication could therefore be evaluated against the source's domain, classification, operator, company identity decision, and evidence strength. A value could not borrow confidence from a different source.

## Domain isolation

Candidate domains were evaluated independently. Fields from separate candidates were not pooled into a composite record before ownership and identity conditions were satisfied. This prevented a correct name from one site, a telephone number from another, and an email from a third from being presented as one verified company profile.

## Portal and source classification

Sources were classified into categories such as official company sites, directories, registers, municipal pages, social media, PDFs, portals, and unrelated sites. Classification changed how evidence was interpreted; a mention on a register or directory did not establish that the page operator owned the displayed contact channel.

## Confidence criteria

Confidence was based on evidence quality and agreement across required checks. Field presence alone was insufficient. High confidence required verified organization identity, verified operator or official-domain relationship, source-bound contact evidence, and satisfaction of publication rules. Failure at a required gate led to a lower classification or an unresolved result.

## Deterministic replay fixtures

Preserved fixtures represented the conditions needed to test known risks without relying on live search ordering or mutable webpages. They supported repeatable comparisons between baseline behavior and V2.1 while remaining in the private package.

## Regression testing

Seventeen deterministic tests covered acceptance conditions including false-positive prevention, source binding, domain isolation, portal handling, confidence behavior, header handling, and reproducible replay. All 17 passed for V2.1 on the controlled sample.

## SHA-256 integrity verification

SHA-256 digests identified the exact private fixtures and packaged artifacts used during validation. Hashes supported change detection and release traceability; they did not establish the correctness of the underlying content by themselves.

## Private and public-safe packaging

The private release retained evidence needed for authorized review. The public-safe package retained only anonymized documentation, aggregate results, original synthetic diagrams, and governance records. Separation reduced the chance that publication, version control, or portfolio reuse would expose client data or proprietary implementation.

## Interpretation rule

All reported results are conditional on the controlled, deliberately risk-based 30-company sample. No metric in this repository should be interpreted as an unbiased estimate for the approximately 499-record workload.
