# HTML Effectiveness Skill

A compact Codex/Cursor skill for creating interactive single-file HTML artifacts in the Claude paper visual style when Markdown would make information too flat, long, or hard to compare.

This skill is inspired by the idea and visual language behind [`thariqs/html-effectiveness`](https://github.com/ThariqS/html-effectiveness), but it does not vendor or depend on that repository's 20 HTML demos. It extracts the reusable workflow and default look: choose HTML when comparison, filtering, diagrams, reports, prototypes, or small editing surfaces make the answer more useful, and present it with warm paper backgrounds, editorial serif headings, clay/olive accents, fine borders, and restrained interactive controls.

## What It Helps With

- Interactive analysis pages
- Visual reports and dashboards
- Product or engineering plans
- PR/code-review summaries
- Research and feature explainers
- Design-system sheets
- Triage boards
- Prompt tuners
- Small prototype sandboxes

## Installation

For Codex, copy this folder into your skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/sharelgx/html-skill.git ~/.codex/skills/html-effectiveness
```

For Cursor or another agent, add the repository folder to the agent's skills/rules location, or paste `SKILL.md` as a project rule and keep `references/example-patterns.md` available as supporting context.

## Usage

Ask for an interactive HTML artifact instead of a Markdown document:

```text
做一个交互 HTML 分析页，比较这几个方案的取舍和风险。
```

```text
Turn this implementation plan into a self-contained HTML report with filters, milestones, risks, and a copyable task list.
```

```text
不要只写 Markdown，做成一个单文件 HTML 看板，可以筛选和导出。
```

The skill guides the agent to:

- Decide when HTML is worth using.
- Pick a dominant pattern such as comparison explorer, code-review board, flow explainer, triage board, or prompt tuner.
- Build a self-contained `.html` file with inline CSS and JavaScript.
- Use the Claude paper visual system by default while keeping controls genuinely interactive.
- Validate that the artifact opens locally and preserves the user's source data.

## Repository Contents

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── example-patterns.md
```

`SKILL.md` contains the core workflow and standards. `references/example-patterns.md` is a short pattern library the agent can read only when it needs to choose a structure.

## Design Principle

Use HTML when the answer should become an inspectable object, not just prose. The artifact should make complex information easier to browse, compare, filter, explain, or act on. The default style is Claude paper: warm, editorial, calm, and interactive.
