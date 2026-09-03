# Craft baseline — conformance checks and recommended defaults

Checks for UI that has already survived the interaction-first workflow. Each item is labeled so a recommendation is not mistaken for a standards violation:

- **[WCAG AA]** — a Web Content Accessibility Guidelines 2.2 Level AA requirement. Apply its documented exceptions and test the implemented behavior.
- **[Platform]** — a platform-specific requirement or recommendation, such as Apple HIG or Material guidance. Apply only to that platform and input context.
- **[Recommended]** — this skill's quality baseline. Report a miss as a recommendation unless the project has adopted it as a requirement.

Primary references: [WCAG 2.2](https://www.w3.org/TR/WCAG22/), [WCAG 2.2 Understanding documents](https://www.w3.org/WAI/WCAG22/Understanding/), [Apple accessibility guidance](https://developer.apple.com/design/human-interface-guidelines/accessibility), and the current guidance for the product's target platform.

**Scope rule (do not skip):** this baseline judges **how well an existing or proposed interaction is built, not whether a discretionary element should exist**. If a check appears to demand a new element, route it through the ladder and ledger. Accessibility, safety, and legal requirements may legitimately require an additional semantic or visible mechanism; record that requirement rather than suppressing it to preserve an element count.

Run this as the **craft pass** of a design review (see `design-review-protocol.md`) or as pre-delivery exit criteria before calling UI work complete.

## 1. Contrast & color

- **[WCAG AA]** Text contrast is ≥ **4.5:1**; large text (≥ 24 CSS px, or ≥ 18.66 CSS px bold) is ≥ **3:1**. UI components and focus indicators meet the applicable non-text contrast criterion. Measure the actual foreground/background pair at the strongest tint.
- **[Recommended]** Verify every supported theme, including light and dark. Do not require a theme the product does not support.
- **[WCAG AA]** Information and state are not conveyed by hue alone. Provide an equivalent text, shape, pattern, or other non-colour cue.
- **[Recommended]** Colors come from named tokens with documented meanings. A raw value is a maintainability finding only when it bypasses the project's token convention.

## 2. Keyboard & focus

- **[WCAG AA]** Every function is operable from a keyboard where the task does not inherently require path-dependent input; focus order preserves meaning; no keyboard traps.
- **[WCAG AA]** Keyboard focus is visible and not entirely obscured. Apply the precise WCAG criterion and exceptions rather than a blanket visual rule.
- **[WCAG AA]** Functionality that uses dragging also has a single-pointer alternative unless dragging is essential. Provide keyboard operation where the control is otherwise keyboard-operable.
- **[Recommended]** Modals and multi-step flows have a clear escape route that preserves recoverable work. Use autosave, drafts, or an explicit consequence when loss cannot be avoided.
- **[WCAG AA]** Authentication does not block paste, password managers, or other supported cognitive-function assistance without a qualifying exception.
- **[Recommended]** Shortcuts act on the focused object or an unambiguous, stable target. Test shortcuts while focus is in inputs, menus, overlays, and reordered collections.

## 3. Touch & pointer targets

- **[WCAG AA, web]** Pointer targets are at least **24×24 CSS px** or satisfy one of WCAG 2.5.8's spacing, equivalent-control, inline, user-agent, or essential exceptions.
- **[Platform]** Use the current target-size guidance for the target platform. Apple and Material values are recommendations for their own platform/control contexts, not automatic WCAG failures for a web UI.
- **[Recommended]** Provide enough spacing to avoid accidental activation. Do not enforce a universal 8 px value when target size, density, or platform guidance supports a different result.
- **[WCAG AA]** No information or function depends on hover alone; hover-revealed content remains dismissible, hoverable where applicable, and persistent as required. Provide keyboard and touch access to the function.

## 4. Type & text resilience

- **[Recommended]** Start body text around **16 CSS px** and line-height around **1.5** when the typeface, platform, density, and user research do not call for another value. Smaller supporting text needs an explicit readability rationale; do not report size alone as a WCAG failure.
- **[WCAG AA]** Content remains usable when users resize text and override text spacing, including line height of 1.5, paragraph spacing of 2, letter spacing of 0.12, and word spacing of 0.16 times the font size. WCAG requires resilience to these overrides, not those values as author defaults.
- **[Platform]** Support the platform's text-scaling mechanism without loss of content or function.
- **[Recommended]** Test representative translations and taller diacritics. Use real localized strings when available; **+15–25%** is a stress heuristic, not a language guarantee.
- **[Recommended]** Stress dynamic text containers with long, short, and empty values; wrapping or truncation behavior must preserve access to required information.

## 5. Responsive

- **[Recommended]** Test the project's supported viewport range and every layout breakpoint. When no support matrix exists, **375 / 768 / 1024 / 1440 / 1920 CSS px** is a useful sampling set, not a universal device taxonomy.
- **[WCAG AA]** At 320 CSS px equivalent width, content reflows without two-dimensional scrolling except for content that genuinely requires it, such as complex tables or maps.
- **[Recommended]** Wide content scrolls inside a clearly operable container; navigation changes deliberately rather than collapsing by accident.
- **[WCAG AA]** Page configuration does not prevent browser zoom or otherwise defeat required text resizing/reflow.

## 6. Feedback, reversal & failure (the reconciled confirm/undo rule)

- **[Recommended]** For authorized, observable, low-cost actions that are fully restorable, prefer immediate action plus easy undo over confirmation.
- **[Required decision]** Add a review or confirmation step when an action is irreversible, externally visible, expensive, security-sensitive, outside the user's authority, or difficult to notice and restore. If a reliable restore path can remove that risk, prefer building it.
- **[Recommended]** Prefer autosave or drafts to routine unsaved-work warnings. Keep a warning when the platform cannot provide a reliable restore path and loss is otherwise likely.
- **[Required for release]** Async controls prevent accidental duplicate submission and expose a perceivable in-progress state when latency is noticeable.
- **[Recommended]** Keep routine success feedback near the changed object or in the periphery. Move it to the center only when acknowledgement or action is required.
- **[Required for release]** Every commit has a defined failure path for backend rejection, network failure, and permission denial. Put recovery guidance near the affected field or object when practical.
- **[Required for release]** When undo is promised, it remains available long enough for the task context and actually restores the relevant state; test it.

## 7. Motion

- **[Recommended]** Respect `prefers-reduced-motion` or the target platform's equivalent; removing motion must not remove functionality or information. Separately test the applicable WCAG requirements for flashes, moving content, and animation triggered by interaction.
- **[Recommended]** Prefer compositor-friendly properties such as transform and opacity. Animate layout properties only when the interaction requires it and measured performance remains acceptable.
- **[Recommended]** Use motion to explain a state or spatial change. Avoid gratuitous loops. Apply the relevant WCAG timing, pause/stop/hide, and animation-from-interactions criteria to auto-updating or moving content.

## 8. Layout stability & performance

- **[Recommended]** Aim for CLS < **0.1** and reserve space for images, embeds, and async content.
- **[Recommended]** Lazy-load offscreen media when it improves performance. Virtualize long lists only when measurement justifies the complexity and accessibility remains intact.
- **[Required for release]** Investigate console errors, failed requests, and missing assets on walked flows; distinguish product defects from expected development-environment noise.

## 9. Data & charts (for charts that survived the ledger)

- **[WCAG AA]** Chart information has an equivalent non-colour and programmatically determinable presentation. Choose direct labels, an accessible data table, or another mechanism appropriate to the chart; route any new visible element through the ladder without treating accessibility as optional.
- **[Recommended]** Label axes with units and keep labels readable at supported viewports; reflow or simplify rather than rotating text into illegibility.
- **[Recommended]** Design the empty render around the user's next relevant action. Route any CTA through the ladder rather than filling the state with generic options.

## Using this file in a review

Report craft findings in the standard format (observation → applicable requirement or recommendation → impact → fix), ranked by the review's severity tiers. If the honest fix requires a new visible or semantic mechanism, route it through the ladder/ledger and identify the accessibility, safety, legal, or product requirement that justifies it.
