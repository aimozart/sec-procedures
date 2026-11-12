# P0 Patient and client data safety comes first (DRAFT, top priority)
Owner role: Human Principal. Supports: HIPAA 164.306(a) general requirements, 164.308(a)(1), 164.312; HITRUST data protection and privacy; NIST AI RMF Govern/Manage; ISO/IEC 42001. Wording: aligned with. This policy overrides convenience, speed and demo polish (Human Principal, 2026-10-21).

1. Patient and client data and information safety MUST come first, always, even when the data is mocked.
2. All healthcare and banking data in our systems MUST be synthetic and labelled as such; real PHI or real personal data MUST NOT enter any system, prompt, log, ledger event, repository or public page.
3. Synthetic data MUST be generated on demand from a seed and stored as little as possible; identifier-shaped values (SSN, MRN, names, phones, emails) MUST come from reserved invalid ranges so they can never match a real person.
4. Canary strings MUST be planted in mock PHI and automated checks MUST prove they never appear in prompts, logs, ledger events, bundles, public pages or model inputs outside the gate.
5. Synthetic PHI MUST be handled as if real under the mock-PHI SOP (P2).
6. Any suspected real data MUST stop the work and start incident response (P6) at once.
7. Every stage review MUST ask: could this leak or look like real data?
Mechanism (status, refreshed 2026-11-12): reserved-invalid identifier generators, canary scanner and repo-wide scans (implemented); council decoder refuses canaries (implemented); canary and identifier scan of every published file in the site export (implemented 2026-11-05); runtime log scan (open).
Public evidence: the live explorers (scryon.entropa.space, scryon-health.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public, aimozart/scryon-health-data, aimozart/scryon-council and aimozart/hippagrchealthcare. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
