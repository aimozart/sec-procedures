# Google Cloud controls (project entropa-testnet)

Right-sized for a small footprint: Cloud Run services that scale to zero, Cloud Storage, Cloud KMS, Secret Manager, Vertex AI (Gemini), Cloud DNS and Firebase Hosting for static pages. Synthetic data only. Account identifiers and emails are deliberately not published.

## Identity and access
- One human principal holds Owner; every service account has a single purpose. The Firebase deployer lost its Owner role (2026-10-21).
- Console and CLI sessions re-authenticate every 8 hours (owner setting).
- Services use attached identities, not key files. CI authenticates through Workload Identity Federation restricted to one repository and branch (healthcare site publisher, 2026-11-04): no long-lived key.
- Of 14 user-managed service-account keys found, 10 unused ones are disabled (reversible) and 4 recently used ones remain until replaced; deletion only on the owner's explicit word. Remaining work: replace the four with workload identity.
- IAM Recommender and Policy Analyzer are used to find over-broad roles and last-used credentials.

## Logging and detection
- Admin Activity logs (default) plus Data Access logs on IAM, KMS, Secret Manager and Vertex AI (enabled 2026-10-21).
- Policy Analyzer API on. The ledger of our own AI decisions is separately signed and witnessed.

## Keys and cryptography
- The ledger signs checkpoints with a Cloud KMS ML-DSA-65 key (a post-quantum signature); the private key never leaves KMS. Witnesses on two other clouds co-sign checkpoints.
- Secrets live in Secret Manager; none in repositories (secret scanning, push protection and full-history scans in CI).

## Data and AI
- Only synthetic data. Gemini calls use closed-code, data-minimal inputs; model output is validated by deterministic checks and a policy gate before any action.
- Services used for anything that could touch protected data must be on Google's covered-products list, checked and dated per stage. Where product naming is unclear, inputs stay closed-code.
- Public pages (Firebase Hosting) hold static synthetic content only.

## Cost and account safety
Budget alerts are set; anything billable needs a stated price and teardown first; the account is never upgraded or converted; deletes need the owner's exact word and a separate yes/no.

## Known gaps (dated 2026-11-12)
1. The default compute service account still holds the Editor role (kept for a cluster that has since been removed): re-check and right-size.
2. Four service-account keys remain: move to workload identity.
3. DNSSEC is not enabled on the Cloud DNS zones.
4. No security headers other than HSTS on the Firebase sites (CSP, nosniff, frame protection, referrer and permissions policies to add).
5. Confirm budget-alert thresholds on the GCP budget.
