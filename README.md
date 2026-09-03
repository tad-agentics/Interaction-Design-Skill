# interaction-first-design

A Claude Code skill for UI/UX and interaction design that makes "solve it with an interaction, not another interface element" the default operating procedure — and audits design work against that standard with evidence, measurable criteria, and a persistent element ledger.

## The problem it solves

Design agents solve problems by adding things. Users can't find sort → add a sort button. Users forget to save → add an "unsaved" badge. Users don't trust the AI → add a confidence chip, an explanation panel, and three feedback buttons. Every problem becomes an element; every element becomes a new problem (discoverability, layout, state, copy, accessibility, maintenance). The interface grows monotonically while every individual change looked reasonable.

Forty years of interaction-design research says the opposite: the interface is a cost the user pays to reach a goal, and the best interaction is usually the one that removes the need for the element. This skill makes that stance the default, then keeps it honest through implementation and review.

## How it works

### Core stance

1. The unit of design is the interaction, not the widget.
2. Every element is debt — it must close a gulf nothing cheaper can close.
3. Inference before interaction: read environment and history before asking the user.
4. Act, then let people correct — undo beats confirm.
5. Periphery before center — status stays calm until action is needed.
6. Modes are bugs.
7. Habit is the goal — design for the thousandth use, not the first.

### Three-layer precedence

Every UI decision passes through three layers, in this order, and lower layers can never create an element:

| Layer | Question | Decided by |
| --- | --- | --- |
| **Existence** | Should this element exist at all? | The Ladder of Least Interface and the element ledger |
| **Quality** | Is the surviving element built to standard? | The craft baseline — measurable WCAG 2.2 / HIG / Material criteria |
| **Style** | What visual direction? | Chosen last, applied to interactions that already work |

A craft check that seems to demand a new element is a ladder question in disguise. A style system generated before the interaction spec exists is decoration looking for a product.

### The workflow (runs before any code or mockup)

1. **Name the goal and the gulf** — execution (can't see how to act) or evaluation (can't tell what happened) — plus the user's distance and attention. If the brief is ambiguous, ask exactly one question, with choices; otherwise declare your read and proceed.
2. **Climb the Ladder of Least Interface** — stop at the first rung that closes the gulf:

   | Rung | Move |
   | --- | --- |
   | 0 | Eliminate the need (better default, remove the step) |
   | 1 | Infer from environment (selection, viewport, clipboard, time) |
   | 2 | Infer from history (last value, this user's pattern) |
   | 3 | Act automatically with cheap undo |
   | 4 | Fold into an existing interaction (the action lives on the object) |
   | 5 | Disclose progressively, in context, on request |
   | 5.5 | Assign the meaning to a channel — position, luminance, heat, glow — a property costs 0 elements |
   | 6 | Add a new element — last resort, paid for in the ledger |

3. **Design the interaction, not the widget** — Verplank's Do / Feel / Know and Saffer's trigger / rules / feedback / loops, written as an interaction spec.
4. **Apply the constraints** — modeless, monotonous, reversible, direct, calm, consistent, habit-safe — plus channel physics for products with recurring state and object–verb sovereignty for products where users commit actions.
5. **Pay for every element** — a ledger entry for anything that reaches rung 6, persisted at `design/LEDGER.md` in the project: read before every round, appended to, corrections logged in place, never regenerated over.

### Worked example

> "Users can't find how to sort the table."

Element-first: add a Sort dropdown. Interaction-first (rung 4): column headers are the sort control — click toggles direction, a subtle chevron is the feedback; rung 2 on top: remember the last sort per user. Elements added: none. Removed: the dropdown you would have built.

## What it covers

- **Creating and modifying UI** — screens, components, flows, onboarding, settings, empty states, notifications — including requests as small as "add a button" or "fix this UX."
- **AI-agent experiences** — Horvitz's act / scope down / ask / wait decision at every agent action point; the Microsoft human-AI guidelines that most reduce interface; the anti-patterns (plan viewers by default, feedback buttons on every message, approval gates on reversible edits).
- **Design reviews** — evidence-based: render and walk the artifact, screenshot the five viewport tiers, stress with long strings and empty data, read the console; run the craft pass over surviving elements; report with a Ship / Ship with fixes / Needs work verdict and findings ranked Blocker / High / Medium / Nit, each as observation → rule broken → fix. No finding without something the walk showed.
- **Inheriting an existing UI** — detect preserve-vs-overhaul before any design work; the audit becomes ledger round zero; habits are load-bearing; never silently change slugs, nav labels, form field names, tracked IDs, the logo, legal copy, or existing accessibility wins.
- **Craft and accessibility QA** — contrast, keyboard and focus, touch targets, type resilience, responsive tiers, the confirm-vs-undo rule (confirmation only where undo cannot reach), motion, layout stability.
- **Multi-round work with design agents** — the regression watchlist (decoration creep, banned patterns returning under new names, generator tells, fixture drift), comply-or-argue collaboration, and convergence criteria.
- **Product classes and domains** — task/decision products get the core at full strength; feeds, learning/games, and persuasion surfaces get a remapped channel map and cost model. Eight domains (money movement, health & safety, public sector, regulated consent, safety-critical operations, children's products, privacy-sensitive surfaces, shared devices) override specific rungs — undo-beats-confirm, infer-from-history, glanceable status — and the table says what applies instead. Domain changes the rung, never the palette.

## Repository contents

| Path | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | The skill: stance, precedence, workflow (ladder, interaction spec, constraints, channel physics, verb sovereignty, ledger), AI-agent section, deliverable formats, anti-pattern lexicon, pointers to the references |
| [references/foundations.md](references/foundations.md) | The research canon — Norman, Hutchins/Hollan, Verplank, Raskin, Cooper, Saffer, Nielsen, Bret Victor, Weiser & Brown, Krishna, Herigstad — with sources |
| [references/design-review-protocol.md](references/design-review-protocol.md) | Render-and-walk practice, the craft pass, inheriting a UI, the regression watchlist, design-system review, comply-or-argue, report format, convergence |
| [references/craft-baseline.md](references/craft-baseline.md) | Measurable exit criteria (WCAG 2.2 AA, Apple HIG, Material Design) for elements that survived the ledger — judges quality only, can never add an element |
| [references/ai-agent-interaction.md](references/ai-agent-interaction.md) | Horvitz's mixed-initiative principles, the Microsoft human-AI guidelines, Google PAIR, Nielsen's intent-based paradigm — mapped to reducing interface |
| [references/worked-examples.md](references/worked-examples.md) | Eight request → element-first → interaction-first walkthroughs with rungs and net counts |
| [references/product-class-overlays.md](references/product-class-overlays.md) | How the channel map and the definition of cost change for feeds, learning/games, and persuasion surfaces; the domain-constraints table (money, health, public sector, regulated consent, safety-critical, children, privacy, shared devices) naming which rung each domain overrides |
| [tests/scenarios.md](tests/scenarios.md) | Verbatim scenario prompts for both arms, expected shapes, and the not-yet-covered list — the re-runnable suite |
| [tests/fixtures/](tests/fixtures/) | Fixture files the scenarios need: the two-round OpsQueue ledger and a renderable prototype seeded with wrong-commit paths and generator tells |
| [tests/pressure-log.md](tests/pressure-log.md) | Outcomes from each run of the suite |
| [CHANGELOG.md](CHANGELOG.md) | Version history |
| [.claude-plugin/](.claude-plugin/) | Plugin and marketplace manifests for Claude Code installation |

## Pressure-tested

The load-bearing wording is verified the way code is. For each scenario, a control subagent runs first to document the failure — *without* the skill for core rules, or with the skill *minus the section under test* when that section overrides the skill's own defaults — then an agent that reads the skill runs the same scenario under the same pressure. Current suite:

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

All with-skill runs pass, and the whole suite was re-run after SKILL.md was restructured for token cost. Two results are worth knowing: the medication scenario showed the skill's existing rules already handled a high-stakes domain, so the health row of the domain table reinforces rather than rescues; the mental-health scenario showed the opposite — without the privacy row, the skill's own "periphery before center" instinct put health status on onlooker-visible surfaces. Edits to the precedence, craft-scoping, confirm-vs-undo, ledger, redesign, or domain-constraint rules should re-run the suite; see [tests/scenarios.md](tests/scenarios.md) for the prompts and [tests/pressure-log.md](tests/pressure-log.md) for outcomes.

## Installation

**As a Claude Code plugin:**

```bash
claude plugin marketplace add tad-agentics/Interaction-Design-Skill
```

```bash
claude plugin install interaction-first-design@interaction-first-design
```

**Or copy the skill directly** into your skills directory:

```bash
cp -R interaction-first-design ~/.claude/skills/interaction-first-design
```

Claude invokes it automatically on matching tasks, or explicitly with `/interaction-first-design`.

## Influences

The interaction-first core is grounded in the research listed in [references/foundations.md](references/foundations.md). The review and craft machinery was elevated by studying two other design skills: [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) contributed the evidence-based review structure, measurable craft criteria, and persisted-decision pattern; [taste-skill](https://github.com/Leonxlnx/taste-skill) contributed the redesign protocol, the "generator tells" framing, and field confirmation that binary rules bind where "use sparingly" does not. Both were adapted under this skill's precedence rule: interaction design decides existence, craft rules decide quality, style comes last. Some things were deliberately not taken: ui-ux-pro-max's 192 industry-specific reasoning rules map industries to palettes, fonts, and landing-page skeletons — style-layer lookups that would train agents to skip interaction thinking. Their place here is the eight-row domain-constraints table, which changes which rung an interaction lands on and never prescribes a look.
