# P6 Incident response and breach notification (DRAFT)
Owner role: Human Principal (decides), Orchestrator (runs), Builder (fixes). Supports: HIPAA 164.308(a)(6) security incident procedures, 164.404-414 breach notification concepts; HITRUST incident management; NIST AI RMF Manage; ISO/IEC 42001. No real PHI is processed: every drill is a simulation. Wording: aligned with.

1. An incident is any suspected leak of real or canary data, credential exposure, failed audit-chain verification, unexplained hook deny, unauthorized change, or agent action outside its role. Anyone (human or agent) MUST stop and report it the moment it is suspected.
2. Suspected real data in any system MUST trigger P2 immediately: stop the work, contain, tell the Human Principal.
3. Severity classes and first responses MUST be written down: S1 (data or credential exposure: contain at once, revoke, rotate), S2 (integrity or policy failure), S3 (near miss).
4. Every incident MUST be recorded as a signed ledger event and a written report: timeline, cause, impact, fix, and the test or rule that prevents recurrence (a red test, a Cedar rule or a lesson).
5. Containment actions that delete, spend, publish or change credentials MUST still follow the hard rules (Human Principal's word, standalone yes/no).
6. If real PHI were ever involved, the breach-notification duties of HIPAA (individuals, regulator, media as applicable, within the legal deadlines) MUST be followed with counsel; until a signed BAA exists no real PHI is allowed.
7. At least one incident drill MUST be run and reported before Gate G1 passes, then quarterly.
Mechanism (status, refreshed 2026-11-12): hook deny/ask with an audit chain (implemented); restore test and runbook (done 2026-11-05); kill switch (planned); incident ledger events (schema planned); full drill (planned).
Public evidence: the live explorers (scryon.entropa.space, scryon-health.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public, aimozart/scryon-health-data, aimozart/scryon-council and aimozart/hippagrchealthcare. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
