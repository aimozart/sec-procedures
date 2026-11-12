# HIPAA Security Rule alignment, with synthetic data

**Scope.** Our systems process only synthetic data, so HIPAA does not legally apply to them. We align to the Security Rule anyway and treat synthetic data as protected health information under written procedures, so the safeguards are real, tested and demonstrable. If real PHI ever appeared, we would stop and run the incident procedure; before any real PHI, a signed business associate agreement with each cloud provider would come first.

**Why do it with fake data?** A control you have never exercised is a claim. Treating mock data as real forces the same discipline (access control, minimum necessary, logging, disposal, incident handling) and gives a reviewer something concrete to inspect.

Source of the safeguard list: the Security Rule text (45 CFR 164 Subpart C, sections 164.308, .310, .312, .314, .316), read from a public mirror; re-check wording against the official source before relying on it. R = required, A = addressable. Status as of the dates shown; see the baseline page for the latest.

## Administrative safeguards (164.308)
| Safeguard | Our mechanism | Status |
|---|---|---|
| Risk analysis and management | threat tables in design docs; risk register v1 approved 2026-11-05; guardrails (Cedar gate, approvals, hook, rate limits, fail-closed) | implemented / partial |
| Sanction policy | key revocation and role removal for agents and humans (P3) | planned (document) |
| Information system activity review | signed ledger, hook audit chain, weekly council cycle | implemented |
| Assigned security responsibility | the Human Principal (P1) | documented |
| Workforce security and access management | per-actor keys, actor directory, Cedar policies, approvals | implemented |
| Awareness and training | rule packs, hook messages, lessons log | partial |
| Incident response | P6; restore test done 2026-11-05; drill planned | partial |
| Contingency plan | backups to two private mirrors plus encrypted copies; restore test; kill switch planned | partial |
| Evaluation | check scripts, mutation tests, council, independent auditor rounds | implemented |
| Business associate contracts | not applicable (no real PHI); required first if that changes | N/A |

## Physical safeguards (164.310)
Data-centre controls are provider-attested and inherited. Workstation use and security (disk encryption, screen lock, updates), media disposal and re-use are documented in procedures P9 and P11 and are being inventoried.

## Technical safeguards (164.312)
| Safeguard | Our mechanism | Status |
|---|---|---|
| Unique user identification | one key and handle per actor | implemented |
| Emergency access | break-glass procedure for the Human Principal | planned |
| Automatic logoff | session expiry in tools and cloud consoles (8-hour GCP re-authentication) | partial |
| Encryption at rest | provider-managed encryption, KMS keys; local disk encryption to verify | partial |
| Audit controls | signed hash-chained ledger, witnesses on two clouds, CloudTrail, GCP Data Access logs | implemented |
| Integrity | ML-DSA-65 signatures, Merkle log, witness co-signatures, in-browser verifier | implemented |
| Person or entity authentication | keys for agents; strong MFA on every human account | implemented |
| Transmission security | TLS on every endpoint, signed payloads | implemented |

## Organizational requirements and documentation (164.314, 164.316)
Policies P0-P12 are written, approved and public; documentation is kept in version control with dates; review is quarterly.

## Minimum necessary and data handling
Event records hold only event type, actor key, a hash of the subject, outcome and a reference, never free text or data values. Identifier-shaped values come from reserved invalid ranges; canary strings are checked for leakage in prompts, logs, ledger events and public pages (P0, P2, P9).

## Provider services and eligibility
We use only services on each provider's own HIPAA-eligible or covered list for anything that could touch protected data, check those lists per stage with a dated record, and keep public pages to static synthetic content. Items where a provider's naming is unclear (for example some model services) are treated conservatively: closed-code inputs only. Providers cover security of the cloud; configuration, access, logging, encryption settings and AI oversight are ours (shared responsibility).
