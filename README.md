# interaction-first-design

A Claude Code skill that makes "solve it with an interaction, not another interface element" the default operating procedure for any UI work — and audits design output against that standard.

## What it does

Design agents tend to solve problems by adding things: a sort button, an "unsaved" badge, an explanation panel. Every element costs attention, motor effort, learning, and screen real estate. This skill flips the default: the interface is a cost the user pays to reach a goal, and the best interaction is usually the one that removes the need for the element.

When active, the skill enforces a workflow that runs **before** writing UI code or drawing a screen:

1. **Name the goal and the gulf** — is the problem a gulf of execution (user can't see how to act) or a gulf of evaluation (user can't tell what happened)?
2. **Search for a cheaper move** — inference from context and history, better defaults, undo instead of confirm, peripheral status instead of central chrome — before any new widget.
3. **Keep an element ledger** — every element added across design rounds must earn its place, and additions are tracked so the interface doesn't grow monotonically.

It triggers on any UI creation, modification, review, or prototyping task — including requests as small as "add a button" or "fix this UX" — and always for design reviews, visual state systems, and AI-agent experiences.

## Contents

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | The skill itself: core stance, workflow, and trigger conditions |
| [references/foundations.md](references/foundations.md) | The research the stance is grounded in — Norman, Hutchins/Hollan, Verplank, Raskin, Cooper, Saffer, Bret Victor, Weiser & Brown, Herigstad, Horvitz |
| [references/design-review-protocol.md](references/design-review-protocol.md) | Protocol for auditing screens, prototypes, and design systems against the interaction-first standard |
| [references/ai-agent-interaction.md](references/ai-agent-interaction.md) | Applying the stance when an AI agent acts on the user's behalf (Horvitz's mixed-initiative principles, Microsoft/Google human-AI guidelines) |

## Installation

Copy or symlink this directory into your Claude Code skills location:

```bash
cp -R interaction-first-design ~/.claude/skills/interaction-first-design
```

Claude will invoke it automatically on matching tasks, or you can invoke it explicitly with `/interaction-first-design`.
