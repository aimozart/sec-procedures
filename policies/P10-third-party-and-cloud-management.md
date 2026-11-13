# P10 Third-party and cloud provider management (DRAFT)
Owner role: Human Principal. Supports: HIPAA 164.308(b) business associate contracts, 164.314(a); HITRUST third-party assurance and inheritance; NIST AI RMF Govern; ISO/IEC 42001 supplier clauses. Wording: aligned with, never claims a provider's attestation as ours.

1. Shared responsibility MUST be stated plainly: providers secure the cloud; we secure what we configure in it (identity, encryption, logging, network, backups, AI oversight). Compliance is never claimed as inherited as a whole.
2. Only services on the provider's HIPAA-eligible or covered list MAY be used for PHI-equivalent data, and each service MUST be checked before use and quarterly (AWS, Google, Azure lists; Gemini on Vertex treated as covered per the Human Principal; Nova and Titan not named on AWS's list, so no PHI-equivalent text goes to them and the check is repeated).
3. If real PHI ever appears, a signed business associate agreement with each provider MUST exist first.
4. Inherited controls MUST be documented from the provider's attestation (for example the HITRUST shared-responsibility workbooks, used privately under their licence) and our own configuration MUST be evidenced separately in the controls map.
5. Each provider account MUST have a spend limit or budget alert, strong MFA, a recorded owner, and no standing broad keys.
6. Provider and model changes (deprecations, new model versions, price changes) MUST be reviewed before adoption, with the planted-case suite re-run for models.
7. Free-credit accounts MUST never be upgraded; credit expiry dates MUST be tracked and teardown planned before they end.
Mechanism (status): HIPAA eligibility check (done 2026-10-21), cloud inventories (AWS, GCP done; Azure pending), budgets (AWS alerts set; GCP/Azure to confirm), controls map (S14a).
Public evidence: the live explorers (scryon.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public and aimozart/scryon-council. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
