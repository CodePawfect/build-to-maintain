# Prompt review and evaluation

Reviewed September 25, 2026 against the previous four-prompt revision. The [research notes](prompt-research.md) connect each revision to primary sources and identify our editorial choices.

The current prompts score **9/10 for design readiness under the rubric below**. This is the author's structured text assessment, not an independent review, a measured success rate or a claim that research alone proves execution quality. No end-to-end agent trials were run for this revision.

## Rubric

The rubric was defined before rewriting and applied to both versions. Each dimension contributes 0–2 points with equal weight. Earlier informal ratings for quality, effectiveness and ease used different dimensions; their numbers are not directly comparable with this total.

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| **A · Input usability** | Requires a technical specification. | Important missing choices routinely return to the user. | An ordinary-language brief works; the agent discovers technical details and states reversible defaults. |
| **B · Task ownership** | Advice only, or the wrong scope. | Implementation is requested, but diagnosis, selection or completion is underspecified. | The agent selects bounded work, defines success and implements the complete stated scope without manufacturing changes. |
| **C · Domain precision** | Generic quality wishes. | Relevant principles with ambiguous outputs. | Concrete artifacts or decision rules, a calibration example and version-aware primary research. |
| **D · Verification** | Unsupported completion. | Checks and repairs are named, but live outcomes, assertion quality or final evidence have gaps. | Actual task replay, a meaningful failure challenge, repair and final-candidate evidence with honest blockers. |
| **E · Evidence maturity** | No documented review or trials. | Textual scenario review only. | Repeatable execution trials on representative tasks, recorded outcomes and regression checks. |

This rubric measures the design of the instructions and the maturity of their evidence. Its first four dimensions cannot establish that a model will follow them. Evidence maturity remains **1** until trials exist; a 9 is not “90% of tasks succeed.”

## Before and after

Vectors list A, B, C, D and E in that order. Scores are judgments against the stated anchors, not keyword counts.

| Prompt | Baseline vector | Baseline total | Current vector | Current total |
|---|---|---:|---|---:|
| [Start a project](../prompts/start-project.md) | 2 · 1 · 1 · 1 · 1 | 6/10 | 2 · 2 · 2 · 2 · 1 | **9/10** |
| [Refactor a project](../prompts/refactor-project.md) | 1 · 1 · 2 · 1 · 1 | 6/10 | 2 · 2 · 2 · 2 · 1 | **9/10** |
| [Build UI from a reference](../prompts/extract-design-system.md) | 2 · 2 · 1 · 1 · 1 | 7/10 | 2 · 2 · 2 · 2 · 1 | **9/10** |
| [Improve a user flow](../prompts/improve-user-flow.md) | 1 · 1 · 2 · 1 · 1 | 6/10 | 2 · 2 · 2 · 2 · 1 | **9/10** |

The meaningful differences are specific:

- **Build:** the baseline ended at a first slice. The new instruction makes that a milestone, completes the scoped checklist, exercises the real interface and challenges relevant failures. Its acceptance example is inside the copyable block.
- **Refactor:** the baseline required a maintenance problem from the user. The new instruction investigates candidates from a vague request, selects one using evidence, checks assertion quality and permits a justified no-change result.
- **UI:** the baseline listed visual categories. The new instruction requires values mapped to tokens/components, labels estimates, records intentional adaptations before comparison and explicitly exercises interactions.
- **UX:** the baseline expected a task and journey. The new instruction discovers those from an ordinary request, provides a no-analytics investigation path, and supplies a neutral participant task and observation sheet when user evidence is absent.

## Scenario walkthroughs

These cases were walked through against the prompt text to look for missing or contradictory instructions. The table records required branches and limits, not observations of an executing agent.

| Case | Required branch in the current prompt | What must not happen |
|---|---|---|
| **B1** · “Build a recipe app,” no stack selected | State a small complete scope, choose compatible tooling, derive acceptance checks and implement them. | Ask the user to design packages or stop at a plan. |
| **B2** · Save, search and edit are explicitly required | Build one path first, then finish the remaining listed behavior; verify saved state in the real interface. | Call the first working save form the completed app. |
| **B3** · The new-project destination contains application code | Request a fresh destination and preserve the files. | Convert this prompt into an existing-project workflow. |
| **R1** · “My project is hard to change,” no file named | Investigate up to three candidates and select one by benefit, behavior risk and verification cost. | Require an architecture diagnosis from the user. |
| **R2** · A long file with no demonstrated maintenance problem | Look for actual mixed responsibilities or change friction; allow a justified no-change result. | Split files to improve a superficial metric. |
| **R3** · Settlement refactor, missing coverage and a baseline failure | Protect relevant contracts; investigate conflicting expectations; separate pre-existing failures from new regressions. | Silently change rounding, idempotency, errors or test expectations. |
| **U1** · A desktop screenshot with no inspectable CSS | Label estimated values; match the known view and separately check product responsiveness. | Invent a reference's mobile state or exact measurements. |
| **U2** · Different brand colors and longer content | Record intended adaptations, map the new information hierarchy and test realistic lengths. | Copy distinctive brand assets or excuse accidental layout defects afterward. |
| **U3** · Attractive static output with a broken primary action | Exercise the action, keyboard/focus and applicable recovery paths before completion. | Treat the screenshot or build as sufficient evidence. |
| **X1** · “Signup is confusing,” no analytics or exact route | Discover the journey, label a heuristic walkthrough and implement only a supported issue. | Invent user criticism, a drop-off cause or a conversion uplift. |
| **X2** · No concrete issue is supported | Supply a focused neutral research task and observation sheet. | Make arbitrary UI changes to appear productive. |
| **X3** · Code and guidance reveal an issue, browser unavailable | Report runtime behavior as unverified and provide the smallest next action. | Claim the flow was exercised or usability improved. |
| **C1** · A code/configuration edit after a passing check | Revalidate the final candidate with affected checks and required gates. | Reuse stale success evidence. |
| **C2** · Repeated failure with no new diagnostic evidence | Diagnose the cause and report a concrete blocker after two unsuccessful attempts. | Repeat unchanged commands or weaken protections. |

## Measuring actual effectiveness

Use a fixed starting repository, explicit acceptance criteria and recorded tool access for each task. Compare the baseline and revised prompt with the same model/settings, tools and task budgets. Include clear requests, vague requests and missing-capability cases; perform multiple trials because outputs vary. Grade the resulting application and diff, not just the final message.

Report these measures separately instead of treating the design score as a performance result:

| Measure | Definition |
|---|---|
| Acceptance completion | Verified acceptance criteria met / applicable criteria; a task succeeds only if all required criteria pass. |
| User intervention | Count substantive user decisions and rescue steps; distinguish necessary product choices from avoidable technical questions. |
| Regressions | Count previously passing behavior checks that fail on the final candidate. |
| Evidence accuracy | Supported completion claims / completion claims; retain unverified items rather than counting them as passed. |
| Scope discipline | Review unrequested changes and whether each is necessary for the stated outcome. |
| Time and cost | Elapsed time, tool calls and tokens for successful and unsuccessful trials, using the same accounting. |

Inspect test assertions and have a reviewer check subjective design or usability judgments. Anthropic's [evaluation guide](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) supports evaluating actual outcomes, combining graders and repeating trials. The exact task cases and score thresholds here remain repository choices.
