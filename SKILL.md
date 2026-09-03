---
name: interaction-first-design
description: Design or review interaction behavior in user flows, state and feedback systems, irreversible or agent-initiated actions, and high-stakes UI. Use for explicit UX/design audits and when a frontend change materially alters how a person acts or understands system state. Do not invoke for visual-only styling, copy-only edits, or routine component implementation whose interaction semantics are unchanged.
---

# Interaction-first design

## Scope and authority

- In a **review**, inspect and report. Do not edit product files or create design documentation unless the user asks for changes.
- In an **implementation or redesign**, preserve the requested platform, design system, product constraints, and explicit stakeholder decisions. Raise a concise objection only when a requested pattern creates a concrete usability, accessibility, safety, permission, or compliance risk; otherwise execute it.
- Treat this skill's principles as decision criteria, not universal laws. Accessibility, safety, permission, legal requirements, product conventions, and relevant user research outrank a generic preference here.
- Ask only for information that would materially change the result. Do not guess through unresolved identity, privacy, permission, legal, or irreversible-action decisions.

## Core stance

Design the loop between intent, action, system response, and the person's next decision before choosing interface elements. The aim is not a minimal element count; it is the least interaction cost that lets people act safely and understand what happened.

1. **Design the interaction, not the widget.** Start with the person's goal and the complete action-feedback loop.
2. **Treat interface as a cost, not as proof of completeness.** New elements cost attention, learning, space, state, accessibility work, and maintenance; keep them when they close a real gulf better than a cheaper interaction.
3. **Infer only within authority and privacy boundaries.** Use safe context and history before asking, but never cross identities, sessions, permissions, or regulated decision boundaries.
4. **Prefer correction to confirmation only when the action is authorized, observable, inexpensive, and genuinely reversible.** Otherwise use preview, review, authentication, or focused confirmation as the risk requires.
5. **Keep routine status calm and actionable exceptions prominent.** Privacy-sensitive state may need to remain hidden until summoned.
6. **Protect habits without preserving defects.** Keep inputs and action semantics stable; make necessary modes explicit and test them for wrong-target errors.

This is a synthesis of the interaction-design sources in `references/foundations.md`, not a claim that every source mandates one interface style.

## Decision layers

Consider **existence** (does the task need this mechanism?), **quality** (does it meet applicable standards and platform expectations?), then **style** (how should it look and feel?). This order prevents decoration from inventing functionality, but it does not make accessibility, safety, law, or platform requirements subordinate: route any required mechanism back through the existence decision and keep it when it is justified.

## Workflow

Scale this workflow to the task. A small behavior change may need one sentence per step; a high-stakes flow needs explicit evidence and failure states.

### Step 1 — Name the goal and the gulf

State the person's intended end state and whether the main gap is **execution** (how to act) or **evaluation** (what happened or what state the system is in). Include the relevant distance, attention, input modality, who else can see the surface, and any authority, reversibility, safety, privacy, legal, or collaboration constraints.

If two plausible readings would materially change the design, ask one focused question when possible. Otherwise state the working assumption and proceed. For an inherited product, read `references/design-review-protocol.md` before changing established habits.

### Step 2 — Climb the Ladder of Least Interface

Choose the lowest-cost rung that closes the gulf without violating the constraints above. Lower rungs are not automatically better: accessibility, comprehension, authority, safety, consent, collaboration, or recovery may require a higher rung.

| Rung | Move | Source |
|---|---|---|
| 0 | **Eliminate.** Remove the need. The problem is excise (work the software imposes, not the goal demands). Better default, remove the step, remove the feature. | Cooper (excise), Raskin |
| 1 | **Infer from environment.** Use authorized, relevant context such as device, current selection, viewport, or what's on screen. Do not infer across identity, privacy, or permission boundaries. | Victor (Magic Ink), Amershi G4 |
| 2 | **Infer from history.** Reuse prior choices only when identity is known, retention is appropriate, and the context is stable. | Victor, Saffer ("bring the data forward"), Amershi G12–13 |
| 3 | **Act automatically with cheap undo.** When authority is clear and the effect is observable and fully restorable, do the probable thing and make reversal easy. | Cooper ("ask forgiveness, not permission"), Horvitz (act/ask/wait thresholds) |
| 4 | **Fold into an existing interaction.** Put the action on the object itself when the affordance remains discoverable and has accessible input alternatives: sortable column header, drag-to-reorder plus keyboard controls, tap the number to edit it. | Shneiderman, Hutchins/Hollan/Norman (direct engagement) |
| 5 | **Disclose progressively.** Show the primary path only; reveal secondary options on request, in context, near the trigger. Not a new persistent element — a conditional one. | Nielsen (progressive disclosure), Cooper ("design for the probable, provide for the possible") |
| 5.5 | **Reuse a perceptual channel.** Give the fact to a suitable property of an existing surface. This adds no discrete element but still spends semantic and accessibility budget. | Weiser (periphery) |
| 6 | **Add a new element.** Use it when it closes the gulf better than the lower rungs, and account for its cost. | — |

Questions, forms, confirmations, and explanations add work, but they are appropriate when inference would be unsafe, authority is unclear, consequences are difficult to recover from, or comprehension and disclosure require them.

### Step 3 — Design the interaction, not the widget

Define the smallest complete loop: trigger, physical action, state-transition rules, feedback, failure and recovery, repetition, and any modes. State what the person must perceive and understand to predict the result. Prefer direct manipulation when it improves control, but do not force it when an accessible symbolic, conversational, or mediated interaction better fits the task.

### Step 4 — Apply the constraints

Check that the interaction is predictable, accessible across supported input modalities, genuinely recoverable where claimed, direct enough, proportionate in prominence, consistent with the product, and safe after habits form. Hidden state must not silently change a command's target or consequence. A recovery mechanism must actually restore the affected state; compensation, a delayed second transaction, or a support process is not undo.

For recurring-state surfaces or commit controls, read `references/interaction-patterns.md`. It provides a method for deriving a product-specific channel map and safe action semantics; its examples are not universal assignments.

### Step 5 — Account for interaction cost

Record additions, removals, and changed signals when a ledger is requested or already part of the project. Evaluate attention, motor effort, learning, layout, state, copy, accessibility, privacy, and maintenance—not only the raw element count.

A new element needs a concrete purpose and an exit criterion. It does **not** have to retire another element when accessibility, safety, law, a genuinely new capability, or a lower total task cost justifies it. A restyle should not introduce unrelated functionality, but a justified semantic or accessible mechanism is not a failed restyle merely because it is visible.

For the ledger format, persistence rules, inherited interfaces, or multi-round governance, read `references/design-review-protocol.md`.

## When the product contains an AI agent

Read `references/ai-agent-interaction.md` whenever a model infers intent, generates content, or acts on the person's behalf. Establish **authorization separately from confidence and reversibility**. Direct invocation, dismissal, correction, and undo are a useful starting surface for many low- and medium-risk features, not a complete control set: add preview, approval, authentication, explanation, collaboration, audit, or recovery controls when authority, consequence, policy, or shared work requires them.

## Interaction spec

Write this before code or mockups when the behavior is material:

```
INTERACTION: <verb + object>
Goal and gulf: <end state; execution or evaluation gap>
Chosen rung: <0–6 and why it fits>
Trigger and action: <who initiates; what they physically do>
Rules and feedback: <state transition; what changes, where, and how quickly>
Failure and recovery: <rejection, interruption, retry, undo or restore>
Modes and repetition: <state that changes mappings; repeated-use effect>
Elements changed: <added, removed, or altered, with costs>
```

Put the spec only in a repository-approved location or the response. Do not create documentation during a review.

## Conditional guidance

Read only what the task needs:

- **Recurring-state surfaces or commit controls:** `references/interaction-patterns.md`.
- **AI systems that infer, generate, or act:** `references/ai-agent-interaction.md`.
- **Money, health, safety, government, consent, children, privacy, shared devices, feeds, learning/games, or persuasion surfaces:** `references/product-class-overlays.md`.
- **Design reviews, inherited products, design systems, or multi-round work:** `references/design-review-protocol.md`.
- **Implementation quality or accessibility checks:** `references/craft-baseline.md`.
- **Source rationale:** `references/foundations.md`.
- **Calibration when a ladder decision remains unclear:** `references/worked-examples.md`.

## Review output

Open with **Ship / Ship with fixes / Needs work**. State what evidence was inspected or exercised, distinguish observed, source-based, measured, and heuristic findings, and rank issues by user and release impact. For each finding give observation → applicable requirement or principle → impact → concrete fix. Lead with the most consequential simplification, but retain required controls and disclosures. Summarize element changes and net interaction cost; do not use raw element delta as the verdict.

Reviews remain read-only unless the user asks for implementation. The evidence rules, severity definitions, and regression checks are in `references/design-review-protocol.md`.
