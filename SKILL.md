---
name: interaction-first-design
description: Solve user problems with interactions, not by adding interface elements — and audit design work against that standard. Use whenever creating, modifying, redesigning, reviewing, or prototyping any UI, screen, component, flow, onboarding, settings page, empty state, notification, or AI-agent experience, and for craft QA — accessibility/WCAG, contrast, touch targets, keyboard, responsive layout, typography, motion. Trigger even when the user only says "add a button/toggle/badge/modal/tooltip", "fix this UX", "users are confused", or asks for a mockup. Always trigger for DESIGN REVIEWS of screens, prototypes, or design systems (including output from design agents like Claude Design), for defining visual state systems (colour/glow/motion/urgency), for element ledgers across design rounds, and when an AI agent acts on the user's behalf. Grounded in Norman, Raskin, Cooper, Saffer, Bret Victor, Weiser & Brown, Horvitz, and the Microsoft/Google human-AI guidelines.
---

# Interaction-first design

## The failure mode this skill exists to stop

Design agents solve problems by adding things. User can't find sort → add a sort button. User forgets to save → add an "unsaved" badge. User doesn't understand the AI's output → add an explanation panel, a confidence chip, and three feedback buttons. Every problem becomes an element; every element becomes a new problem (discoverability, layout, state, copy, accessibility, maintenance). The interface grows monotonically and the product gets worse while every individual change looked reasonable.

The research consensus from forty years of interaction design is the opposite: the interface is a cost the user pays to reach a goal, and the best interaction is usually the one that removes the need for the element. Cooper: "No matter how cool your interface is, less of it would be better." Bret Victor: interactivity is "a curse for users and a crutch for designers" and should be the last resort, after inferring context from the environment and from history. Horvitz: prefer "doing less but doing it correctly under uncertainty." Weiser & Brown: good technology "informs but doesn't demand our focus or attention."

This skill makes that stance the default operating procedure. Interface design is downstream of interaction design; interaction design is downstream of the user's goal.

## Core stance (apply to every UI decision)

1. **The unit of design is the interaction, not the widget.** An interaction is a loop: user intent → action → system response → user evaluates → next intent. Design the loop; the widget is whatever the loop needs, often nothing new.
2. **Every element is debt.** It costs attention (Hick's law), motor effort (Fitts's law), learning, and permanent screen real estate. It must earn its place by closing a gulf that nothing cheaper can close.
3. **Inference before interaction.** Read the environment and history before asking the user. Asking is the most expensive move available.
4. **Act, then let people correct — never make them ask permission for reversible things.** Undo beats confirm. Scoped defaults beat questions.
5. **Periphery before center.** Status belongs in the periphery (calm) and moves to the center only when action is needed.
6. **Modes are bugs.** Same input must produce the same result. If you need a mode, make it a quasimode (held, not toggled).
7. **Habit is the goal.** Interfaces are used hundreds of times; the design target is the thousandth use, not the first.

## Precedence — three layers, in order

Every UI decision passes through three layers, and the order is not negotiable:

1. **Existence** — does the element exist at all? Decided by the ladder (Step 2) and paid for in the ledger (Step 5). Nothing below this layer can create an element.
2. **Quality** — is the surviving element built to standard? Decided by `references/craft-baseline.md` (contrast, touch targets, keyboard, type resilience, responsive tiers, reversal, motion). A craft check that seems to demand a *new* element is a ladder question in disguise — send it back to layer 1.
3. **Style** — visual direction (palette, typography voice, effects, signature aesthetics). Chosen last, applied to interactions that already work. A style system generated before the interaction spec exists is decoration looking for a product.

One consequence worth stating plainly: for **conversion surfaces** (landing/marketing pages, first-contact flows) style may legitimately optimize the first impression; for **product surfaces** (the tool someone uses daily) the thousandth-use rules above win every conflict between the layers.

## Workflow — run this BEFORE writing UI code or drawing a screen

Do not skip to implementation. The whole value of this skill is in steps 1–2; steps 3–5 keep the result honest.

### Step 1 — Name the goal and the gulf

Write one sentence each:

- **Goal** (Cooper): what end state does the person want? Not the task ("filter the list") — the goal ("find the invoice I'm thinking of in under five seconds").
- **Gulf** (Hutchins, Hollan & Norman): which side is broken?
  - *Gulf of execution* — the user knows what they want but can't see how to make the system do it (no affordance, wrong mapping, hidden action, too many steps).
  - *Gulf of evaluation* — the user acted but can't tell what happened or what state the system is in (no feedback, ambiguous state, delayed or noisy response).

Most "add a button" requests are gulf-of-execution problems that get patched with a gulf-of-evaluation element (badges, banners, tooltips) or vice versa. Naming the gulf prevents the mismatch.

Add one more sentence: **distance and attention** (Herigstad). How far away is the person and how much attention do they have — one foot and focused (phone), two feet and working (laptop), ten feet and relaxed (TV, shared), passing by (public screen, glanceable)? This sets the element budget before you design anything: the further away or the less attentive, the fewer things can be on screen and the more must be inferred or curated.

The same discipline applies to your own questions to the user. If the brief is ambiguous, ask exactly one question, with choices, and only when your possible reads genuinely diverge; otherwise state your read in one sentence and proceed. A multi-question intake is rung-6 interface imposed on the person you are designing for. If the artifact is an existing product that users already rely on, the one question is the redesign mode — see `references/design-review-protocol.md` §3.

### Step 2 — Climb the Ladder of Least Interface

Start at rung 0. Stop at the first rung that closes the gulf. Only reach a higher rung when you can state in one sentence why every lower rung fails.

| Rung | Move | Source |
|---|---|---|
| 0 | **Eliminate.** Remove the need. The problem is excise (work the software imposes, not the goal demands). Better default, remove the step, remove the feature. | Cooper (excise), Raskin |
| 1 | **Infer from environment.** Location, time, device, current selection, viewport, what's on screen, what's in the clipboard. Show what's relevant *now*. | Victor (Magic Ink), Amershi G4 |
| 2 | **Infer from history.** Last value used, most frequent choice, this user's pattern, what they did last session. Never start from zero. | Victor, Saffer ("bring the data forward"), Amershi G12–13 |
| 3 | **Act automatically with cheap undo.** Do the probable thing, show what you did, make reversal one gesture. Autosave, not save. Auto-correct with revert, not a dialog. | Cooper ("ask forgiveness, not permission"), Horvitz (act/ask/wait thresholds) |
| 4 | **Fold into an existing interaction.** Put the action on the object itself: sortable column header, drag-to-reorder, tap the number to edit it, long-press for detail. Direct manipulation on the thing, not a control about the thing. | Shneiderman, Hutchins/Hollan/Norman (direct engagement) |
| 5 | **Disclose progressively.** Show the primary path only; reveal secondary options on request, in context, near the trigger. Not a new persistent element — a conditional one. | Nielsen (progressive disclosure), Cooper ("design for the probable, provide for the possible") |
| 5.5 | **Assign the meaning to a channel.** Give the fact to an unclaimed *continuous property of a surface that already exists* — position, luminance (tone), heat (a background tint), gradient fill, glow. A property costs 0 elements; see "Channel physics" below. | v4 practice; Weiser (periphery) |
| 6 | **Add a new element.** Last resort. Now go to Step 5 and pay for it. | — |

Two rules while climbing:

- **A question to the user is rung 6, not rung 1.** Forms, wizards, confirmation dialogs, "which one did you mean?" prompts, onboarding surveys — all are new interface. Use them only when inference and scoped defaults both fail *and* the cost of a wrong guess is high (Horvitz: dialog sits between inaction and action on the expected-utility curve; it is justified only when the guess is uncertain and the error is expensive).
- **Explanatory UI is a smell.** If you are adding text, a tooltip, a badge, or a help panel to explain how something works, the interaction itself is wrong. Fix the mapping or the feedback instead (Norman). Exception: AI systems must set expectations about what they can do and how well — see the AI section.

### Step 3 — Design the interaction, not the widget

For the interaction you chose, specify it with Verplank's three questions and Saffer's four parts. This is the deliverable that precedes any code or mockup.

**Do / Feel / Know (Verplank)**
- *Do*: what does the person physically do? Button (discrete, symbolic — the machine takes over) or handle (continuous, analogic — the person stays in control)? Prefer handles for anything with a range; prefer a single gesture over a sequence of presses.
- *Feel*: what does the person perceive back, and how fast? Feedback must be immediate, proportional, and in the same place as the action. Delay between doing and feeling forces the user to rely on knowledge instead of perception — that is where explanatory UI creeps in. Plan **motion** here, as a feedback channel, not as polish at the end: where something came from and where it went, shown by movement, replaces the badge or message that would otherwise announce it (Herigstad). Keep **spatial semantics fixed** — decide once what up/down/left/right and forward/back mean in this product and never overload them; a stable axis needs no label.
- *Know*: what must the person understand to predict the result? Minimise it. A good mapping (control → effect) is spatial or natural; a bad one needs a label.

**Trigger / Rules / Feedback / Loops & Modes (Saffer)**
- *Trigger*: user-initiated or system-initiated? System triggers need context timing (Horvitz, Amershi G3). Is the trigger discoverable *by the person who needs it, at the moment they need it* — not globally visible to everyone always?
- *Rules*: what happens, in what order, with what constraints? Constraints prevent errors better than warnings do (Norman).
- *Feedback*: the minimum signal that closes the gulf of evaluation. Apply Saffer's foghorn test: if the person would need to know this even without looking at the screen, it earns prominence; otherwise it stays peripheral. Never report normalcy with a dialog (Cooper).
- *Loops & modes*: does it repeat? Does it change with time or state? If you introduce a mode, make it a quasimode (held, like Shift) or kill it (Raskin).

### Step 4 — Apply the constraints

Check the chosen interaction against these. Any "no" sends you back to Step 2.

- **Modeless.** Same input → same output regardless of hidden state.
- **Monotonous** (Raskin's sense): one way to do each thing, so habits form. Do not add a second path "for discoverability."
- **Reversible.** Any action cheaper than a confirmation is reversible by one gesture.
- **Direct.** The user manipulates the object of interest, not a proxy or a conversation about it.
- **Calm.** Ongoing status lives in the periphery (subtle, ambient, glanceable) and only moves to the center when the user must act.
- **Consistent.** Reuses an interaction the product already has. New vocabulary is its own cost.
- **Habit-safe.** After twenty uses, would a person do this without thinking? Would that habit ever cause harm (Raskin: habituation + modes = errors)?

### Step 4.5 — Channel physics (for any product with recurring state)

When many objects carry state (queues, dashboards, lists, monitors), do not encode state as badges. Assign each *meaning* to one *channel* — a continuous visual property of surfaces the design already has — and let no two channels say the same thing:

- **Position** = priority. Order carries "what first"; nothing else claims it, and the list never re-sorts under the user's hands (defer re-ranking while anything holds focus).
- **Luminance** = hierarchy. How bright a surface is says how much of it is yours (light = in your hands, dark = others', sunk = done). Not for category or type.
- **Heat** = urgency, continuous. A background tint or text colour that warms as the deadline approaches — a *function of time remaining*, not badge states. The interface ages: time passing updates it with no animation, because time passing is not an event.
- **Gradient fill** = progress, in exactly one place. Never decoration.
- **Glow + motion** = attention. At most one attention glow per screen, on the one object a single confirming gesture can act on. Motion means "the world changed" — arrival, commit, reversal, escalation — and nothing else; no idle loops, shimmer, pulses, or animation on data refresh.

Two laws make this honest. **A property costs 0; a signal costs 1**: a background tint on an existing card adds nothing to the ledger, but an outline that emits light is a signal and counts — the test is whether it exists as a thing the eye must parse separately. **Every colour channel needs a non-colour twin** (text, shape, or luminance) so no state is hue-only.

### Step 4.6 — Object–verb sovereignty (for any product where users commit actions)

- **The verb belongs to the object and appears wherever the object appears** — main queue, zoomed-out list, notification card, chat surface, command palette. One verb per object, one sentence carrying action + consequence ("Approve ₫23.4M → Treasury · same-day run"), identical everywhere. This is what makes multi-surface consistency automatic; a second phrasing of the same verb is a mode.
- **Verb classes are visual states**: committable (filled = one gesture commits, everywhere), reasoned (hollow until the user's typed words arm it — the reason field is the constraint, not a warning), scoped (the verb counts itself down as the user confirms the uncertain parts — the verb is the progress indicator). A filled look that isn't one-gesture-armed is a lie.
- **The commit never renders in untrusted territory.** External or embedded content (web pages, documents, third-party frames) is read-only, visibly bounded, carries no product chrome inside it, and closing it returns focus to the verb exactly where it was.
- **Keystroke safety**: a key never acts on something other than what holds focus; no shortcuts bound to positions that change (habituation turns them into wrong-target actions).

### Step 5 — Pay for every element (the element ledger)

If you reached rung 6, write the ledger entry before adding anything:

```
NEW ELEMENT: <name>
Closes gulf: execution | evaluation
Why rungs 0–5.5 fail: <one sentence each, or "n/a" with reason>
Replaces / removes: <at least one existing element, step, or state — or state "none" and justify>
Who sees it, when: <audience + condition; "everyone, always" needs strong justification>
Cost: attention | motor | learning | layout | state | copy | a11y | maintenance
Exit criteria: <what would let us remove it later>
```

The ledger is a *living document across rounds*, not a one-shot form. Rules that keep it honest:

- **Additions are declared, always** — icons, outlines, chips, plates, hint lines. A ledger that lists only removals is not a ledger; "small" and "decorative" are how creep enters.
- **A signal counts even if it decorates.** Anything the eye must parse separately (a ring, a glyph, a glow) is +1; a property of an existing surface (a tint, an ordering, a tone) is 0.
- **Corrections are logged in place**, not silently fixed ("logged as 0 for three rounds — that was wrong — +1 while it existed, now removed, back to 0"). The ledger's value is that it can be audited.
- **Restyles net zero.** A visual refresh that adds a glyph is a failed restyle.
- **Live prototypes carry ledgers like any frame.** Builds are where undeclared elements leak in.
- Aim for net-zero or net-negative element count per change; if a feature genuinely needs three new elements, the design is probably wrong at rung 0.

**Persistence.** The ledger lives at `design/LEDGER.md` in the project root (page- or module-specific ledgers under `design/pages/<name>.md`, overriding the master for that surface only). Before any design round: read the existing ledger first; entries in it are prior decisions, not suggestions. Never overwrite or regenerate a ledger that exists — append entries and log corrections in place. If no ledger exists, create one with the current element census as round zero.

## When the product contains an AI agent

AI products accumulate interface faster than anything else, because uncertainty tempts designers to add hedges: confidence badges, "why?" panels, thumbs up/down, regenerate buttons, approval dialogs, step-by-step plan viewers. Most of these are gulf-of-evaluation patches for a gulf-of-execution problem (the agent didn't scope its action to its confidence). The paradigm shift matters here: Nielsen calls it intent-based outcome specification — the user states the outcome, not the steps — which reverses the locus of control and makes turn-by-turn refinement the interaction to design, not a settings panel.

Apply Horvitz's three-way decision at every agent action point, in this order:

1. **Act** when confidence is high and the cost of being wrong is low or fully reversible. Show what was done, in place, with one-gesture undo. No confirmation.
2. **Scope down** when uncertain: do the part you are sure of, leave the rest positioned for the user to finish. Horvitz's Lookout example: if it cannot find the meeting time, it opens the right week of the calendar instead of guessing or asking. "Doing less but doing it correctly."
3. **Ask** only when the guess is uncertain *and* wrong is expensive. Ask with choices, not open questions (Cooper: "provide choices; don't ask questions"). One question, inline, dismissible by ignoring it.
4. **Wait** when the person is mid-flow and the service is not urgent. Time to attention, not to availability (Horvitz, Amershi G3).

The Microsoft guidelines that most reduce interface (full set in `references/ai-agent-interaction.md`):

- **G1–G2 Set expectations up front** — what it can do, and how well. This is the one place explanatory content is mandatory; put it at first use and in the empty state, not on every screen.
- **G7–G9 Efficient invocation, dismissal, correction** — these three are the *entire* control surface most agent features need. Invocation is usually a selection or a keystroke; dismissal is ignoring or Esc; correction is editing the result directly. If you have designed these three well, you do not need approve/reject/regenerate/rate.
- **G10 Scope services when in doubt** — replaces most confirmation dialogs.
- **G11 Explain why on access** — an explanation *available*, not an explanation *displayed*. Reveal on request (rung 5).
- **G14 Update and adapt cautiously** — do not re-layout, re-rank, or move things the user is looking at because the model learned something.
- **G16 Convey consequences** — when the user corrects, show the effect once, inline, then stop.

Anti-patterns specific to agents: streaming a plan the user didn't ask to read; asking clarifying questions that a default plus undo would handle; a persistent "AI" badge on every generated item; feedback buttons on every message (feedback should be the correction itself — G15 is satisfied by editing); modal approval gates on reversible file edits.

## Deliverable formats

### Interaction spec (write this before code or mockups)

```
INTERACTION: <verb-noun, e.g. "reorder priorities">
Goal: <user end state>
Gulf: execution | evaluation — <why>
Ladder rung chosen: <n> — why lower rungs fail: <one line>
Do: <physical action; button or handle>
Feel: <feedback; where; latency>
Know: <the one thing the user must understand>
Trigger: <user | system; condition; timing>
Rules: <what happens; constraints>
Feedback: <minimum signal; center or periphery; foghorn test result>
Loops/modes: <repeat? modes? quasimode?>
Reversal: <the undo gesture>
Elements added: <list or "none">   Elements removed: <list>
```

In Claude Code / Cursor: put this as a comment block at the top of the component or in the PR description, then implement it. In Claude Design: put it in the frame notes and make the mockup show the *loop* (before, during, after states), not just the resting screen.

### Design review output

When asked to review a UI, screen, or flow:

1. State the goal and the gulf for the primary task.
2. List every interactive element with its rung (0–6) and what it costs.
3. For each rung-6 element, propose the lowest rung that would replace it.
4. Run the craft pass (`references/craft-baseline.md`) over the surviving elements.
5. Give a net element count: current → proposed.
6. Flag modes, confirmations on reversible actions, explanatory UI, and center-of-attention status that should be peripheral.

Open with a one-line verdict (ship / ship with fixes / needs work), rank findings by severity, and back each with observed evidence — the full report format, evidence rules, and regression watchlist are in `references/design-review-protocol.md`. Lead with the biggest removal, not the longest list.

## Worked examples (request → element-first response → interaction-first response)

**"Users can't find how to sort the table."**
Element-first: add a Sort dropdown above the table.
Interaction-first (rung 4): column headers are the sort control; click toggles asc/desc, a subtle chevron is the feedback. Rung 2 on top: remember last sort per user. Elements added: none. Removed: the dropdown you would have built.

**"Users lose work — add an unsaved-changes warning."**
Element-first: badge + beforeunload dialog.
Interaction-first (rung 3): autosave on every change; peripheral "saved" tick that fades; version history reachable on request (rung 5). Elements added: one peripheral indicator. Removed: dialog, badge, Save button.

**"The AI sometimes picks the wrong file — add an approval step."**
Element-first: modal listing the file with Approve/Reject.
Interaction-first (rung 3 + G10): if confidence is high, act and show a one-line inline note with undo; if low, open the file picker pre-filtered to the top candidates with the best one focused — the user's confirming action is the selection itself. Elements added: none persistent. Removed: modal.

**"New users don't know what to do on the empty dashboard — add three CTA cards and a tour."**
Element-first: cards + coach marks.
Interaction-first (rung 1–2): populate the dashboard with the user's own data from signup context (company, imported items, sample derived from their domain); the first real action is available on the first real object. If nothing can be inferred, one CTA, not three. Elements added: one. Removed: tour, two cards.

**"Users miss important notifications — make the badge red and bigger."**
Element-first: bigger badge, toast, sound.
Interaction-first (calm): distinguish by foghorn test. Only action-required events move to center (inline, at the object needing action). Everything else is a peripheral count that the user pulls. Elements added: none. Changed: routing of existing signal.

**"Add a settings page so users can configure the agent."**
Element-first: settings page with 12 toggles.
Interaction-first (Amershi G17 + rung 2): the agent learns from corrections (G13); global controls reduce to on/off and scope (what it may touch). Preferences the user never changes are excise. Elements added: two controls. Removed: ten.

## Anti-pattern lexicon

| Smell | What it usually means | Fix |
|---|---|---|
| Tooltip/help text on a control | Mapping or label is wrong | Fix the mapping; rename; make the effect visible |
| Confirmation dialog | Action isn't reversible | Make it reversible; show undo |
| Badge/banner announcing state | Feedback is missing where the action happened | Put feedback on the object, in the periphery |
| "Advanced" section that everyone opens | Wrong default | Change the default |
| Wizard for a 3-field task | Excise dressed as guidance | One screen, inferred defaults |
| Toggle that changes what other controls do | Mode | Remove, or quasimode |
| Two ways to do the same thing | Discoverability patch | Keep one; fix its signifier |
| Thumbs up/down on every AI output | Feedback channel bolted on | Let editing be the feedback |
| Plan/steps viewer by default | Agent explaining instead of scoping | Act or scope down; explanation on request |
| Empty state with N CTAs | Nothing inferred | Infer; one CTA max |

## Scope by product type

The ladder, gulfs, channels-as-meaning, ledger, motion grammar, and review protocol are universal. Two things vary by product class — the channel *map* (what position, heat, glow encode here) and the definition of *cost*:

- **Task / decision products** (ops, fintech, admin SaaS, productivity, e-commerce checkout): full strength, as written. Interaction is cost; the concrete channel assignments in Step 4.5 and all of Step 4.6 apply.
- **Consumption / social products** (feeds, media, community): the meta-rules hold; the concrete assignments don't. There is no commit, heat has no SLA, one-glow-per-screen is meaningless on a feed. Re-derive the channel map from the product's actual meanings before applying 4.5, and skip 4.6. Attention is the revenue here, so the ethics of "reduce interaction cost" changes sign — reducing friction toward compulsive consumption is not a win; the ledger should count engagement mechanics the way it counts elements.
- **Learning, games, fitness** (anywhere effort is the product): split the surface. Chrome around the core loop (navigation, enrollment, resume, finding the next thing) gets full strength — most of these products fail exactly there. Inside the core loop the central bet inverts: effortful interaction IS the product (desirable difficulties — retrieval beats re-reading because it is harder), so never infer away or smooth the struggle. Friction there is deliberate, budgeted like an element, and measured in retention or mastery, not clicks.
- **Persuasion artifacts** (landing/marketing pages): mostly out of scope; Hick's law on calls-to-action is about all that transfers.

Extend by overlay, not by generalizing the core: when a new product class enters real design rounds, write a ~60-line overlay (channel remap + cost redefinition + class-specific regression items), hardened against that product's reviews. An overlay fighting the core is a separate skill.

## References

Read these when you need the underlying argument, the full guideline sets, or citations for a design rationale:

- `references/foundations.md` — the interaction-design canon: Norman's principles and the two gulfs, Hutchins/Hollan/Norman on directness, Verplank's Do/Feel/Know, Raskin's modes and habituation, Cooper's goal-directed principles and excise, Saffer's microinteraction anatomy, Nielsen's progressive disclosure, Bret Victor's Magic Ink, Weiser & Brown's calm technology, Krishna's NoUI principles, Herigstad's spatial/motion/distance practice. With source links.
- `references/ai-agent-interaction.md` — Horvitz's 12 mixed-initiative principles, Microsoft's 18 Human-AI Interaction guidelines (full text), Google PAIR guidebook structure, Nielsen's intent-based paradigm, and how each maps to reducing interface. With source links.
- `references/design-review-protocol.md` — how to review design work (your own or a design agent's) across rounds: render-and-walk practice, viewport tiers, the craft pass, inheriting an existing UI (redesign mode, audit as ledger round zero, what never changes silently), the regression watchlist, self-limiting system rules, comply-or-argue collaboration, and the severity-ranked review output format. Read it whenever auditing screens, prototypes, or a design system.
- `references/craft-baseline.md` — measurable exit criteria (WCAG 2.2 AA, Apple HIG, Material Design numbers) for elements that survived the ledger: contrast, keyboard and focus, touch targets, type resilience, responsive tiers, the confirm-vs-undo rule, motion, layout stability, charts. Read it for any craft/accessibility QA pass or before calling UI work delivery-ready. It judges quality only — it can never add an element.
