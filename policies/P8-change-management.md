# P8 Change management (DRAFT)
Owner role: Orchestrator (reviews), Human Principal (approves release). Supports: HIPAA 164.308(a)(8), 164.312(c); HITRUST change/configuration management; NIST AI RMF Manage; ISO/IEC 42001 operational controls. Wording: aligned with.

1. Every change MUST be test-first (red, then green) and the red state MUST be shown to fail for the stated reason; tests written against a stub MUST be checked against a deliberately broken implementation.
2. Every stage MUST be reviewed independently by a different role on a fresh checkout; the author MUST NOT accept its own work.
3. Changes to accepted tests MUST be separate commits with the reason stated and MUST NOT remove or weaken an assertion without approval.
4. Nothing reaches a protected branch except by pull request with passing checks; force pushes and branch deletions on protected branches MUST be blocked; actions MUST be pinned by commit hash.
5. Deployment to any cloud or public surface MUST wait for Gate G1 and the Human Principal's word; every deployment MUST have a runbook, a rollback and a recorded decision.
6. Dependency, container and workflow changes MUST pass scanning (gitleaks, cargo deny/audit, SBOM) and MUST NOT introduce unpinned inputs.
7. Emergency changes MUST still be recorded afterwards with the same evidence.
Mechanism (status, refreshed 2026-11-12): check script gate, enforcing hook and review procedure (implemented); main-branch rulesets active on all six public repositories (verified 2026-11-12); CI with secret scanning on the healthcare repository; per-module pipelines with signed receipts.
Public evidence: the live explorers (scryon.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public and aimozart/scryon-council. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
