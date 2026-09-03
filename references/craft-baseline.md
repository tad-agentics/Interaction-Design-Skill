# Craft baseline — measurable exit criteria

Pass/fail numbers for UI that has already survived the interaction-first workflow. Sources: WCAG 2.2 AA, Apple HIG, Material Design.

**Scope rule (do not skip):** this baseline judges **how well an element is built, never whether it should exist**. An element enters this checklist only after it has a ledger entry (SKILL.md Step 5). If a check here seems to demand a *new* element ("add a tooltip", "add a badge", "add an empty-state block"), that is a ladder question — go to SKILL.md Step 2 and climb from rung 0. This file never adds elements; it only sets the bar for the ones that survived.

Run this as the **craft pass** of a design review (see `design-review-protocol.md`) or as pre-delivery exit criteria before calling UI work complete.

## 1. Contrast & color

- Body text ≥ **4.5:1** against its background; large text (≥ 24px, or ≥ 18.66px bold) and UI components/focus indicators ≥ **3:1**. Measure at the strongest tint — the tinted edge, not the white centre.
- Verify in **both** light and dark mode; dark mode is where tinted surfaces silently fail.
- No state is hue-only — every colour channel has its non-colour twin (text, shape, luminance). This restates the channel-twin law (SKILL.md Step 4.5); here it is a measurable check, not a design choice.
- Colors come from named tokens with one meaning each; a raw hex in a component is a finding.

## 2. Keyboard & focus

- Every interactive element reachable by Tab; order matches visual order; no traps.
- Focus visibly indicated (≥ 3:1 against adjacent colors); never removed, only restyled.
- Sticky bars, overlays, and banners must not hide the focused control (WCAG 2.2 focus-not-obscured).
- Every drag interaction has a single-pointer and keyboard alternative (WCAG 2.2).
- Modals and multi-step flows have an escape route (Esc / cancel / back) that loses no work — reconcile with autosave, not a "discard changes?" dialog.
- Authentication allows paste and password managers; never blocks either.
- A keystroke never acts on something other than what holds focus (restates SKILL.md Step 4.6; here it is a test to run, not a rule to remember).

## 3. Touch & pointer targets

- Touch targets ≥ **44×44 pt** (Apple) / **48×48 dp** (Material); web pointer targets ≥ **24×24 CSS px** (WCAG 2.2 minimum). Extend the hit area beyond the visual bounds rather than growing the visual.
- ≥ **8 px/dp** between adjacent targets.
- Nothing depends on hover alone; every hover-revealed affordance has a tap/focus equivalent.

## 4. Type & text resilience

- Body base ≥ **16px**, line-height ≈ **1.5**; nothing below **12px** anywhere.
- Survives system text scaling (Dynamic Type / font-size settings) without truncation or clipped containers.
- Survives translation expansion: budget **+15–25%** width and taller diacritics (Vietnamese is the house test case).
- Stress every text container with a very long string and with emptiness; layout degrades gracefully (wrap or defined truncation with full value reachable), never breaks.

## 5. Responsive

- Walk **375 / 768 / 1024 / 1440 / 1920** and screenshot each tier.
- No horizontal page scroll at any tier; wide content scrolls inside its own container.
- Content reflows rather than shrinking; images reflow, not scale to illegibility; navigation collapses deliberately (and what it collapses *to* went through the ladder).
- Viewport meta present; pinch-zoom never disabled.

## 6. Feedback, reversal & failure (the reconciled confirm/undo rule)

- **Reversible action → act immediately, one-gesture undo, no confirmation.** (Ladder rung 3.)
- **Confirmation only where undo cannot reach**: irreversible external effects — a message sent, a payment executed, content published, data destroyed with no restore path. If soft-delete or versioning can create a restore path, build that instead of the dialog. This is the *entire* legitimate territory of confirmation dialogs.
- Unsaved-work warnings are a finding, not a fix: autosave removes the problem the dialog guards.
- Async controls show an in-progress state and are single-fire (no double-submit).
- Success feedback is peripheral and fades; normalcy is never reported with a dialog (Cooper). Only action-required outcomes move to center.
- Every irreversible commit has a defined failure state: what the user sees when the backend rejects, the network drops, permission is denied. Error messages sit next to the field/object they concern and name the recovery path.
- The undo affordance appears where the action happened, survives long enough to be used, and actually restores state (test it).

## 7. Motion

- `prefers-reduced-motion` honored: animation reduced or removed, function intact.
- Animate transform/opacity only; never width/height/top/left (layout thrash).
- Exits faster than entrances; motion means "the world changed" and nothing else (SKILL.md motion grammar — no idle loops, shimmer, or refresh animation). Anything auto-advancing (carousel, ticker) has pause/stop and halts on focus.

## 8. Layout stability & performance

- CLS < **0.1**: reserve space for images, embeds, and async content before they load.
- Below-the-fold media lazy-loads; long lists virtualize.
- Console clean on the walked flows: no errors, failed requests, or 404 assets.

## 9. Data & charts (for charts that survived the ledger)

- Every value readable without color: direct labels, tooltips on interact, or an accessible table twin.
- Axes labeled with units; no truncated/rotated axis text on mobile — reflow or simplify the chart instead.
- The empty render is a *designed* state, and its design routes through the ladder (infer real data first, rung 1–2; one CTA max) — a "No data yet" block with three buttons is a ladder violation wearing a craft badge.

## Using this file in a review

Report craft findings in the standard format (observation → rule broken, by name → fix), ranked with the review's severity tiers. A craft finding proposes a change **to an existing element**; if the honest fix is a new element, write it up as a ladder/ledger item instead and say so.
