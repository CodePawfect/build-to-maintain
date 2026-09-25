# Research behind the prompts

Reviewed September 25, 2026. These prompts turn a short, ordinary-language request into scoped engineering work. The sources below support specific workflow decisions. They do not establish a universal prompt, a guaranteed success rate or a measured score for this collection.

## Sources and the decisions they inform

| Primary source | Relevant guidance | Applied in this collection |
|---|---|---|
| [Anthropic: prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) | Specify the desired action, constraints and output; examples clarify expectations. Avoid unnecessary work and abstractions. | Implementation is explicit. Each prompt has a small example or concrete decision rule, a scope boundary and a useful handoff. |
| [Claude Code: best practices](https://code.claude.com/docs/en/best-practices) | Give the agent executable verification, inspect before implementing, and compare UI output with its reference. Scale planning to the task. | Discover commands and context automatically; define acceptance checks; repair findings in the same workflow. |
| [Anthropic: effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) | Incremental progress and explicit end-to-end testing address premature completion. Unit checks can miss broken user journeys. | A first working slice is a milestone. Finish the scoped behavior list and exercise the real interface before declaring completion. |
| [Anthropic: building effective agents](https://www.anthropic.com/engineering/building-effective-agents) | Simple workflows, concrete environmental feedback and explicit stopping conditions help govern agent work. Iterative evaluation needs clear criteria. | Use a bounded task, examine actual results and diagnose stalled repairs. A focused review works without requiring a team of agents. |
| [Google: what to look for in a code review](https://google.github.io/eng-practices/review/reviewer/looking-for.html) | Review design, functionality, complexity and the usefulness of tests. Consider edge cases and whether assertions can catch defects. | A final challenge pass examines plausible failures and the checks meant to detect them; smaller files alone are insufficient. |
| [Martin Fowler: refactoring](https://refactoring.com/) and [Extract Function](https://refactoring.com/catalog/extractFunction.html) | Refactoring preserves observable behavior. A named function can communicate intent. | Discover contracts before changing structure; isolate a meaningful rule without quietly changing what callers observe. |
| [GOV.UK Design System: spacing](https://design-system.service.gov.uk/styles/spacing/) | A design system can express spacing as explicit scales, including responsive values. | Extract observed values and map them to implementation tokens. The prompt does not impose GOV.UK's particular scale on other products. |
| [GOV.UK: moderated usability testing](https://www.gov.uk/service-manual/user-research/using-moderated-usability-testing) | Observe people completing realistic tasks. Task instructions should state a goal without revealing the solution. | When user evidence is absent, prepare a neutral task and an observation sheet. An agent walkthrough remains a heuristic inspection. |
| [W3C: WCAG 2.2](https://www.w3.org/TR/WCAG22/) | Accessibility has testable, scoped success criteria. | Investigate relevant keyboard, focus, error, contrast and reflow requirements; a screenshot or a narrow check is not a conformance audit. |
| [Anthropic: demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) | Assess the resulting environment as well as the transcript, use suitable graders and repeat trials to account for variability. | Separate a prompt-design review from measured agent performance. Record practical criteria for later execution trials. |

## How we adapt the evidence

Official product guidance and engineering case studies provide useful experience, but are not controlled comparisons of these four prompts. W3C provides a standard; GOV.UK and Google provide institutional practice. Fowler supplies refactoring definitions and techniques. None of these source types warrants a claim that this wording works equally well with every model.

The common design is our synthesis: an ordinary-language brief, repository or product investigation, an explicit decision, implementation, a challenge pass, and evidence for the final candidate. Source examples are adapted to the workflow rather than copied as a large instruction bundle. Research, diagnostics and reports stay proportional to the task.

The following are editorial defaults, not thresholds validated by the sources: inspecting up to three refactoring candidates, using a short acceptance list, diagnosing after two attempts without new evidence, and the scoring rubric in the [review notes](prompt-review.md). Defaults should yield to real task complexity and repository requirements.

We keep provider-specific commands, model names and reasoning-trigger phrases out of the copyable blocks. Prompts use tools the host actually provides and honor its permissions. Their architecture and UI/UX decisions are expanded in the [architecture](architecture.md), [design](design-workflow.md) and [engineering-loop](agent-loop.md) guides.
