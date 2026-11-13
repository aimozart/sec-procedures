# P1 Zero-trust principles (DRAFT)
Owner role: Human Principal. Supports: HIPAA 164.312(a)(1) access control, 164.312(c) integrity, 164.312(d) authentication; HITRUST CSF access control and audit categories; NIST AI RMF GOVERN/MANAGE; ISO/IEC 42001 operational controls. Alignment, not certification.

1. **Verify explicitly.** Every action by a person, an agent or a service MUST be authenticated and authorized at the moment it happens (Cedar gate + approvals). Nothing is trusted because of where it runs or who ran it before.
2. **Least privilege.** Every actor MUST have its own key and the minimum rights for its role. Standing broad credentials MUST NOT exist; cloud calls use short-lived or narrowly scoped access.
3. **Assume breach.** Every control MUST fail closed. Logs MUST be tamper-evident (signed, hash-chained, witnessed). Guardrails (the Claude Code hook, Cedar, rate limits) assume an agent can be wrong or manipulated.
4. **Prove it.** A claim about a control MUST come with evidence a stranger can re-run (a test, a verifier, a ledger proof). "Trust us" statements MUST NOT be published.
5. **Transparency by default.** Decisions, approvals, denials and policy changes MUST be recorded as data-minimal signed events and, for the demo, publicly verifiable.
6. **Separation of duties.** Nobody approves their own work. Hard-rule actions (delete, spend, publish, credentials, billing) need the Human Principal's own word.
Public evidence: the live explorers (scryon.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public and aimozart/scryon-council. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
