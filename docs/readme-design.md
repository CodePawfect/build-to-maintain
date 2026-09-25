# Designing the repository's front page

The README helps a reader choose a task, copy a prompt and understand the standard behind it. Detailed explanations belong one click deeper. The visual treatment uses GitHub's Markdown and supported HTML, with no custom CSS or scripts in the repository.

## Reference observations

Reviewed on September 24, 2026. These repositories are examples of presentation choices; their popularity does not establish that a layout caused it.

| Reference | Observable pattern | Applied here |
|---|---|---|
| [Build Your Own X](https://github.com/codecrafters-io/build-your-own-x) | A banner, short purpose statement and direct category links precede the resource list. | One hero, one introduction and immediate task selection. |
| [System Design Primer](https://github.com/donnemartin/system-design-primer) | A structured learning path, topic index and diagrams support a large technical collection. | A clear route from practical workflow to deeper explanations. |
| [Awesome](https://github.com/sindresorhus/awesome) | Categories and concise descriptions make a large link collection navigable. | Descriptive links and a compact guide index. |
| [The Book of Secret Knowledge](https://github.com/trimstray/the-book-of-secret-knowledge) | A distinct visual identity, badges and chapter navigation organize dense content. | Informational badges and a recognizable, subject-specific hero. |
| [Build What Sells](https://github.com/CodePawfect/build-what-sells) | A branded banner, content badges and a situation-to-prompt table establish a consistent entry point. | Shared family resemblance, with this repository's own engineering diagram and workflow choices. |

## Composition decisions

The circular hero carries the identity and process explanation. Its colors reappear in four content badges. The introduction leads straight into compact contents navigation, followed by four numbered workflow rows with descriptive links and outcomes.

Two local composition studies compared a two-column grid and an open vertical list. The grid grouped the choices well on desktop but narrowed the text excessively on a phone. The final selector uses full-width rows with a small number column. It keeps all four choices comparable while giving their descriptions room to wrap.

A worked task brief makes the prompts concrete. One expandable code example provides depth without interrupting the first read. Detailed architecture, research and failure handling live in linked guides. The related repositories remain visible at the end.

GitHub documents [collapsed sections](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-collapsed-sections), [relative links, images and alerts](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax). Use those native features instead of relying on styling that a repository renderer may discard. Keep essential labels as text and give images useful alternatives.

These are editorial design decisions, not an experimentally established recipe for earning stars. The repository makes no engagement or conversion claim from this redesign.

## Visual verification

The local Markdown preview was inspected at 320, 375, 768 and 1280 pixels. After publication to the private repository, the actual GitHub rendering was checked at desktop width and 390 pixels, including loaded hero/badge assets and a prompt destination. Native GitHub rendering remains the final reference; the local preview only approximates its styling.
