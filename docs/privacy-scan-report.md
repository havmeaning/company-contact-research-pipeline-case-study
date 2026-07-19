# Privacy Scan Report

Scan date: 2026-07-19  
Scope: all repository files, including hidden and ignored files

## Outcome

**Pass for local publication review.** No confidential project content or executable implementation was detected.

## Checks performed

| Check | Result |
|---|---|
| Named private-person and client identifiers | No matches |
| Organization-specific identifiers | No known identifiers included |
| Email-like values | No matches |
| Telephone-like values | No contact values detected; date and SVG-coordinate regex hits were reviewed as false positives |
| Postal-address content | No address records detected |
| Absolute private filesystem paths in repository content | No matches |
| Credentials, authorization material, secrets, or authentication values | No matches |
| Live evidence locations or search results | No matches |
| Private filenames, datasets, archives, or workbooks | No included artifacts |
| Executable source or notebook file types | No files detected |
| SVG external dependencies | None |

## Protective ignore rules

The ignore file contains patterns that block common spreadsheet, archive, log, key, environment, and dataset artifacts. Those pattern strings are publication controls, not included private files.

## Manual review notes

- All organizations remain anonymized.
- The only personal identity intentionally included is the case-study author in citation metadata.
- SVG text and metadata contain aggregate metrics and conceptual labels only.
- The repository includes no implementation excerpt or detail intended to reconstruct private code.
- Aggregate claims remain bounded to the controlled, risk-based regression sample.

## Boundary

This scan supports local publication review. It does not certify external hosting behavior or replace a final review of the staged commit before publication.
