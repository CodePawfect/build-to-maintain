# Refactor a project

Describe what feels hard to change, or simply ask the agent to find the most worthwhile improvement. It investigates the code and protects existing behavior.

**Try this:** “This project has become hard to change. Find the most useful cleanup and implement it without changing how the app works.”

Replace `Request` below. You do not need to name a file, architecture or code smell. An agent needs repository, shell and web access; user-facing changes also need browser verification.

```text
Request: [describe the maintenance problem, or use "Find and fix the most worthwhile maintainability problem"]
Optional limits: [areas to focus on or leave alone; otherwise choose one bounded change]

Own the diagnosis, implementation and verification. Discover technical details
instead of asking me for an architecture. State reversible assumptions and proceed;
ask only when an unresolved behavior decision would materially change the result.
Follow repository instructions and permissions; preserve unrelated local work.

1. Find the change worth making.
Identify frameworks, dependencies, resolved versions, conventions and validation
commands from manifests, lockfiles, runtime files and CI. If I gave a target,
trace it. Otherwise inspect representative entry points and up to three likely
problem areas. Use concrete evidence: duplicated policy, changes spreading across
unrelated modules, mixed responsibilities or rules buried in difficult control
flow. Do not rank candidates by file length or personal style alone.

Choose one bounded improvement using likely change benefit, behavior risk and
verification cost. Show the source locations and a future change it simplifies.
Example: a shipping rule is repeated in two handlers; centralize that policy
while preserving each endpoint's response. If there is no justified improvement,
explain the evidence and leave the code alone. Do not manufacture cleanup.

2. Protect the behavior before moving it.
Trace callers, rules, persistence and side effects. Run relevant baseline checks.
Map at-risk contracts to checks: inputs/outputs, errors, authorization, rounding,
ordering, retries, transactions and side effects where applicable. Add focused
characterization coverage before risky changes when existing checks are missing.
Use current behavior and established contracts to determine expected results.
If they conflict, resolve that uncertainty before the affected move. Record bugs
separately; do not silently fix them or update expected outputs to bless drift.

Research consequential choices in official documentation for the actual versions.
Cite the applicable idiom and distinguish it from judgment or unverified guidance.
Keep cohesive responsibilities together. Extract a named rule when it lowers
cognitive load at the caller; keep effects explicit. For complex larger backends,
prefer an independent domain, inner-owned ports, outer adapters and edge wiring.
Keep simple CRUD framework-native. Avoid speculative layers, forwarding wrappers,
unrelated upgrades and broad rewrites.

3. Refactor, then try to disprove equivalence.
Move one slice at a time and run fast static and behavior checks. Review the full
diff against the protected contracts. Challenge the highest-risk edge cases:
for settlement code, these might be rounding boundaries, replayed requests and
rollback after failure. Check that assertions cover outcomes and side effects,
not merely whether a function was called. Repair regressions and recheck.
For affected UI behavior, replay the real task in a browser.

Distinguish new regressions, pre-existing failures, flaky results and environment
problems; preserve raw check statuses. Never remove protections to get green.
Run required project validation on the final candidate, repeating affected checks
and required gates after relevant code, test or configuration changes. Missing
required evidence remains unresolved. After two attempts at the same failure
without new evidence, diagnose and report the blocker instead of repeating it.

4. Show what became easier.
Finish the selected change and its verification; leave unrelated findings for
later. Report: what changed; where the next change of this kind belongs; contracts
and checks preserved; actual commands/results; unresolved risks and the smallest
next action. A compile or smaller file count alone is not proof of improvement.
For work spanning sessions, preserve a short verified/pending/blocked handoff.
```

[Back to the workflows](../README.md#choose-your-workflow) · [Architecture guide](../docs/architecture.md) · [Research behind this prompt](../docs/prompt-research.md)
