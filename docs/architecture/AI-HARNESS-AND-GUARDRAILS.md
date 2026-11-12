# How we work with Claude Code: harness and guardrails

We build with AI agents every day. This page describes the control system around them: what each agent may do, what stops a mistake, and what proves afterwards what happened. The design rule is **mechanisms over claims**: every guardrail is code or configuration that can be tested, not a sentence in a prompt.

## 1. Roles (separation of duties)
One human, several AI roles, each with its own identity and a single job.
| Role | Does | Must not |
|---|---|---|
| Human Principal | decides every hard-rule action, approves policy, issues and revokes keys | (final authority) |
| Orchestrator (this session type) | writes orders, reviews every stage on a fresh copy, accepts or rejects, keeps state | write production code, approve its own orders, publish, spend |
| Builder | writes code and tests on short-lived branches | merge or approve its own work, publish, spend, change permissions |
| Critic and contestor (model reviewers from different model families) | file findings and rebuttals with evidence | change production |
| Operators, signers, witnesses | narrow functions with their own keys | approve actions |

Honest limit: one human operates all roles, so this is technical separation, not organizational independence. Independence comes from the gates below, reviewers from different model families, the signed audit trail and the human's final authority.

## 2. The layers
```
rule packs and standing orders                   what the agent is told
permission settings (allow / ask / deny)        what the tool lets it try
PreToolUse hook (runs before every tool call)  what is blocked or escalated
approvals gate + Cedar policy                   who may approve what (no self-approval)
human gates                                     deletes, spend, publishing, credentials, billing
signed audit trail + witnesses                  proof of what happened, tamper-evident
council review (critic, contestor, human)       weekly review of decisions and outcomes
```
No single layer is trusted alone. A prompt rule can be ignored; a hook, a gate and a signed record cannot be quietly skipped.

## 3. The hook (enforcement on the agent's own tool calls)
A PreToolUse hook runs before every Claude Code tool call. Principles:
- It only tightens: it returns deny, ask or nothing, never allow. Silence hands the call back to the normal permission rules.
- Classification is a pure function of the call, tested with unit tests, fuzzing and mutation testing.
- It complements, not replaces, the permission rules: the rules match command text, the hook also catches wrappers and rewrites (`bash -c`, absolute paths, flags after the refspec, interpreter one-liners, `xargs`, launchers).
- Observe mode first: it recorded what it would have decided for a trial period, was reviewed for false positives, and only then switched to enforce.
- It is a guard against mistakes, not a sandbox. A determined actor with shell access is out of scope; the signed trail makes bypasses visible instead.

What it denies or escalates (classes, not the full rule table): destructive deletes and cloud deletes (deny); force pushes, pushes to unreviewed remotes and merges (deny or ask); account, billing and plan-upgrade actions (deny); anything that creates billable resources or publishes (ask); secret paths such as cloud credentials and key files (deny); text shaped like a personal identifier (deny); piping downloads into a shell (deny); privilege elevation and unparseable commands (ask); edits to rule files and policy (ask: a human gate).
Every decision appends a line to a hash-chained audit log holding hashes only, never command text. A verify script checks the chain.

## 4. Permissions and tools
- Settings carry explicit allow and deny lists per project; the deny list covers force pushes, destructive git, recursive deletes and credential paths.
- MCP servers are read-only by design (stdio, a small fixed tool set, size-bounded inputs, fuzzed). They answer questions; they cannot act. Enforcement is the hook's job.
- Agents work on short-lived branches, one pull request per stage, squash-merged by the human.

## 5. How work flows
1. The orchestrator writes an order: scope, hard rules, tests to write first, what to report.
2. The builder writes failing tests, shows them failing for the stated reason, then implements, then runs the full gate (format, lint, tests, dependency and secret scans).
3. The orchestrator re-runs the gate on a fresh copy, probes the built binary or page independently, and accepts or sends changes back. Review findings are recorded.
4. The human approves anything on the hard-rule list. No agent's say-so opens it.
5. State files are saved after each task and at least every two hours, and backed up off the machine, so a context reset loses nothing that was decided.

## 6. Data safety is the first priority
All data is synthetic, labelled, generated from a seed where possible, and built from reserved invalid ranges so a value can never match a real person (see policy P0). Canary strings are planted and automated checks fail if one ever appears in a prompt, log, ledger event or public page. Agents see closed-code, data-minimal inputs. Every stage review asks: could this leak or look like real data?

## 7. Cost and credentials
Anything billable needs a stated price, a teardown plan and the human's go first. Cloud credit accounts are never upgraded or converted. Agents use short-lived scoped credentials and workload identity where possible; no long-lived keys in files, prompts or chat.

## 8. What the guardrails do not prove
They show that an agent stayed inside its permissions and that the record is unaltered. They do not prove an agent's answer was correct. Correctness is measured separately: evaluation sets with planted bad cases, human review, and published error rates.
