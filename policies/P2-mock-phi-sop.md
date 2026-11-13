# P2 Mock-PHI handling SOP (DRAFT)
Owner role: Human Principal. Supports: HIPAA 164.308(a)(1) risk management, 164.312(a)/(e) access and transmission, minimum-necessary 164.502(b); HITRUST data-protection categories. Alignment, not certification.

Purpose: all patient-like data in our systems is **synthetic**, but it is handled as if it were real, so every control can be demonstrated honestly.
1. Synthetic records MUST be labelled synthetic in the data and on every page that shows them (`synthetic: true`). Real PHI or real customer data MUST NOT enter any system, ever; if suspected, stop and run the incident SOP (P6).
2. Synthetic PHI-shaped data MUST be classified as PHI-equivalent: access only through the gate, encrypted in transit and at rest, never in logs, prompts or ledger events beyond closed-code fields and hashes (minimum necessary).
3. Agents MUST see only what the task needs; the ledger MUST hold only event type, actor handle, subject hash, outcome and reference.
4. Test fixtures MUST be generated at run time where they look like identifiers (SSN/MRN-shaped), so scanners and reviewers do not mistake them for real data.
5. Every access to PHI-equivalent data MUST be an audited, authorized event; any denied or anomalous access MUST appear in the weekly council packet.
6. Disposal: synthetic datasets MUST have a stated retention and a documented disposal step approved by the Human Principal (no deletion without his word and a separate yes/no).
Public evidence: the live explorers (scryon.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public and aimozart/scryon-council. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
