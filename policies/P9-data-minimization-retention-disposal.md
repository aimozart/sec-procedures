# P9 Data minimization, retention and disposal (DRAFT)
Owner role: Human Principal. Supports: HIPAA 164.312(a)(2)(iv) encryption, 164.310(d)(2) disposal and media re-use, 164.316(b)(2) documentation retention; HITRUST data protection and privacy categories; NIST AI RMF Map/Manage; ISO/IEC 42001 data clauses. Wording: aligned with.

1. Systems MUST collect and keep the minimum: ledger events carry codes, hashes and references only; no conversation text, secrets, personal or health data.
2. Mock PHI MUST be synthetic, generated on demand from a seed, stored as little as possible, and labelled; identifier-shaped values MUST come from reserved invalid ranges.
3. Retention: audit evidence and policy documents MUST be kept at least six years (HIPAA documentation period) once the system is live; synthetic working data MUST be discarded after use; the ledger is append-only and holds no personal data.
4. Data at rest MUST be encrypted (AES-256 with managed or customer-managed keys) and data in transit MUST use TLS; hybrid post-quantum key exchange SHOULD be used where the service supports it.
5. Backups MUST be encrypted, and restore MUST be tested at least once before Gate G1 and then quarterly.
6. Disposal (deleting data, buckets, keys, accounts) MUST follow the hard rule: the Human Principal names the exact item and answers a standalone yes/no first; disposal MUST be recorded.
7. Logs and evidence for publication MUST be masked (account IDs, ARNs with numbers, device lists) and scanned before release.
Mechanism (status): data-minimal event schemas and canary scans (implemented), encryption defaults (S3 SSE, KMS), backups (state backup to Gitea and laptop running), restore drill (planned), retention setting per store (to define at deployment).
Public evidence: the live explorers (scryon.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public and aimozart/scryon-council. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
