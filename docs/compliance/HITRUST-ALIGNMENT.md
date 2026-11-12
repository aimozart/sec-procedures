# HITRUST alignment

**Status wording (fixed).** Controls implemented and evidenced by us (signed, public, verifiable); aligned with the shape of HITRUST e1 and i1; **not independently assessed, not certified.** HITRUST's materials are licensed: we do not reproduce requirement text, and our mapping uses our own control IDs and words. We are aware of and follow HITRUST's usage terms.

## Scope: one baseline, deepest where the data path is
| Platform | Depth |
|---|---|
| AWS | deepest: i1-style subset covering the data path, ledger signer and explainer |
| Google Cloud | deep on the public explorer and the analytics and bank data paths (i1-style) |
| Azure | light: e1-style essentials for the witness only; out of scope after its credit ends |
| GitHub and agent tooling | in the baseline (access, change management, supply chain) |

The shared baseline is e1-style essentials plus the HIPAA Security Rule plus our policies P0-P12.

## What inheritance really covers
HITRUST publishes shared-responsibility inheritance data for the major clouds. Our reading, in our own words: of roughly 3,300 baseline requirements, only about 15 percent can be fully or partly inherited from a given provider, and roughly 19 percent were tested in the provider's own assessment. So most requirements are ours. We inherit only what the provider marks as inheritable for the services in scope, and for every partial inheritance we document what the provider does and what we do. Inheritance applies only to services the provider's assessment covers; we check that before claiming anything.

## The controls map
Each control carries: framework reference, our mechanism, evidence path, status (implemented, partial, planned, inherited, not applicable), and an owner role. A governance check in the build fails if a policy statement has no mapped mechanism or if forbidden wording ("compliant", "certified") appears on a public page.

## Independent readiness loop
An auditor agent from a different model family, read-only, audits our controls in rounds. It reports against our control IDs, is tested with planted gaps, and never fixes or approves its own findings; the Human Principal decides. Reports follow a real audit layout (scope, method, sampling, findings with severity, management response, remediation, retest, residual risk) and are labelled as AI-assisted readiness assessments.

## Why a certificate is not the goal
A certificate is third-party evidence of a claim. It does not create the controls and its absence does not mean they are missing. We publish the controls and their evidence so a reader, or an assessor, can check them directly.
