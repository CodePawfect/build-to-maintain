# Hero and badges

The hero was created with the built-in OpenAI image-generation tool for **Build to Maintain**. It illustrates the [researched engineering loop](../docs/agent-loop.md) as a circle with explicit code-repair branches and a conditional completion point.

- File: [hero.png](hero.png)
- Delivered dimensions: 1942 × 809 pixels.
- Exact title: **BUILD TO MAINTAIN**
- Exact subtitle: **Build idiomatic, maintainable software with coding agents.**
- Forward path: Agent Research → Code Change → Fast Checks → Code Review → Local CI → Ready.
- Code findings from checks, review and CI return through the repair step to Code Change.
- The green PASS arrow makes readiness conditional; the dashed NEXT CHANGE arrow starts a new task after completion.
- Scope: the hero summarizes the successful path and code-repair loop. Missing prerequisites, unavailable evidence and runtime failures require separate diagnosis, as described in the guide.
- Method: one built-in diagram redesign followed by a focused text edit. The previous hero supplied the title, subtitle and flat visual direction.
- Review: checked labels, ordering, arrow directions, repair routing, readability and margins.
- Format: generated PNG with a flat diagram style, not an editable SVG.
- Interpretation: this is an illustrative process, not a report of completed checks or a claim that one workflow is optimal for every task.

## Redesign prompt

```text
Use case: infographic-diagram.
Redesign the supplied GitHub README hero into a precise, colorful CIRCULAR coding-agent engineering workflow. Keep ONLY its English headline, subtitle, white background and flat graphic direction. Remove both previous linear diagrams and all old labels, including "SOURCE DEPENDENCIES".

Wide landscape banner, approximately 2.4:1. Left 39%: strong navy sans-serif title on two lines, exact text "BUILD TO" / "MAINTAIN". Beneath, exact subtitle "Build idiomatic, maintainable software" / "with coding agents." Balanced readable typography and generous margins.

Right 61%: SIX substantial colored building blocks arranged around a clean circular path, like a carefully designed engineering lifecycle diagram. Six distinct stages, no duplicate nodes. Arrange CLOCKWISE from upper-left:
1. upper-left blue node: "01  AGENT RESEARCH", second line "Stack · Sources · Plan"
2. upper-right turquoise node: "02  CODE CHANGE", second line "Small, focused diff"
3. right-middle yellow node: "03  FAST CHECKS", second line "Static analysis · Tests"
4. bottom-right orange node: "04  CODE REVIEW", second line "Independent feedback"
5. bottom-left rose node: "05  LOCAL CI", second line "Configured checks"
6. left-middle green node: "06  READY", second line "Evidence verified"

CONNECTORS ARE IMPORTANT:
The forward path is 01 → 02 → 03 → 04 → 05 → 06, using clean thin navy arrows following the circle. The arrow from LOCAL CI to READY is green and explicitly labeled "PASS".
Close the circular layout with a visually lighter GRAY DASHED arrow from READY back to AGENT RESEARCH, labeled "NEXT CHANGE". This means a new task, not an endless retry after success.
Inside the circle, one small CORAL OUTLINE node reads "FIX & RECHECK". Three thin CORAL DASHED feedback arrows come IN to this center node from FAST CHECKS, CODE REVIEW, and LOCAL CI. One coral arrow leaves the center node and points back UP to CODE CHANGE. The center represents actionable feedback and revision. Make arrowheads and direction unambiguous. Keep all lines out of labels. Feedback lines must not point from READY into rework.
The outer ring shows the successful path; the center shows the repair loop. The diagram should look circular and integrated, not like rows of cards. Use graceful curved connectors where needed.

Style: disciplined 2D vector-like information design; flat solid cobalt, turquoise, yellow, orange, rose and mint fills, dark navy readable type, consistent line weights, restrained corners, white negative space. Crisp, colorful and technically intentional. Node headings large enough to read when the banner is displayed at 1000 pixels wide. No decorative icons, no robots, no 3D, no photographic objects, no paper, no grain, no gradients, no drop shadows, no glow. No fake metrics, no extra prose, no footer, no certification symbols. Do not add SOURCE DEPENDENCIES or the old module diagram. Keep the requested words exact.
```

## Final refinement prompt

```text
Use case: text-localization.
Make exactly THREE text refinements to the supplied circular Build to Maintain diagram. Keep every shape, position, color, arrow, heading, title, subtitle and all other words unchanged.

1. In the coral outlined CENTER node, replace the single-line text "FIX & RECHECK" with TWO readable centered lines: main line "CODE FINDINGS" and smaller line "Fix & recheck". This labels the repair branches as code-specific findings; it must not imply that an environment/access failure always requires changing source code.
2. In the orange "04 CODE REVIEW" node, replace ONLY its second line "Independent feedback" with "Behavior · Design". Preserve the node heading.
3. In the rose "05 LOCAL CI" node, replace ONLY its second line "Configured checks" with "Harness checks". Preserve the node heading.

Everything else must be exactly preserved, especially arrowheads: the three dashed coral arrows point INTO the center node and the solid coral arrow exits the center toward CODE CHANGE; green PASS arrow goes from LOCAL CI to READY; gray NEXT CHANGE arrow goes from READY to AGENT RESEARCH. No new nodes, no objects, no textures, no extra words.
```

## Local badges

The four SVG badges are editable vector assets with a charcoal label and a color drawn from the hero. They identify actual repository contents:

- Four complete engineering workflows.
- KISS as the guiding principle.
- New projects and existing-project refactoring.
- UI and UX workflows.

They are informational labels, not live build status, quality ratings or certifications.

## Reusable image brief

Use an agent with image generation and image inspection. Replace the inputs before copying.

```text
Create a generated hero for [project, audience and specific subject].
Placement: [aspect ratio and expected display width].
Brand/reference: [owned references and palette, or none].
Exact text: [title/subtitle, or no text]. Save to: [project asset path].

Read the project first. Choose a concrete visual that explains what the
project does, and state the concept in one sentence. For a process diagram,
settle the stages, arrow meanings, failure paths and completion condition
before generating. Research uncertain technical relationships.

Use one clear composition, a small palette and readable labels with safe
margins. Avoid decorative robots, glowing brains, floating code and fake
product screenshots or metrics. These are art-direction preferences, not
a method for detecting AI imagery. Use an available image-generation tool;
report a missing capability rather than claiming generation.

Inspect the image at its actual display size. Check subject fit, hierarchy,
text, crop, contrast and any diagram's arrow directions. Fix concrete
defects and inspect again. Save the final asset with useful alt text. Record
the generation tool, exact prompt and edits in a short asset note. Badges
may describe contents, but must not imply unrun checks or certifications.
```
