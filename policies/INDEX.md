# Policy set (DRAFT, private until the Human Principal approves publishing)

Operating principles (Human Principal, 2026-10-21): **transparency, prove-it (not tell-me), zero trust all the way around.** Synthetic HIPAA data is treated as real under the SOPs, so the controls, policies and evidence can be demonstrated end to end. No real PHI ever enters any system.

Rules for every policy in this folder:
1. **One page, plain words, testable statements** (MUST / MUST NOT, each checkable). No decorative policy: if we cannot show evidence that we follow it, it does not ship.
2. **Each policy lists** its owner role, the controls it supports (HIPAA Security Rule citation, HITRUST CSF category, NIST AI RMF function, ISO/IEC 42001 clause where relevant), the mechanism in code that enforces it, and the evidence path (a file or a command anyone can re-run).
3. **Aligned, not certified.** Wording: "aligned with" / "mapped to". Never "compliant" or "certified" unless earned.
4. **Public naming by role**, never crew names. Drafts by the Orchestrator, approved by the Human Principal, signed into the ledger as `policy.published` events when published.
5. Publishing any policy is the Human Principal's decision.

**P0 (top priority, Human Principal 2026-10-21): patient and client data and information safety comes first, always, even when the data is mocked. It overrides convenience, speed and demo polish.**

## Index (status)
| # | Policy / SOP | Status |
|---|---|---|
| P0 | Patient and client data safety first (synthetic data, reserved invalid ranges, canaries) | APPROVED 2026-10-21 (internal; not published) |
| P1 | Zero-trust principles (verify explicitly, least privilege, assume breach) | APPROVED 2026-10-21 (internal; not published) |
| P2 | Mock-PHI handling SOP (synthetic data treated as real) | APPROVED 2026-10-21 (internal; not published) |
| P3 | Access control and separation of duties (agents as role-holders, role matrix) | APPROVED 2026-10-21 (internal; not published) |
| P4 | Audit logging and integrity (signed ledger, witness, hook audit) | APPROVED 2026-10-21 (internal; not published) |
| P5 | AI use and human oversight (gates, council, contestor) | APPROVED 2026-10-21 (internal; not published) |
| P6 | Incident response and breach notification (simulated drills) | APPROVED 2026-10-21 (internal; not published) |
| P7 | Risk analysis and review cadence (weekly council, monthly retro) | APPROVED 2026-10-21 (internal; not published) |
| P8 | Change management (red-green, independent review, evidence) | APPROVED 2026-10-21 (internal; not published) |
| P9 | Data minimization, retention and disposal | APPROVED 2026-10-21 (internal; not published) |
| P10 | Third-party and cloud provider management (shared responsibility, inheritance) | APPROVED 2026-10-21 (internal; not published) |
| P11 | Secrets and key management | APPROVED 2026-10-21 (internal; not published) |
| P12 | Training and awareness (crew rule packs, book) | APPROVED 2026-10-21 (internal; not published) |
