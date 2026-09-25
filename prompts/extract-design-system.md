# Build UI from a reference

Give the agent a reference and describe the screen you want. It extracts concrete design rules, applies your content and brand, then checks the implementation visually.

**Try this:** “Use this reference for my recipe library. Keep my app's name and colors; make the saved recipes easy to browse on a phone.”

Fill in `Reference` and `Change`. Brand rules are optional. Use an agent with repository, web, browser and screenshot access.

```text
Reference: [URL or attached screenshot]
Change: [describe the screen or component you want in ordinary language]
Optional brand or limits: [otherwise use the product's existing identity and scope]

Own the reference analysis, implementation and visual verification. Discover
routes, components and technical choices yourself. State reversible assumptions
and proceed; ask only when a missing product/design decision materially changes
the result. Follow repository instructions and permissions; preserve unrelated
work. If the reference cannot be inspected, request an accessible reference and
continue independent repository discovery without inventing its appearance.

1. Establish the target and extract usable rules.
Inspect the app, tokens, routes, manifests and lockfiles; identify the framework,
UI libraries, resolved versions and run/check commands. Locate the requested
surface and capture its starting state. Define the intended user task and the
content that must remain visible. For a new surface, use neighboring conventions.

Inspect the reference at available sizes and states. Produce a compact mapping:
visual role -> observed value/rule -> target token or component. Include relevant
font sizes/weights/line heights, spacing, content width/grid, colors, borders,
image proportions and responsive/state changes. Label measured versus estimated
values. Example: "three desktop columns collapse to one; reuse the card primitive
with the observed spacing scale." Never infer unseen behavior as an observation.

2. Adapt the system to this product.
Map my content hierarchy and primary action into those rules. Use the product's
own name, copy, logo and assets. If brand rules are absent, state a provisional
palette/type choice; do not import another brand's distinctive artwork or marks.
List deliberate adaptations before comparison so they do not become excuses for
accidental mismatches. Research relevant official framework, component and
platform guidance for the versions in use. Keep the implementation idiomatic,
accessible and within scope; reuse primitives and tokens rather than adding
one-off offsets or replacing the stack.

3. Implement the full surface and its behavior.
Preserve working data flow. Include relevant loading, empty, error, success and
focus states, realistic text lengths and mobile behavior. Keep semantic structure,
keyboard operation, contrast and labels intact. Do not stop at a static mockup
when the task calls for a working interface.

4. Compare the result and repair specific differences.
Capture reference and result at matching available viewport, scroll and UI state,
with comparable content density. Review layout/hierarchy, typography, spacing,
color/surfaces and component states. Mark each dimension matched, intentionally
adapted or needing correction, with screenshot evidence and a concrete reason.
Prioritize task/accessibility defects, then repeated system mismatches, then
small decoration. Fix the largest underlying cause and recapture affected views.
With one screenshot, match only its known view; separately verify the product's
responsive behavior. Check narrow mobile and desktop, plus a width where layout
changes. A build passing does not establish a visual match.

Exercise the primary action, keyboard/focus and relevant failure/recovery paths.
Inspect assertions and outputs; review the diff and run required project checks
against the final candidate. Recheck after changes. After two passes without
material progress, diagnose the constraint and report unresolved differences.
Missing browser or research access stays explicitly unverified, not passed.

5. Hand over the result.
Finish when the scoped task works and consequential mismatches are resolved.
Return where to try it, key design values and adaptations, comparison evidence,
actual checks, remaining limitations and their next action. Do not claim user
validation or full accessibility conformance from screenshots or limited checks.
```

[Back to the workflows](../README.md#choose-your-workflow) · [Design guide](../docs/design-workflow.md) · [Research behind this prompt](../docs/prompt-research.md)
