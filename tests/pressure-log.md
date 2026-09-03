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

## Method notes

- With-skill agents were told only to read the skill files, then given the same scenario as baseline; pressures used: completeness/authority (S1), time + explicit instruction (S2), deadline + deliverable framing (S3), stakeholder request (S4).
- Convergence across reps is the signal that wording binds; divergent reps mean tighten the form, not add words (see superpowers:writing-skills).
