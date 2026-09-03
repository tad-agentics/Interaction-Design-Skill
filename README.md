# interaction-first-design

A Claude Code skill for UI/UX and interaction design that makes "solve it with an interaction, not another interface element" the default operating procedure — and audits interaction behavior with scoped evidence, standards-aware criteria, and an optional persistent element ledger.

## The problem it solves

Design agents solve problems by adding things. Users can't find sort → add a sort button. Users forget to save → add an "unsaved" badge. Users don't trust the AI → add a confidence chip, an explanation panel, and three feedback buttons. Every problem becomes an element; every element becomes a new problem (discoverability, layout, state, copy, accessibility, maintenance). The interface grows monotonically while every individual change looked reasonable.

This skill synthesizes interaction-design research around a practical counterweight: interface carries attention, learning, accessibility, and maintenance costs, so an element should exist because it improves the task—not because completeness pressure produced more chrome.

## How it works

### Core stance

1. The unit of design is the interaction, not the widget.
2. Every element has a cost — keep it when it closes the gulf better than a cheaper interaction.
3. Inference before interaction, within identity, privacy, permission, and legal boundaries.
4. For authorized and genuinely reversible actions, correction usually beats confirmation.
5. Periphery before center — status stays calm until action is needed.
6. Hidden modes are error-prone; necessary modes must be explicit and habit-safe.
7. Recurring product surfaces should support durable habits without sacrificing learnability or accessibility.

### Three-layer precedence

Consider three layers in this order so decoration does not invent functionality. Accessibility, safety, law, and platform requirements may legitimately require a mechanism; route it back through the existence decision rather than suppressing it.

| Layer | Question | Decided by |
| --- | --- | --- |
| **Existence** | Does the task need this mechanism? | The Ladder of Least Interface and interaction-cost accounting |
| **Quality** | Is the surviving interaction built to standard? | The craft baseline — WCAG requirements, platform guidance, and recommendations kept distinct |
| **Style** | What visual direction? | Chosen last, applied to interactions that already work |

A craft check that requires a new element returns to the existence decision with its accessibility, safety, legal, or platform rationale. Style follows interaction behavior rather than defining it.

### The workflow (runs before any code or mockup)

1. **Name the goal and the gulf** — execution (can't see how to act) or evaluation (can't tell what happened) — plus the user's distance and attention. Ask the smallest set of questions that would materially change the result; otherwise declare your read and proceed.
2. **Climb the Ladder of Least Interface** — stop at the first rung that closes the gulf:

   | Rung | Move |
   | --- | --- |
   | 0 | Eliminate the need (better default, remove the step) |
   | 1 | Infer from environment (selection, viewport, clipboard, time) |
   | 2 | Infer from history (last value, this user's pattern) |
   | 3 | Act automatically with cheap undo |
   | 4 | Fold into an existing interaction (the action lives on the object) |
   | 5 | Disclose progressively, in context, on request |
   | 5.5 | Assign meaning to an existing channel — no discrete element, but still a perceptual and accessibility cost |
   | 6 | Add a justified new element and account for its interaction cost |

3. **Design the interaction, not the widget** — Verplank's Do / Feel / Know and Saffer's trigger / rules / feedback / loops, written as an interaction spec.
4. **Apply the constraints** — predictable, accessible, recoverable, direct enough, proportionate, consistent, and habit-safe. For recurring state and committed actions, derive a product-specific channel map and stable action semantics.
5. **Account for interaction cost** — record relevant additions, removals, and changed signals. Use element count as supporting evidence, not the objective; legitimate accessibility, safety, legal, and capability additions do not require an arbitrary retirement.

### Worked example

> "Users can't find how to sort the table."

Element-first: add a Sort dropdown. Interaction-first (rung 4): column headers are the sort control — click toggles direction, a subtle chevron is the feedback; rung 2 on top: remember the last sort per user. Elements added: none. Removed: the dropdown you would have built.

## What it covers

- **Creating and modifying UI** — screens, components, flows, onboarding, settings, empty states, notifications — including requests as small as "add a button" or "fix this UX."
- **AI-agent experiences** — Horvitz's act / scope down / ask / wait decision at every agent action point, with authorization established separately from confidence and reversibility; preview, approval, authentication, audit, and collaboration controls remain when risk or policy requires them.
- **Design reviews** — evidence-based: render and walk the artifact when possible, test supported viewports and dynamic content, inspect relevant source and accessibility semantics, and label each finding's evidence source. Reviews report rather than edit unless changes are requested.
- **Inheriting an existing UI** — detect preserve-vs-overhaul before any design work; the audit becomes ledger round zero; habits are load-bearing; never silently change slugs, nav labels, form field names, tracked IDs, the logo, legal copy, or existing accessibility wins.
- **Craft and accessibility QA** — WCAG requirements, platform guidance, contrast, keyboard and focus, targets, type resilience, responsive behavior, action authority and recovery, motion, and layout stability.
- **Multi-round work with design agents** — the regression watchlist (decoration creep, banned patterns returning under new names, generator tells, fixture drift), comply-or-argue collaboration, and convergence criteria.
- **Product classes and domains** — task/decision products strongly use the core while still deriving their own channel mappings; feeds, learning/games, and persuasion surfaces use different cost models. Eight high-stakes or sensitive domains override specific defaults such as undo-beats-confirm, inference from history, and glanceable status.

## Repository contents

| Path | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Concise entrypoint: scope, stance, decision layers, ladder, interaction spec, authority safeguards, cost accounting, review format, and conditional routing |
| [references/foundations.md](references/foundations.md) | The research canon — Norman, Hutchins/Hollan, Verplank, Raskin, Cooper, Saffer, Nielsen, Bret Victor, Weiser & Brown, Krishna, Herigstad — with sources |
| [references/design-review-protocol.md](references/design-review-protocol.md) | Render-and-walk practice, the craft pass, inheriting a UI, the regression watchlist, design-system review, comply-or-argue, report format, convergence |
| [references/interaction-patterns.md](references/interaction-patterns.md) | Deriving product-specific visual channels, keeping action semantics stable across surfaces, and choosing confirmation or recovery from authority and consequence |
| [references/craft-baseline.md](references/craft-baseline.md) | WCAG 2.2 AA checks, platform-specific guidance, and recommended defaults kept distinct so preferences are not reported as conformance failures |
| [references/ai-agent-interaction.md](references/ai-agent-interaction.md) | Horvitz's mixed-initiative principles, the Microsoft human-AI guidelines, Google PAIR, Nielsen's intent-based paradigm — mapped to reducing interface |
| [references/worked-examples.md](references/worked-examples.md) | Eight request → element-first → interaction-first walkthroughs with rungs and net counts |
| [references/product-class-overlays.md](references/product-class-overlays.md) | How the channel map and the definition of cost change for feeds, learning/games, and persuasion surfaces; the domain-constraints table (money, health, public sector, regulated consent, safety-critical, children, privacy, shared devices) naming which rung each domain overrides |
| [tests/scenarios.md](tests/scenarios.md) | Verbatim scenario prompts for both arms, expected shapes, and the not-yet-covered list — the re-runnable suite |
| [tests/fixtures/](tests/fixtures/) | Fixture files the scenarios need: the two-round OpsQueue ledger and a renderable prototype seeded with wrong-commit paths and generator tells |
| [tests/pressure-log.md](tests/pressure-log.md) | Outcomes from each run of the suite |
| [CHANGELOG.md](CHANGELOG.md) | Version history |
| [.claude-plugin/](.claude-plugin/) | Plugin and marketplace manifests for Claude Code installation |

## Behavioral evaluation status

The repository includes scenario-based prompt smoke tests. Historical runs suggest that older versions changed model behavior in the intended direction, but most used one repetition, did not retain complete raw artifacts, and included one contaminated control. They are not automated tests or evidence of user outcomes, and **version 0.5.1 has not yet been behaviorally rerun**. `tests/scenarios.md` defines stricter requirements: isolated arms, identical prompts and tool policies, retained raw outputs and environment metadata, multiple repetitions, and disclosed scoring.

| Scenario | Pressure | Control | With skill |
| --- | --- | --- | --- |
| Design review of a flawed table | "Miss nothing" completeness | Tooltips, CTA blocks, confirm dialog, two unrequested elements | Verdict-first, heuristic-labeled, undo not confirm, sort on headers (net −1), one CTA max |
| "Add a confirmation dialog before delete" | Ship today | Built the dialog | Soft-delete + undo, ledger net 0, argued the case |
| "First deliverable: style, palette, fonts" | Deadline | Style with no interaction analysis | Three reps converged: style as layer 3, palette as channel map, spec precedes build |
| Brand restyle + "urgent" icon on an existing ledger | Stakeholder request | — | Read the ledger, appended round 3, declined the icon (heat channel), restyle net 0 |
| Inherited product redesign | Marketing brief, then "CEO decided, no debate" | Wizard, renames, expert-mode toggle, tooltips, tour | Mode question, ledger round zero, never-silently applied, wizard costed and argued side by side |
| AI agent "trust" bundle (approval modal, confidence badge, thumbs, always-open why panel) | Sprint deadline | Weak control — rejects most of it unprompted | Execution gulf named, rungs 1–2 targeting, scope-down with one chip, verb state as confidence, explanation on request |
| Rendered prototype review | Real browser walk | Contaminated (installed skill auto-loaded) | Walked 1440/375, observed a wrong-card commit from a positional key, receipt-that-waits for the irreversible transfer, generator tells as undeclared elements, 31 → 15 |
| Medication dosing "speed-ups" (autofill from last dose, one-tap repeat, drop the confirmation) | Nursing lead + pediatric pilot | Control = skill without the domain table: already correct | Same design, now citing patient-context resets and the shared, family-visible tablet |
| Mental-health app made "ambient" (mood widget, lock-screen activity, chat dot) | "Calm, glanceable" framing | Control = skill without the domain table: **shipped mood colour and a therapist's name onto onlooker-visible surfaces** | Who-else-can-see-the-screen governs: calendar hand-off under a neutral title, check-in folded into launch, opt-in summoned widget with no mood colour |

Treat the table above as a historical summary, not a release claim. Re-run both arms after changes to the skill, model, harness, system instructions, tool policy, scenario, or rubric. See [tests/scenarios.md](tests/scenarios.md) for the current method and [tests/pressure-log.md](tests/pressure-log.md) for the qualified historical record.

## Installation

**As a Claude Code plugin:**

```bash
claude plugin marketplace add tad-agentics/Interaction-Design-Skill
```

```bash
claude plugin install interaction-first-design@interaction-first-design
```

**Or load the repository as a skills-directory plugin:**

```bash
git clone https://github.com/tad-agentics/Interaction-Design-Skill.git ~/.claude/skills/interaction-first-design
```

Claude invokes it automatically on matching tasks. Explicit plugin invocation is namespaced:

```text
/interaction-first-design:interaction-first-design
```

The shorter `/interaction-first-design` form applies only when `SKILL.md` is installed as a standalone skill without the plugin manifest.

## License

[MIT](LICENSE) © 2026 tad-agentics.

## Influences

The interaction-first core is grounded in the research listed in [references/foundations.md](references/foundations.md). The review and craft machinery was informed by two other design skills: [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) contributed evidence-based review structure, measurable craft criteria, and persisted decisions; [taste-skill](https://github.com/Leonxlnx/taste-skill) contributed the redesign protocol and “generator tells” framing. Both were adapted around this repository's decision layers: interaction design considers existence, craft checks quality, and style follows. Industry-to-palette or template lookups were deliberately not adopted; the domain table changes interaction decisions without prescribing a visual direction.
