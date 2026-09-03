# interaction-first-design

A Claude Code skill that makes "solve it with an interaction, not another interface element" the default operating procedure for any UI work — and audits design output against that standard.

## What it does

Design agents tend to solve problems by adding things: a sort button, an "unsaved" badge, an explanation panel. Every element costs attention, motor effort, learning, and screen real estate. This skill flips the default: the interface is a cost the user pays to reach a goal, and the best interaction is usually the one that removes the need for the element.

When active, the skill enforces a workflow that runs **before** writing UI code or drawing a screen:

1. **Name the goal and the gulf** — is the problem a gulf of execution (user can't see how to act) or a gulf of evaluation (user can't tell what happened)?
2. **Search for a cheaper move** — inference from context and history, better defaults, undo instead of confirm, peripheral status instead of central chrome — before any new widget.
3. **Keep an element ledger** — every element added across design rounds must earn its place, and additions are tracked so the interface doesn't grow monotonically. The ledger persists at `design/LEDGER.md` in the project, read before every round and never regenerated over.

The skill orders every decision through a three-layer precedence: **existence** (does the element deserve to exist — the ladder and ledger), then **quality** (is the surviving element built to measurable standard — the craft baseline), then **style** (visual direction, chosen last). Craft and style rules can never create an element; only the ladder can.

It triggers on any UI creation, modification, review, or prototyping task — including requests as small as "add a button" or "fix this UX" — and always for design reviews, visual state systems, and AI-agent experiences.

## Contents

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | The skill itself: core stance, workflow, and trigger conditions |
| [references/foundations.md](references/foundations.md) | The research the stance is grounded in — Norman, Hutchins/Hollan, Verplank, Raskin, Cooper, Saffer, Bret Victor, Weiser & Brown, Herigstad, Horvitz |
| [references/design-review-protocol.md](references/design-review-protocol.md) | Evidence-based review protocol: render-and-walk, viewport tiers, craft pass, regression watchlist, severity-ranked report format |
| [references/craft-baseline.md](references/craft-baseline.md) | Measurable exit criteria (WCAG 2.2 AA, Apple HIG, Material Design) for elements that survive the ledger — contrast, keyboard, touch targets, type, responsive, confirm-vs-undo, motion |
| [references/ai-agent-interaction.md](references/ai-agent-interaction.md) | Applying the stance when an AI agent acts on the user's behalf (Horvitz's mixed-initiative principles, Microsoft/Google human-AI guidelines) |
| [tests/pressure-log.md](tests/pressure-log.md) | Pressure-test scenarios and results — how the skill's wording was verified against agent behavior |

## Pressure-tested

The load-bearing wording is verified the way code is: baseline subagents run each scenario *without* the skill to document the failure (tooltips and CTAs added to score review points, a confirmation dialog shipped on a reversible delete, a style system generated before any interaction thinking), then agents reading the skill run the same scenario under the same pressure. Current suite: a completeness-pressured design review, a "ship the confirm dialog today" instruction, a style-first deliverable request (three converged reps), a ledger-persistence fixture with a badge-shaped stakeholder request, and an inherited-product redesign run twice — once on a marketing brief, once under "the CEO already decided" authority pressure. All with-skill runs pass; scenarios and outcomes live in [tests/pressure-log.md](tests/pressure-log.md), and edits to the precedence, craft-scoping, confirm-vs-undo, or ledger rules should re-run that suite.

The review protocol also covers **inheriting an existing UI**: detect preserve-vs-overhaul before any design work, take the audit as ledger round zero, treat habits as load-bearing, and never silently change slugs, nav labels, form field names, tracked IDs, the logo, legal copy, or existing accessibility wins.

## Installation

**As a Claude Code plugin** (from the marketplace manifest in this repo):

```bash
claude plugin marketplace add tad-agentics/Interaction-Design-Skill
```

```bash
claude plugin install interaction-first-design@interaction-first-design
```

**Or copy the skill directly** into your skills location:

```bash
cp -R interaction-first-design ~/.claude/skills/interaction-first-design
```

Claude will invoke it automatically on matching tasks, or you can invoke it explicitly with `/interaction-first-design`. See [CHANGELOG.md](CHANGELOG.md) for version history.
