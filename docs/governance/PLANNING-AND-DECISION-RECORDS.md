# Planning and decision records

Adopted 2026-11-12 by the Human Principal.

## Rule for every build stage
1. **Plan first.** The first commit of a stage is a plan file in the project repository: goal, forecast (the numbers expected), exit bar, cost cap, how it is turned off, what is out of scope.
2. **Approval.** The Human Principal approves the plan. The approval is a signed receipt in the evidence ledger. Until the Human Principal holds a signing key, the receipt is recorded by the Orchestrator on his stated word, and says so. That is a stated limit.
3. **Build.** Failing tests are committed on their own before the code that passes them. An independent review runs on a fresh copy.
4. **Outcome.** The stage ends with an outcome receipt: forecast against measured, pass or fail, and the commit. A failed bar is recorded as failed. Bars are not moved to make a result pass.
5. **Review.** The decision review council compares plan and outcome pairs. The Human Principal accepts or rejects its findings.

## Orders
Stage orders from the Orchestrator to the Builder are structured XML with fixed parts: context, goal, plan first, branch, tasks, constraints, cost, forecast, exit bar, stop and ask, report.

## Sessions
Agent sessions end at stage boundaries. State, milestones and a backup are saved before each break.

## Why
An outside analysis of our own working transcripts found decisions that were not checked against finished results. The fix uses the ledger we already run, not a new document.

## Evidence
Receipts recorded 2026-11-12 (run ids): `approval-triage-bars-v1`, `approval-triage-tenth-bar`, `approval-a4-go-cap-10usd`, `approval-plan-session-2026-11-12`, `approval-l1-llm-security-proof`.
