# Reliable Company Contact Research Pipeline

_An anonymized case study in source traceability, entity verification, confidence calibration, and evidence-controlled automation_

## Overview

This documentation-only repository examines the redesign of a Python-based company-contact research workflow. The work began as a performance investigation and became a data-quality and evidence-governance project after a controlled audit showed that incorrect contact attribution—not runtime alone—was the dominant risk.

> “Diagnosed and redesigned a slow, unreliable company-contact research pipeline, reducing harmful false-positive assignments from 80% to 0% in a controlled, risk-based 30-company regression sample while introducing source-level traceability, confidence controls, deterministic testing, and privacy-safe release packaging.”

**The sample was deliberately risk-based and is not an unbiased estimate of performance across the full dataset.**

## Problem

The original workflow processed approximately 499 records through repeated search, retrieval, and spreadsheet-export steps. A focused audit found that candidate discovery, organization verification, contact extraction, and publication were too tightly coupled. Correct company details could be combined with contact information owned by a directory, portal, municipality, or unrelated organization. Confidence often reflected field availability rather than evidence quality. A spreadsheet header defect also skipped the first company.

## Baseline

On a controlled 30-company risk-based regression sample, the baseline took 425.46 seconds, issued 90 search requests and 115 page requests, and produced harmful false-positive assignments in 24 of 30 records. It also produced 21 incorrect high-confidence results. These figures describe the deliberately challenging regression sample only.

## Intervention

V2.1 separated candidate discovery, source classification, identity verification, official-domain verification, extraction, source binding, validation, confidence gating, and publication. It added domain isolation, portal detection, deterministic replay fixtures, regression checks, SHA-256 integrity verification, and distinct private and public-safe release packages.

## Results

Within the same controlled sample, V2.1 reduced harmful false-positive records from 24/30 to 0/30 and harmful high-confidence errors from 21 to 0. It also recorded zero invalid portal publications, unbound contact fields, mixed source domains, and header errors; 17/17 replay and regression tests passed.

The precision improvement came with a deliberate recall trade-off: 25/30 records remained unresolved because the evidence did not meet the publication threshold. V2.1 is **a validated intermediate release tested against a controlled, risk-based regression sample**, not a production-ready system or a general estimate for all 499 records.

## Key engineering decisions

- Bind every published contact field to its source.
- Keep candidate domains isolated until identity and operator checks pass.
- Treat page mention, site ownership, field ownership, and publishability as separate claims.
- Classify directories, registers, municipal sites, social platforms, PDFs, portals, and unrelated sources explicitly.
- Make “unresolved” a valid safety outcome.
- Use deterministic replay and integrity hashes to make validation repeatable.
- Separate confidential evidence from public-safe documentation.

## Limitations

The validation used 30 deliberately risk-selected records. Live search is volatile, 25 records remained unresolved, V2.1 was not production deployed, runtime optimization was incomplete, and broader generalization requires a larger shadow test. Manual review remains appropriate for uncertain cases.

## Repository scope

This repository contains architecture, methodology, validation results, decision records, and original synthetic diagrams. It contains no executable project code, datasets, private workbooks, live evidence, or implementation details sufficient to reconstruct the proprietary workflow.

## Privacy statement

All organizations and operational artifacts are anonymized. Confidential identifiers, contact details, evidence links, logs, credentials, and private file paths are excluded by design.

## Skills demonstrated

Systems analysis · data-quality engineering · entity and domain verification · evidence governance · confidence calibration · deterministic testing · privacy-aware release design · technical communication

## Project status

Documentation complete for local review. V2.1 remains a validated intermediate release; no deployment-readiness claim is made.

Start with [CASE_STUDY.md](CASE_STUDY.md), then review [METHODOLOGY.md](METHODOLOGY.md), [VALIDATION.md](VALIDATION.md), and [LIMITATIONS.md](LIMITATIONS.md).
