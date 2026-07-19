# Decision Log

| Decision | Rationale | Consequence |
|---|---|---|
| Reframe the project from performance-only to evidence integrity | The baseline showed harmful attribution was the dominant risk | Correctness controls preceded optimization |
| Use a risk-based 30-record regression sample | Challenging cases exposed failure modes efficiently | Results cannot estimate the full dataset |
| Separate discovery from verification | Search relevance did not prove identity or ownership | More explicit stages and decisions |
| Isolate candidate domains | Cross-domain merging produced unsupported composite records | Lower apparent coverage, stronger provenance |
| Bind every contact field to its source | Detached fields could inherit unrelated evidence | Auditable field-level decisions |
| Classify portals and intermediaries | Correct company mentions did not prove contact ownership | Intermediary details were blocked from direct publication |
| Make unresolved a valid output | Forced completion encouraged harmful false positives | V2.1 left 25/30 records unresolved |
| Base confidence on evidence quality | Field availability created unjustified certainty | High confidence required identity, ownership, and binding evidence |
| Add deterministic replay | Live search volatility hindered repeatability | Regression checks could be rerun consistently |
| Verify artifact integrity with SHA-256 | Validation needed stable artifact identity | Controlled packages could be checked for change |
| Separate private and public-safe releases | Evidence and implementation were confidential | Public documentation remains useful without disclosure |
| Defer broad performance claims | No validated V2.1 runtime comparison was supplied | The case study makes no speed-improvement claim |

Every result in this log is bounded to a controlled, deliberately risk-based 30-company regression sample unless stated otherwise.
