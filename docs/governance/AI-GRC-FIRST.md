# AI governance, risk and compliance first

Our order of work is: **safety and governance foundations first, features on top.** Nothing is deployed publicly or to a cloud until the foundation gate passes. This page explains the principles, the frameworks we map to, and how governance is enforced in code.

## 1. Principles
1. **Data safety first, always, even when the data is fake.** Synthetic data is handled under written procedures as if it were real, so the controls are demonstrated end to end. No real patient or customer data is ever used.
2. **Prove it, don't tell me.** Each control has a mechanism, evidence anyone can inspect, and an honest status (implemented, partial, planned, inherited, not applicable).
3. **Zero trust all the way around.** No actor, agent, network or tool is trusted because of where it runs; every action is authenticated, authorised and recorded.
4. **Transparency.** Policies, controls and evidence are public. Gaps are listed, not hidden.
5. **Humans decide the irreversible.** Deletion, spending, publishing, credentials and billing always need the human principal.

## 2. Frameworks we align to
| Framework | How we use it |
|---|---|
| HIPAA Security Rule | the safeguard list we map every control to (see compliance/HIPAA-WITH-SYNTHETIC-DATA) |
| HITRUST CSF (shape of e1 and i1) | requirement-level mapping per platform, our own words (see compliance/HITRUST-ALIGNMENT) |
| NIST AI RMF and its generative AI profile | GOVERN, MAP, MEASURE, MANAGE structure for AI risk |
| ISO/IEC 42001 | AI management system controls: roles, oversight, lifecycle |
| EU AI Act (logging and oversight themes) | record-keeping and human oversight design |
| IAPP AIGP body of knowledge | AI governance vocabulary and checklist (a personal credential, not a standard) |
Wording rule: **aligned with, mapped to**. Never "compliant" or "certified" unless an assessor says so. A certificate would be third-party evidence of a claim; it does not create controls, and its absence does not mean ours do not exist.

## 3. Enforcement is in code, not in the prompt
Governance rules are given to agents as rule packs, but enforcement sits in systems that do not depend on the model behaving: the Cedar policy gate, the approvals gate with no self-approval, the PreToolUse hook, output guardrails with closed-code outputs, human gates, and kill switches. See architecture/AI-HARNESS-AND-GUARDRAILS.

## 4. The foundation gate
Public deployment waits for: data-safety tests green; the policy set approved; a controls map with evidence paths and honest gaps; per-cloud least-privilege baselines; a tested kill switch and circuit breakers; the hook in enforce mode; model cards and impact assessments for each AI agent; one incident drill. Status of each item is tracked openly in the baseline page.

## 5. Independent review
- A decision review council (critic and contestor from different model families, an orchestrator packet, the human's decision) reviews recorded AI decisions weekly. No quorum means no change.
- An auditor agent, read-only and from a different model family, audits controls against HIPAA and the shape of HITRUST in rounds (baseline, findings, remediation, retest). It is tested with planted gaps. Reports use our control IDs and our words, and carry the honest label "independent AI-assisted readiness assessment", never "HITRUST assessment" or "HIPAA audit".

## 6. Cross-cutting rules
Post-quantum signatures for long-lived integrity (ML-DSA), AES-256 at rest, strong multi-factor authentication on every human account (we say "strong MFA", not "phishing-resistant"), short-lived credentials for agents, a cryptographic inventory, and a policy set (P0-P12) reviewed quarterly.
