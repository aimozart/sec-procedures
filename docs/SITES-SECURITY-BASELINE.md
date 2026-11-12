# Security baseline: GCP, the three sites and administration (draft 1, 2026-11-12)

Scope: entropa.space (+ docs, scryon, scryon-health, scryon-council subdomains), hippagrchealthcare.site, bigironbank.online, the GCP project entropa-testnet, AWS and Azure footprints, GitHub. Written for a public reader after review: no account IDs, no emails, no balances. Wording: aligned with / mapped to HIPAA Security Rule, HITRUST (shape only), NIST AI RMF; not assessed, not certified. All data is synthetic.

Status key: DONE (verified on the date shown), PARTIAL, GAP (known, with the fix), N/A.

## 1. Who can administer what (identity and MFA)
| Area | Control | Status |
|---|---|---|
| Human accounts: Google Workspace, GitHub, AWS root and IAM, Azure, registrar, password manager, Anthropic, personal Gmail | Strong multi-factor authentication on every account (phone prompt, passkey or authenticator, vaulted and printed backup codes). No hardware keys; wording is "strong MFA", never "phishing-resistant" | DONE (owner statement, 2026-10-21) |
| Google Workspace | 2-Step enforced for all users, SMS and phone call excluded, super-admin recovery off, Security advisor all green | DONE (2026-10-21) |
| GCP project owners | One human Owner; Owner removed from the Firebase deployer service account | DONE (2026-10-21) |
| GCP session length | Re-authentication every 8 hours | DONE (owner setting, 2026-11-05) |
| AWS | Console and CLI use MFA-gated roles (auditor read-only, signer, scoped developer role); one legacy long-lived CLI key remains | PARTIAL: retire the key (needs the owner's word) |
| Agents | Each agent has its own identity, key and single role; separation of duties enforced by the approvals gate and Cedar policy (policy P3) | DONE in code; honest limit: one human operates all roles |

## 2. GCP (project entropa-testnet)
| Control | Status |
|---|---|
| Audit logs: Admin Activity (default) plus Data Access logs on IAM, KMS, Secret Manager and Vertex AI | DONE (2026-10-21) |
| Policy Analyzer enabled for last-use evidence on credentials | DONE |
| User-managed service-account keys: 14 found, 10 unused disabled (reversible), 4 recently used kept | PARTIAL: replace remaining keys with workload identity; delete only on the owner's word |
| CI to GCP without keys: GitHub Actions use Workload Identity Federation restricted to one repo and branch | DONE for the healthcare site publisher (2026-11-04) |
| Signing keys: ledger signs with Cloud KMS ML-DSA-65 (post-quantum signature), no key file | DONE (2026-11-05) |
| Default compute service account holds Editor | GAP: was held for the old GKE stack, which has since been deleted: re-check and right-size |
| Budget alerts and per-stage price check before anything billable | DONE as process; confirm alert thresholds on the GCP budget |
| DNS: Cloud DNS zones for all domains | DONE; DNSSEC is NOT enabled on any zone: GAP (needs a DS record at the registrar) |

## 3. The three sites (Firebase Hosting)
| Control | entropa.space and subdomains | hippagrchealthcare.site | bigironbank.online |
|---|---|---|---|
| HTTPS with managed certificates | yes | yes | yes |
| HSTS header | yes (about 1 year) | yes | yes |
| Content-Security-Policy, X-Content-Type-Options, X-Frame-Options, Referrer-Policy, Permissions-Policy | NOT SET | NOT SET | NOT SET |
| No logins, no forms storing data | yes (contact form posts to a rate-limited service; address never shown on pages) | yes (static plus read-only data) | yes |
| Deploys | scripted release from the live files with dry run and verification, rollback version printed | GitHub Actions, keyless, staging channel first, live only when the owner sets GO_LIVE | scripted release |
| Synthetic data only; export scans refuse secrets, identifiers, canary strings | n/a | yes (CI and exporter) | yes |

Measured 2026-11-12: all four hostnames checked return HSTS and no other security header. GAP and fix: add a `headers` block to each Firebase config (CSP tuned per site, nosniff, frame-ancestors none, strict referrer policy, restricted permissions policy). Needs a test pass in a browser per site because the pages use inline scripts and styles; then release behind a dry run.

## 4. GitHub (public repos)
| Control | Status |
|---|---|
| Secret scanning and push protection on all six public repos | DONE (verified 2026-11-12) |
| main protected by an active ruleset (no deletion, no force push) on all six | DONE (verified 2026-11-12) |
| Interaction limit "collaborators only" (set 2026-11-05, expires 2027-05-05) | DONE: renew before expiry |
| Actions default token read-only | DONE (healthcare repo verified) |
| Squash-only and delete-branch-on-merge | PARTIAL: on for three repos; entropa-public, aimozart and MegaMart still allow merge commits |
| CI: tests, export scan, gitleaks over full history, SHA-pinned actions, Dependabot | DONE for the healthcare repo; check the others |
| Commit authorship: Mr. Spock credited by trailer; earlier commits carry the generic trailer | known, history not rewritten |

## 5. AWS and Azure footprint
AWS: one multi-region CloudTrail trail with log-file validation, MFA-gated roles, one KMS signing key, one witness Lambda with a scoped role and boundary, budget alerts. Azure: witness and council resources inside one resource group each, spending limit on, credit ends 2026-11-16, teardown only on the owner's exact word. Never run AWS Organizations; never upgrade a credit account.

## 6. Open items, ranked
1. Security headers on all three sites (GAP, quick win, visible to anyone who scans the sites).
2. Retire the AWS CLI key; replace remaining GCP SA keys with workload identity.
3. DNSSEC on the Cloud DNS zones (registrar DS records).
4. Re-check Editor on the default compute service account now the GKE cluster is gone.
5. Squash-only on the three older repos; verify CI on them.
6. Capture evidence (signed receipts) for each row above so the public page links proof, not claims.

## 7. Verification commands (read-only)
- Headers: `curl -sI https://HOST | grep -i -E "strict-transport|content-security|x-frame|x-content-type|referrer|permissions"`
- Repos: `gh api repos/OWNER/REPO --jq '.security_and_analysis'`; `gh api repos/OWNER/REPO/rulesets`
- DNS: `gcloud dns managed-zones list --project entropa-testnet --format="value(name,dnssecConfig.state)"`
- Keys: `gcloud iam service-accounts keys list --iam-account SA --managed-by=user`
