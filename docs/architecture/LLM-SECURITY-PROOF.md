# LLM security: proven, not stated

Status: PLAN approved by the Human Principal on 2026-11-12. Nothing in the table below is claimed as done until its row has a control in code, an attack test and a measured number. Results will be added here row by row, including miss rates above zero.

All data is synthetic. Wording rule: "tested against", "aligned with"; never "secure", "compliant" or "certified".

## Goal
Every LLM risk class has a control enforced in code, an attack test that tries to break it, and a measured result published with its limits. Frame: OWASP Top 10 for LLM Applications (2025 list; confirm item names from owasp.org when the stage starts). Wording: "tested against", never "compliant" or "secure".

## Proof table (one row per risk: control, attack test, number)
| Risk | Control in code | Attack test | Reported number |
|---|---|---|---|
| Prompt injection | rules first, local injection detector before the model, closed-code output, tripwire, human gate | hostile notes (existing + new paraphrase, encoding, multilingual, split-instruction sets) | detection rate, false-positive rate, obeyed-injection rate with each layer on and off |
| Sensitive information disclosure | de-identify before the model, outbound backstop scan, canaries, data-minimal records | planted identifiers and canaries in every field | leaks = 0 or the count |
| Supply chain | pinned dependencies with hashes, SBOM, pinned model id and version, SHA-pinned CI actions, model file checksum for the local model | tampered lock entry and wrong checksum must fail the gate | pass/fail |
| Data and model poisoning | seeded generated sets with manifests and hashes; only signed accepted precedents enter memory | altered case file or unsigned precedent must be refused | pass/fail |
| Improper output handling | strict parser, closed codes, no model text executed or rendered raw | junk, oversize, markup, code-shaped answers | all denied = count |
| Excessive agency | model can only return a code; Cedar gate; high-value and delete-class actions need a person | model "decides" a forbidden action | unsafe action rate |
| System prompt leakage | no secrets in prompts; prompt hash pinned and public | extraction attempts | leaks; and proof nothing secret was there to leak |
| Vector and embedding weaknesses | tenant in the index hash, exact index is the source of truth, retrieval is evidence not authority | wrong-tenant query, poisoned precedent | zero rows / refused |
| Misinformation | bars on accuracy and needs_human recall; undetermined goes to a person | hard set | the 13 bars |
| Unbounded consumption | spend meter with hard stop, timeout, retry cap, rate limit | loop and flood tests | stop fires at the cap |

## Also in the stage
- Egress allow-list: the model client may reach only the one model host; a test proves any other host is refused.
- Kill switch: one signed halt stops model calls; drill recorded.
- On-premises mode: local model behind the same interface, scored on the same 13 bars; accuracy cost reported.
- Every attack run is an evidence receipt on the ledger; a public scorecard page shows the table with numbers and stated limits.

## Forecast, exit bar, cost
Forecast: 10 risk rows, each with at least one failing-first attack test; some rows will show a non-zero miss rate and that is published. Exit bar: every row has control + test + number; no row is text only; the Orchestrator's own probes on a fresh copy find no unreported bypass. Cost: 0 USD to run locally; Gemini attack runs inside a 5 USD cap. Needs the Human Principal's go at stage start: llama.cpp install (PATH proven) and model downloads of about 5 to 10 GB.


## Results
None yet. This section is filled from signed evidence receipts as each row is built and attacked.
