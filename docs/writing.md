# Clear technical writing for architecture and refactoring

Write for the reader’s next task: understand a design, assess a change, or decide what to do. Make the prose concrete and easy to scan, while preserving the technical detail needed to trust it. “Engaging” means relevant to that task, not louder or more entertaining.

## Evidence and editorial judgment

An early web-writing experiment compared concise, scannable, and factual versions of the same travel-information site. Those versions did better on several measured usability outcomes. The setting was general web content, so this is evidence for helping readers find and use information; it does not prove that shorter technical docs create more interest or engagement. [Morkes and Nielsen’s study](https://www.nngroup.com/articles/concise-scannable-and-objective-how-to-write-for-the-web/) is useful context, not a promise of the same effect in a repository.

A later usability study with domain experts found that specialists value concise, scannable information while still needing facts, evidence, detail, and the vocabulary shared by their field. For engineering playbooks, preserve precision and show how readers can verify important claims. [NN/g’s study of expert readers](https://www.nngroup.com/articles/writing-domain-experts/) supports that direction. A [GOV.UK research review](https://www.gov.uk/government/publications/govuk-content-principles-conventions-and-research-background/govuk-content-principles-conventions-and-research-background) discusses how headings, opening sentences, and clear organization help readers orient and scan; it synthesizes earlier work rather than reporting one new experiment.

Other choices here are editorial judgment, not proven laws: favor active verbs, a calm conversational tone, examples, and varied paragraph rhythm. Google’s developer guide recommends direct, approachable language while cautioning against slang and prose that is either choppy or long-winded. Treat this as a useful style guide, not a universal effect claim. [Google’s voice and tone guidance](https://developers.google.com/style/tone)

## Practical standards

1. **Lead with the answer or decision.** Name what changes, who needs to act, or what question the section resolves.
2. **Use specific nouns and verbs.** Name the service, file, event, boundary, or failure mode. Say what it does: “validates,” “routes,” or “retries,” rather than “handles” or “leverages.”
3. **Connect claims to evidence.** Link to a test, code path, diagram, benchmark, or decision record. Separate observed behavior from expectation and recommendation. If evidence is missing, say what remains unknown.
4. **Explain cause and consequence.** State why a design exists and what its trade-off means for deployment, callers, operators, or future changes. Do not claim a benefit the change does not establish.
5. **Use examples to make abstractions testable.** Show a representative request, event, diff, or before/after behavior. Prefer the simplest valid example first.
6. **Format for scanning and reading.** Use informative headings, short sections, and lists for parallel items or ordered steps. Avoid a wall of text and avoid chopping every sentence into its own paragraph. Vary sentence and paragraph length where it helps the explanation flow.
7. **Remove empty promotion.** Words such as “seamless,” “robust,” “powerful,” and “best-in-class” need a measurable or observable meaning. Otherwise replace them with the behavior, limit, or evidence.
8. **Sound human without inventing a persona.** Be direct and respectful. Use “we” only when it names the actual team or its decision. Do not invent personal experience, success stories, quotes, or certainty.

## Before and after

These examples illustrate wording; adapt the facts to the actual design.

**Architecture**

Before: “Our solution leverages a robust, scalable architecture to seamlessly process orders.”

After: “The API gateway sends `POST /orders` to `OrderService`. After the database transaction commits, the service publishes `OrderCreated`.”

**Refactoring**

Before: “We modernize the codebase with a modular approach that improves maintainability.”

After: “Move address validation from `CheckoutService` into `OrderValidator`. This lets the team change validation rules without editing checkout flow; the response schema stays the same.”

**Agent behavior**

Before: “The agent seamlessly orchestrates complex tasks with robust safeguards.”

After: “The planner checks each tool result against `TaskResult`. It asks the user before a tool can delete data or publish a release.”

## Copyable editing prompt

Use this for a README, architecture note or change description. Fill in the reader and paste the source text.

```text
Edit the supplied technical text for [reader] who needs to [task].
Preserve the facts and technical terms. Lead with the decision or behavior
they need to understand; explain the consequence with a concrete example
only when the source supports one. Remove repeated claims, vague benefits
and promotional filler. Keep enough detail to assess the trade-off.

Use informative headings, connected paragraphs and active verbs. Keep
lists for steps or comparable items. Read the result for a natural rhythm;
avoid both dense walls of prose and one-sentence paragraph chains.

Do not invent measurements, citations, implementation details, personal
experience or certainty. Separate findings from hypotheses. If a claim
cannot be supported, flag it instead of polishing it into a stronger claim.

Return the revised text, then only factual gaps that still need an answer.

Source text and supporting facts: [paste here]
```
