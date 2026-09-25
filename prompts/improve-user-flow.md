# Improve a user flow

Describe the part of your app that feels difficult. The agent investigates the current journey, checks the relevant guidance and implements a supported improvement.

**Try this:** “Signing up feels confusing. Find the main obstacle and fix it. I don't have analytics or user interviews.”

Replace `Improve` below. Evidence is optional; the agent must distinguish its own assessment from actual user research. Use an agent with repository, web and browser access.

```text
Improve: [describe the task or confusing part of the app in your own words]
Optional evidence or limits: [complaints, analytics, research, constraints; none is valid]

Own the investigation, decision, implementation and checks. Discover the journey
and technical details yourself. State reversible assumptions and proceed; ask
only when missing product intent materially changes the work. Follow repository
instructions and permissions; preserve unrelated work. Do not require analytics
or an exact route from me before investigating.

1. Reconstruct the current journey.
Identify the framework, resolved dependencies, relevant routes/components and
run/check commands. Infer the intended task and audience from the product and
brief; label uncertainty. For a broad request, choose the main relevant task
and explain the scope. Follow it in the running app from entry through outcome,
including decisions, errors, recovery and exits. Record a compact before-flow
and link observations to screenshots or source paths. Inspect available metrics,
support and research records, keeping their sources and periods.

Without analytics, perform a task-based heuristic walkthrough. Without browser
access, inspect code/tests and mark runtime behavior unobserved. Separate observed
behavior, actual user criticism, your heuristic criticism and causal hypotheses.
A drop-off alone does not explain why people leave.

2. Research and select the supported change.
Consult applicable official platform, design-system and component guidance;
match versions where relevant. For web, use relevant WCAG 2.2 criteria:
https://www.w3.org/TR/WCAG22/. Connect each candidate to current behavior,
a direct source URL and the recommendation it misses. State unavailable research.
Prioritize blocked completion or recovery, then evidence strength, impact and
implementation risk; keep unknown frequency unknown. Choose one bounded change.

Define an acceptance check separately from the hoped-for usability outcome.
Example: "An expired verification link offers resend without losing the entered
address" is checkable; "more people finish signup" needs user or usage evidence.
If no concrete issue is supported by observation or code and guidance, do not
invent one. Provide the focused research task needed to decide instead of making
a speculative change.

3. Implement and challenge it.
Implement the smallest complete fix for the selected issue. Preserve brand,
contracts and unaffected states. Replay the original task and recovery path at
relevant mobile and desktop sizes. Challenge likely failures such as submitting
twice, correcting invalid input or returning to a prior step; choose cases that
fit the change. Check keyboard, focus, errors and the applicable accessibility
criteria. Ensure assertions cover the promised behavior. Review the diff, repair
findings and run required checks on the final candidate; revalidate after changes.
Distinguish code, environment and evidence problems. After two attempts at the
same failure without new evidence, report the blocker and next action. Never
present an unrun check or missing capability as a pass.

4. Make the next user check easy.
When user evidence is missing, provide a ready-to-run neutral task, its starting
state and success condition, plus an observation sheet for unaided completion,
wrong turns, errors and recovery. Do not coach the participant through controls.
Explain how to compare the same task before/after with comparable conditions;
do not invent a baseline, numeric target, participant, quote or conversion result.

End with the before/after journey, why this change was chosen, where to try it,
actual acceptance results, unresolved hypotheses and the next measurement.
Distinguish verified functionality from demonstrated usability improvement.
```

[Back to the workflows](../README.md#choose-your-workflow) · [Design guide](../docs/design-workflow.md) · [Research behind this prompt](../docs/prompt-research.md)
