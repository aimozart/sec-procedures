# P4 Audit logging and integrity (DRAFT)
Owner role: Orchestrator (drafts), Human Principal (approves). Supports: HIPAA 164.312(b) audit controls, 164.312(c)(1) integrity, 164.308(a)(1)(ii)(D) information system activity review; HITRUST logging/monitoring and integrity categories; NIST AI RMF Measure/Manage; ISO/IEC 42001 monitoring clauses. Wording: aligned with, never certified.

1. Every AI decision, approval, policy change and operational event MUST be recorded as a data-minimal signed ledger event (event type, actor key, subject hash, outcome, reference; never conversation text, secrets, personal or health data).
2. The ledger MUST be append-only and checkpointed with a post-quantum signature (ML-DSA-65); a witness MUST countersign checkpoints so the operator cannot silently rewrite history.
3. Each agent's local tool-use audit (hook audit file) MUST be hash-chained, MUST be verified before it is trusted, and only its chain-head hash is anchored in the ledger.
4. Cloud audit logs MUST be on and kept: AWS CloudTrail (multi-region trail with log-file validation) and GCP Admin Activity plus Data Access logs for IAM, KMS, Secret Manager and Vertex AI.
5. Logs MUST NOT contain secrets, canary tokens or PHI-equivalent values; the canary scan MUST pass before any log or evidence is published.
6. Log review MUST happen at least weekly (the council cycle) and after every incident; a failed chain verification MUST open an incident (P6).
7. Honest limit MUST be stated: the ledger proves recorded events were not altered, not that nothing was omitted.
Mechanism (status, refreshed 2026-11-12): signed Merkle ledger with checkpoints signed by a managed post-quantum key, independent witnesses on two clouds, and public explorers with in-browser verification (deployed 2026-11-05); hook audit chain with a verify script (implemented, enforcing); CloudTrail trail and GCP Data Access logs (applied 2026-10-21). Gap: only one of three ledgers is witnessed (shared signing key).
Public evidence: the live explorers (scryon.entropa.space, scryon-health.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public, aimozart/scryon-health-data, aimozart/scryon-council and aimozart/hippagrchealthcare. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
