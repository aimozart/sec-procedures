# P12 Training and awareness (DRAFT)
Owner role: Human Principal (sets), Orchestrator (maintains). Supports: HIPAA 164.308(a)(5) security awareness and training; HITRUST education/training/awareness; NIST AI RMF Govern; ISO/IEC 42001 competence and awareness clauses. Wording: aligned with.

1. Every actor (human or agent) MUST operate under a written rule pack for its role before it starts work (standing rules, hard rules, role limits); for agents the rule pack MUST be versioned and its hash recorded.
2. Hard rules MUST be restated at each session start and MUST be enforced in code as well (permission rules, the hook, Cedar), never by instruction alone.
3. Every incident, near miss and review finding MUST become a lesson (LESSONS.md) and, where testable, a red test or a rule; lessons MUST be reviewed at the monthly retrospective.
4. New agents MUST get an onboarding checklist: role, permissions, what they must never touch, how to report a problem.
5. The Human Principal MUST be told plainly what each control does and what it does not (honest limits), in short written form.
6. Awareness material (the book, the policy set, the public evidence) MUST use role names, MUST NOT include secrets or personal data, and MUST be reviewed before publication.
Mechanism (status): CLAUDE.md rule sets, standing orders, state saves every two hours (implemented), LESSONS and STANDARDS (implemented), onboarding checklist (planned), the book (in progress).
Public evidence: the live explorers (scryon.entropa.space, scryon-health.entropa.space, scryon-council.entropa.space), docs.entropa.space, and the public repos aimozart/entropa-public, aimozart/scryon-health-data, aimozart/scryon-council and aimozart/hippagrchealthcare. Entropa's source code is private by decision; its behaviour is verifiable through the signed public ledgers and the in-browser verifier.
