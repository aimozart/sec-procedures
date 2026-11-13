# P3 Access control and separation of duties (DRAFT)
Owner role: Human Principal. Supports: HIPAA 164.308(a)(3),(a)(4) workforce security and access management, 164.312(a)(1),(d); HITRUST access control and segregation-of-duties requirements; NIST AI RMF GOVERN; ISO/IEC 42001 roles and responsibilities. Alignment, not certification.

Principle (Human Principal, 2026-10-21): we are a solo human with individual agents; each agent is treated as its own role-holder with its own identity, key and permissions. Separation of duties is technical (enforced by the gate and the ledger), plus the Human Principal as final authority for hard-rule actions.

1. Every agent and service MUST have its own identity (a handle and a key) and a single role. Shared identities MUST NOT exist.
2. An actor MUST NOT approve, review or merge its own work. The same key MUST NOT be both requester and approver of one action (enforced by the approvals gate).
3. Conflicting roles MUST NOT be held by the same actor (matrix below).
4. Hard-rule actions (delete, spend, publish, credentials, billing) MUST require the Human Principal's own decision; an agent's attestation MUST NOT open them.
5. Role changes and key issuance or revocation MUST be recorded as signed ledger events.
6. The honest limit MUST be stated publicly: all actors are operated by one human, so independence comes from the technical gates, different model families for review (critic, contestor), the signed audit trail, and the human's final authority; it is not organizational independence.

| Role (public handle) | May | MUST NOT |
|---|---|---|
| builder-agent | write code and tests on branches, run local checks | approve or merge its own work, publish, spend, change permissions, delete without the human's word |
| orchestrator-agent | order work, review on fresh copies, accept or reject stages, keep notes | write production code, approve its own orders, publish, spend |
| critic / contestor (model reviewers) | submit findings and rebuttals with evidence | change production, approve anything |
| operator-agent (when created) | deploy approved artifacts, run runbooks | approve spend or publishing, change policy |
| log-signer, witness, generator | sign or produce data within their narrow function | read secrets of other actors, approve actions |
| human-principal | decide hard-rule items, approve policy, issue and revoke keys | (the only holder of final authority) |
Public evidence: the live explorers (scryon.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public and aimozart/scryon-council. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
