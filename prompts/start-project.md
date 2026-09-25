# Start a project

Describe the app you want. The agent chooses the technical details, builds a small complete version and shows how to try it.

**Try this:** “A recipe app where I can save recipes, find them by title and edit them later. Everything stays on my laptop.”

Replace `Build` in the block below. Limits are optional. Use an empty or documentation-only directory and an agent with file, shell and web access; web apps also need browser access for verification.

```text
Build: [describe the app in your own words]
Optional limits: [must-have behavior, technology or delivery constraints; otherwise choose sensible defaults]

Own this new project from the brief through working, verified software.
Make routine technical decisions yourself and explain important choices briefly.
Ask only about missing product decisions that would materially change the result;
state reversible assumptions and continue. Follow applicable instructions and
permissions. If the destination already contains application code, request a
fresh destination. Preserve unrelated files.

1. Turn the idea into a finishable scope.
Use my requested scope. For a broad idea, define a small complete initial version
without inventing extra features. Write a short checklist: user action -> visible
result -> verification. Include an important failure or recovery path.
Example for a recipe app: save and reload -> recipe persists; submit an empty
title -> useful error and entered text remains. Adapt examples to this project.
State assumptions and exclusions, then implement; do not stop at a plan.

2. Choose the stack and structure before scaffolding.
Honor supplied constraints. Otherwise select the simplest suitable runtime,
language and tooling; add a framework, storage or service only when needed.
Research supported, compatible versions and relevant setup, layout and testing
idioms in official documentation. Link consequential decisions to their sources.
Record runtime/dependency versions and the ecosystem's lockfile where applicable.
Report unavailable research instead of guessing current APIs.

Keep code that changes for the same reason together. Introduce package, workspace
or service boundaries for actual ownership, dependency or deployment needs.
For larger backends with substantial rules or integrations, prefer hexagonal
architecture: independent domain rules, ports owned by the inner layer that needs
them, outer adapters and explicit wiring. Simple CRUD can remain framework-native.
Avoid empty layers, speculative abstractions and unnecessary dependencies.
Extract a coherent rule when its name makes the caller understandable without
reading its mechanics; keep side effects visible.

3. Build and prove the complete scoped version.
Set up reproducible install, run and relevant build/check commands. Implement one
path end to end, then finish the remaining checklist. A first slice is a milestone.
Use real behavior in scoped paths; label any necessary test doubles or unavailable
integration and never present them as completed functionality.

Run relevant static checks and behavior tests. For a web UI, start the app and
exercise the actual journey in a browser at desktop and mobile sizes, including
errors and saved state. For a CLI/API, exercise its real entry point and outputs.
Challenge the result with plausible failures such as invalid input, duplicate
submission or restart, choosing cases relevant to this app. Check that test
assertions can detect those failures. Review the diff for defects and needless
complexity, repair findings, then rerun required checks on the final candidate.
Do not weaken checks or mark unexecuted cases as passed.

4. Leave something I can use.
Finish when the checklist and required verification pass. Diagnose code defects
separately from setup or access failures. After two attempts at the same failure
without new evidence, stop repeating it and report the cause and next action.
For work spanning sessions, leave a short progress note with verified, pending
and blocked items. Keep setup instructions reproducible.
End with: what works; how to launch and try it; checks and evidence; unresolved
items and the smallest action needed. Explain user-facing consequences plainly.
```

[Back to the workflows](../README.md#choose-your-workflow) · [Architecture guide](../docs/architecture.md) · [Research behind this prompt](../docs/prompt-research.md)
