---
name: html-effectiveness
description: Create compact, interactive, single-file HTML artifacts instead of flat Markdown when Codex is asked for analysis pages, visual reports, product/engineering plans, code-review summaries, research explainers, prototypes, dashboards, triage boards, prompt tuners, or any deliverable where comparison, filtering, interaction, charts, diagrams, or spatial layout would make the information easier to understand. Use when the user asks for HTML, interactive HTML, a visual/interactive report, a prototype, a demo, a dashboard-like document, or says Markdown is too flat.
---

# HTML Effectiveness

## Purpose

Turn dense written work into a useful single-file HTML artifact when Markdown would make the answer long, flat, or hard to compare. The artifact should behave like a small product surface: readable, inspectable, interactive where interaction helps, and self-contained enough to open locally without a build step.

Use the `thariqs/html-effectiveness` visual language as the default: a Claude paper-style interface with warm paper backgrounds, serif editorial headings, clay/orange and olive accents, fine borders, restrained shadows, generous but controlled whitespace, and clear interactive controls. Do not copy the sample pages verbatim; extract the pattern and visual grammar, then adapt it to the user's domain, language, data, and taste.

## Decision Rule

Choose a single-file HTML artifact when at least one is true:

- The user needs to compare options, designs, files, risks, timelines, or records.
- The user needs to explore information by filtering, sorting, toggling, expanding, dragging, or editing.
- The deliverable includes charts, diagrams, mockups, workflows, status, or a board.
- The answer will be handed to another person and should be browsable rather than read as a long note.
- The user explicitly asks for interactive HTML, HTML analysis, prototype, visual report, or dashboard.

Stay with Markdown when the answer is short, mostly prose, or the user wants a normal document.

## Workflow

1. Identify the job the HTML must do: compare, explain, prototype, report, plan, review, triage, or edit.
2. Select one primary pattern. If unsure, read [example-patterns.md](references/example-patterns.md) and choose the closest fit.
3. Build a single `.html` file with inline CSS and JavaScript unless the existing project requires another structure.
4. Use the user's real labels, data, and workflow language. Do not invent enterprise filler or decorative metrics.
5. Add only interactions that make the artifact more useful: filters, tabs, toggles, search, expand/collapse, copy/export, drag/drop, sliders, or live preview.
6. Validate that the file opens locally, renders without missing assets, fits desktop and mobile widths, and does not lose source data.

## Artifact Standards

Make the first screen useful immediately. The user should see the object of work, not a marketing hero.

Prefer:

- Claude paper styling by default: warm ivory/paper background, white panels, clay or rust primary accents, olive/green secondary accents, fine gray dividers, subtle shadows, and editorial serif headings paired with system sans body text.
- Clear information hierarchy and dense-but-readable layouts.
- Real data, filenames, entities, dates, and source labels when available.
- Tables, timelines, comparison grids, boards, diagrams, side-by-side panes, and compact controls.
- Plain-language labels, especially for Chinese business or personal workflows.
- A visible state for empty, warning, selected, filtered, and copied/exported actions.

Avoid:

- A generic landing page for an artifact that should be a tool or report.
- Copying `thariqs/html-effectiveness` HTML source, fictional Acme/Birchline content, or exact demo layouts when the user's task needs its own structure.
- Letting the paper style become decoration only; controls still need to be useful, visible, and stateful.
- One-note palettes, gratuitous gradients, ornamental blobs, or explanation text that describes how to use obvious controls.
- UI cards nested inside other cards.
- Interactions that do not affect the user's understanding or workflow.

## Visual Direction

Start from the Claude paper visual system unless the user requests another style:

- Background: `#FAF9F5`, `#F7F4EC`, or similar warm paper; panels can use white or slightly warmer paper.
- Text: near-black slate for main text; muted warm gray for secondary text.
- Accents: clay/rust/orange for primary emphasis; olive/sage for secondary status; use blue sparingly for links or technical focus.
- Typography: serif display headings such as Georgia or ui-serif; system sans for body and controls; monospace for paths, code, and exports.
- Shape: 8-10px panel radius, fine 1-1.5px borders, light shadows, no glossy gradients.
- Composition: editorial document clarity plus real app controls; not a marketing hero and not a dark developer console unless explicitly requested.

Adapt within that visual system:

- Product/admin work: denser tables and controls, but keep the paper palette and serif section rhythm.
- Personal analytics: warm data-first dashboard, with readable charts and preservation of raw records.
- Engineering review: diff-aware and risk-first, but presented as a paper review packet with compact controls.
- Product prototype: realistic app surface, with paper-style framing only around supporting analysis.
- Teaching or research explainer: progressive disclosure, diagrams, examples, and short checks for understanding.

## Implementation Rules

- Keep the artifact self-contained: inline CSS and JS, no external dependency unless the user or repo already provides it.
- Use semantic HTML and accessible labels for controls.
- Use stable dimensions for boards, tiles, toolbars, charts, and code panes so content changes do not shift the layout unexpectedly.
- For charts, prefer simple SVG or Canvas when no chart library is already available.
- For export/copy actions, provide a plain Markdown, JSON, CSV, or text output that matches the task.
- Preserve raw user data. If summarizing, include a source/raw-record area or a clear way to inspect the underlying items.

## Validation

Before final response:

- Open or otherwise verify the generated HTML renders locally.
- Check desktop and narrow/mobile widths when the artifact is intended for browsing.
- Exercise meaningful controls: filters, toggles, drag/drop, copy, tabs, search, or preview.
- Confirm source records, counts, dates, and labels match the input.
- Mention any validation that could not be run.

## Delivery

Return the local file path and a short description of what the artifact does. If the user needs to pass the skill to Cursor, the `SKILL.md` plus the `references/` folder are sufficient; the original 20 sample HTML files are not required.
