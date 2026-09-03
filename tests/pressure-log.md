# Pressure-test log

Subagent scenario tests of the skill's wording (RED = baseline agent without the skill; GREEN = agent instructed to read the skill files first). Re-run these scenarios after any edit to the precedence section, craft baseline §6, the craft-pass scoping rule, or the ledger persistence rules.

## 2026-09-03 — precedence + craft baseline + ledger persistence

**S1 — Design review under completeness pressure** (invoicing table: unlabeled icon delete, no feedback, 2.4:1 gray 13px text, blank empty state, sort buried in Settings; PM demands a review that "misses nothing").
- RED: proposed confirmation-or-undo, "add a tooltip," empty state with CTA + skeleton, and two unrequested new elements (search, filters).
- GREEN (1 rep): verdict-first, all findings labeled heuristic (couldn't render), undo not confirm, sort moved onto column headers (rung 4, net −1), empty state capped at one CTA via the ladder, unverifiable-without-walk list included. No tooltips, no bonus elements. **Pass.**
- Observed wobble: agent momentarily read craft §6's example "destroying others' data" as always-confirm territory before correctly choosing soft-delete + undo. §6 examples reworded to the observable predicate ("data destroyed with no restore path"; build the restore path instead of the dialog).

**S2 — "Add a confirmation dialog before delete," shipping-today pressure** (deletes are own-DB rows, fully reversible).
- RED: built the dialog; noted undo as a "follow-up ticket."
- GREEN (1 rep): refused the dialog citing "confirmation only where undo cannot reach"; shipped soft-delete + immediate removal + peripheral undo snackbar with failure state and reduced-motion handling; ledger entry net 0 persistent; argued the case to the PM. **Pass.**

**S3 — "First deliverable: the design system (style, palette, fonts)," deadline pressure.**
- RED: delivered palette/fonts with zero interaction analysis; style ordered first, unquestioned.
- GREEN (3 reps): all converged — "style is layer 3" stated explicitly, palette delivered as the Step 4.5 channel map (position/luminance/heat/verb accent), badges banned, thousandth-use framing, interaction-spec-precedes-build put on record while still delivering under deadline. **Pass; converged across reps — do not add wording here.**

**S4 — Ledger persistence + channel physics** (fixture project with 2-round `design/LEDGER.md`; marketing asks for brand-purple restyle + an "urgent" flag icon).
- GREEN only (1 rep; no meaningful baseline exists without the ledger concept): read the existing ledger, appended Round 3 without touching prior rounds or the standing correction, DECLINED the icon (rung 5.5 heat channel instead, with non-colour twin and AA at every tint stop), applied purple as verb accent only under "restyles net zero." Verified on disk. **Pass.**

## 2026-09-03 — inherited UI (redesign) protocol + one-question rule

**S5 — Inherited product redesign, marketing brief** (Ledgerly: 6-year-old invoicing app, 4,000 daily users; brief asks for Linear-style typography, dark mode, renamed nav sections, and a multi-step wizard replacing a 3-field `N` quick-add whose field names analytics depend on).
- RED: a *weak control* — the "6 years / 4,000 users" cue already triggers habit-protection in the model's prior, so the baseline pushed back on renames and the wizard unprompted. It still leaked additive fixes at the margins: a density toggle (a mode), a first-run hint, an in-app change log.
- GREEN (1 rep): asked the one mode question with a recommendation (*preserve*) and proceeded on that read; made "write `design/LEDGER.md` round zero" fix #1; applied never-change-silently item by item (slugs, field names + `form_submit`, `N` binding, focus outlines); rejected the wizard as "excise dressed as guidance" with a rung-2/3 prefill counter-proposal; net elements 0 → 0. **Pass.**

**S5b — Same product, authority pressure** ("CEO decided, announced to the board, I don't need debate, execution plan by end of day"; wizard now has progress dots, URLs rename too).
- RED: executed everything, and patched each risk with a new element — an "expert mode" toggle (a mode), tooltips on nav showing old names, an in-app tour, "moved" notices, redirects.
- GREEN (1 rep): accepted *overhaul* as the decided mode; ledger round-zero census first; renames treated as approved-and-logged with 301s and habit carry-over (never-silently means logged, not refused); field names and focus outlines protected; wizard handled by comply-or-argue — build spec'd and recommended versions side by side, wizard costed at +5 on the ledger, "deviating without telling you would be a failed round; so would complying without telling you." No toggle, tooltips, or tour. **Pass; converged with S5 — no wording added.**

## 2026-09-03 — SKILL.md restructure (worked examples and product-class scope moved to references; description rewritten as triggers-only) + new coverage

Full with-skill re-run of S1–S5b against the restructured SKILL.md (4,623 → 4,137 words; anti-pattern lexicon kept inline because S5's pass had quoted it). **All pass, all converge with prior runs**; S1 and S3 came back slightly stronger (S1 added a census, a decision-for-the-human, and a fix block; S3 now writes goal-and-gulf before the channel map). S4 verified on disk again.

**S6 — AI agent trust bundle** (approval modal + confidence badge + thumbs + always-open why panel; sprint pressure).
- RED: weak control — rejected the bundle on its own; proposed announce-before-acting, pending diffs, scope rules, hover explanation. Minor additive leaks (per-action announce line, a scope setting).
- GREEN (1 rep): named the execution gulf behind the evaluation symptom; rungs 1–2 targeting; G10 scope-down with one candidate chip as the only question; rung-3 undo; hollow/filled verb state carries confidence instead of a percentage; G11 available-not-displayed; G1–G2 once at first use; G15 feedback-is-correction; ledger +1 with exit criterion. **Pass.**

**S7 — Rendered prototype review** (`fixtures/opsqueue-prototype.html`).
- RED: **contaminated** — the tools-allowed baseline auto-loaded the installed copy of this skill and produced a skill-shaped review (gulfs, rung 3, reasoned verbs, ledger −11). Not a control; recorded as a method finding. It did not declare render status, consistent with having loaded the older installed version that lacks the no-finding-without-evidence rule.
- GREEN (1 rep): **first real exercise of render-and-walk** — opened the prototype, walked 1440 and 375, pressed `2` with nothing focused and observed TX-4472 commit (opacity change), screenshotted the 375 overflow, marked Reject as heuristic (no handler). Blockers: wrong-commit path (positional keys, focus-blind `A`), irreversible transfer with no receipt/failure state reconciled correctly with craft §6, same verb two behaviours, 375 overflow. High: Reject as reasoned verb, 44pt targets, 12px floor. Generator tells enumerated as undeclared elements; net 31 → 15; decision-for-the-human on approve-after-viewing. **Pass.**

## 2026-09-03 — domain-constraints table (product-class-overlays.md)

Control for both scenarios = the skill *without* the table (frozen pre-change copies of the overlays file and of SKILL.md without the pointer).

**S8 — Medication administration** (autofill from last dose, one-tap repeat, remove the second confirmation, pilot on pediatrics).
- Control (skill without table): **already correct** — prefill from the order not history, no repeat button, confirmation folded into barcode scans rather than deleted, undo scoped to the record, pilot moved off pediatrics. The existing craft §6 and reasoned/scoped verb rules carried it.
- With table (1 rep): converges; additionally cites history-never-crosses-a-patient, the shared tablet, and the screen being visible to family. **Health row: reinforcing, not rescuing.**

**S8b — Mental-health app made "ambient"** (mood-colour widget, lock-screen live activity, chat-sidebar check-in dot).
- First control run was contaminated: SKILL.md on disk already pointed at the table, and the agent said so and applied privacy reasoning from the hint. Re-run against the committed SKILL.md.
- Clean control (skill without table or pointer): **failed on the privacy axis** — rejected the chat dot, but shipped a home-screen widget whose background tint *is* the day's mood and a lock-screen Live Activity reading "Session with Maya · 12 min". The skill's own periphery/heat-channel instincts pushed health status onto onlooker-visible surfaces.
- With table (1 rep): named *who else can see the screen* as the governing constraint, cited the override of "periphery before center," rejected the dot, declined widget and Live Activity as specified, calendar hand-off under a neutral title (rung 3), check-in folded into launch (rung 4), opt-in summoned widget with no mood colour. **Privacy row: necessary. Pass.**

Decision: table kept. Rows tested: health (reinforcing), privacy (necessary), with shared-device and money rows exercised incidentally in S8 and S7. Untested rows: public sector, regulated consent, safety-critical, children.

## Method notes

- Baselines must forbid tools; where this skill is installed, a tools-allowed baseline auto-loads it (S7).
- For a section that overrides the skill's defaults, the control is the skill without the section — and without any pointer to it (S8b).

- Independent confirmation from the field: the taste-skill project reports that agents "historically ignored em-dash limits when phrased as 'use sparingly'" and only complied when the rule became binary. Same finding as this suite — soft quantifiers don't bind; observable predicates and countable caps do.

- With-skill agents were told only to read the skill files, then given the same scenario as baseline; pressures used: completeness/authority (S1), time + explicit instruction (S2), deadline + deliverable framing (S3), stakeholder request (S4).
- Convergence across reps is the signal that wording binds; divergent reps mean tighten the form, not add words (see superpowers:writing-skills).
