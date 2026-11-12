# P7 Risk analysis and review cadence (DRAFT)
Owner role: Human Principal. Supports: HIPAA 164.308(a)(1)(ii)(A) risk analysis and (B) risk management, 164.308(a)(8) evaluation; HITRUST risk management; NIST AI RMF Map/Measure; ISO/IEC 42001 risk clauses. Wording: aligned with.

1. A risk register MUST exist: asset, threat, likelihood, impact, control, owner, status; it MUST cover each agent, each cloud account, each repository and each public surface.
2. Threat models MUST exist for the ledger, the explorer, the hook and each agent, and MUST be updated when the design changes.
3. Risks MUST be reviewed at the weekly council cycle, triggered sessions (override spike, failed policy, incident, hard-rule request) and the monthly retrospective; an item with no decision stays pending and nothing changes.
4. Access reviews (who holds which role, which keys exist, which accounts have MFA) MUST be done monthly and recorded.
5. Policies MUST be reviewed at least quarterly and after every incident; changes MUST go through P8.
6. Residual risk accepted by the Human Principal MUST be written down with the reason and a review date.
Mechanism (status, refreshed 2026-11-12): council cadence (running, manual sessions); risk register v1 (approved 2026-11-05); access review checklist (task sheet exists; monthly run planned).
Public evidence: the live explorers (scryon.entropa.space, scryon-health.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public, aimozart/scryon-health-data, aimozart/scryon-council and aimozart/hippagrchealthcare. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
