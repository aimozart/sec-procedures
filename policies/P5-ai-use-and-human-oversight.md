# P5 AI use and human oversight (DRAFT)
Owner role: Human Principal. Supports: NIST AI RMF (Govern, Map, Measure, Manage) and the GenAI profile; ISO/IEC 42001; EU AI Act human-oversight and transparency ideas; HIPAA 164.308(a)(1) risk management; AIGP body of knowledge. Wording: aligned with.

1. Language models MUST be used only in the three approved places (clinic decision-support agent, audit explainer, bank fraud triage); everything else MUST be deterministic code. One model family per cloud (GCP Gemini Flash, AWS Nova family; Azure none); Titan embeddings only for the optional memory index, over closed-code text only.
2. A model MUST NOT receive PHI-equivalent or real personal data, secrets or canary tokens; inputs MUST be assembled by the deterministic context packer and its hash MUST be recorded in the decision event.
3. A model's output MUST be treated as untrusted data: closed-code outputs, schema validation, no tool authority beyond the Cedar and approvals gates. Retrieved precedents are evidence, never authority.
4. A human decision MUST be required for hard-rule actions (delete, spend, publish, credentials, billing); an agent's attestation MUST NOT satisfy them.
5. Every agent MUST have a model card, an AI impact assessment and a stated limit before it runs; the transparency statement MUST say what is automated and what a human decides.
6. Model reviewers (critic, contestor) MUST pass planted-fault tests before adoption and again after any change; a model that fails the bar MUST NOT be adopted.
7. A kill switch (signed halt) and circuit breakers MUST exist and be tested before any agent runs in the cloud.
8. The council MUST propose and never change production by itself; no quorum means no change.
Mechanism (status, refreshed 2026-11-12): Cedar gate and approvals (implemented); decision review council running with a critic, a contestor from a different model family, an orchestrator packet and the Human Principal's decision (first full session 2026-11-05); decision memory and agent harness (implemented 2026-11-05); independent auditor loop (three rounds run); model cards and kill switch (planned).
Public evidence: the live explorers (scryon.entropa.space, scryon-health.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public, aimozart/scryon-health-data, aimozart/scryon-council and aimozart/hippagrchealthcare. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
