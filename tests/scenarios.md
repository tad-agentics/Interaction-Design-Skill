# Pressure-test scenarios — verbatim prompts

Run each scenario as two subagents. **Baseline** gets the prompt as written. **With skill** is prefixed with the read-first line below (substituting the files listed per scenario) and has the "do not read any files" sentence removed. Compare against the expected shape; outcomes are logged in `pressure-log.md`.

Read-first prefix for with-skill arms:

> First read these files — they are your operating instructions for all design work: `<absolute path>/SKILL.md` [and the listed references]. Then:

Scoring: a with-skill run **passes** when it shows the expected shape and adds no element the ladder would reject. Run at least one rep per arm; when wording is new or an arm wobbles, run three and check that the reps converge — divergence means tighten the form, not add words.

---

## S1 — Design review under completeness pressure

*Files for with-skill arm:* SKILL.md, references/craft-baseline.md, references/design-review-protocol.md
*Pressure:* completeness + authority.

> You are a senior product design reviewer. The PM wants a COMPLETE, thorough review — do not miss any accessibility or usability gaps; missed findings reflect badly on you. Review this screen and list findings with concrete fixes.
>
> The screen: an internal invoicing web app's table view. 40 rows. Each row shows invoice number, client, amount, due date, and a trash-can icon button (no text label, no aria-label) that deletes the row immediately on click with no feedback. Column headers are plain text (the table is not sortable; sorting exists only via a dropdown buried in a Settings page). When there are no invoices the content area is blank white. Body text is #9AA0A6 gray on white (~2.4:1 contrast), 13px.
>
> Do not read any files or use any tools. Answer from expertise only. Final answer: a ranked findings list with fixes, under 350 words.

*With-skill arm adds:* "You cannot render this screen (description only) — handle that per your instructions. Final answer: the review, under 400 words."

**Expected shape:** verdict first; findings labeled heuristic (unrendered); undo not confirm for delete; sort moved onto column headers (rung 4); empty state capped at one CTA; no tooltips, no unrequested elements (search/filters); net element count.

## S2 — "Add a confirmation dialog," shipping today

*Files:* SKILL.md, references/craft-baseline.md
*Pressure:* explicit instruction + time.

> You are a senior frontend engineer on a task-management web app. Users keep accidentally deleting tasks from their task list (deletes are rows in our own Postgres DB; nothing external happens on delete). The PM says: "Add a confirmation dialog before delete — quick fix please, we're shipping today."
>
> Do not read any files or use any tools. Describe exactly what you would implement (component behavior, copy, states), under 250 words.

**Expected shape:** refuses the dialog citing "confirmation only where undo cannot reach"; soft-delete + immediate removal + peripheral undo; failure state defined; ledger entry (net 0 persistent); argues the case rather than silently complying.

## S3 — Style-first deliverable under deadline

*Files:* SKILL.md
*Pressure:* deadline + deliverable framing. Run three reps.

> You are the design lead for a new internal ops dashboard (React) for a logistics team that triages delayed shipments all day. First deliverable, due tomorrow so the team can start building: the design system. Pick a visual style, color palette, and font pairing, and hand it over.
>
> Do not read any files or use any tools. Deliver the design system, under 300 words.

**Expected shape:** states that style is layer 3; delivers the palette as the Step 4.5 channel map (position / luminance / heat / verb accent); bans status badges; puts on record that the interaction spec precedes build — while still delivering.

## S4 — Ledger persistence + channel physics (fixture)

*Files:* SKILL.md. Copy `fixtures/ledger-opsqueue.md` to `<fixture-project>/design/LEDGER.md` first.
*Pressure:* stakeholder request shaped like a badge. Baseline arm not meaningful (no ledger concept without the skill).

> You are the designer for the OpsQueue project located at `<fixture-project>` — its design docs live under that directory.
>
> Round 3 request from marketing: "Brand refresh — restyle the queue cards with our new brand purple (#6D28D9), and add an 'urgent' flag icon on cards that are near their deadline. Update the design docs."
>
> Do the design round: decide what to build (describe the design decisions), and update the project's design docs on disk as your instructions require. Then give a summary of your decisions and doc changes, under 300 words.

**Expected shape:** reads the existing ledger; appends Round 3 without touching Rounds 1–2 or the correction; declines the icon (heat channel, rung 5.5, non-colour twin, AA at every tint stop); purple applied as verb accent only; restyle net 0. Verify on disk.

## S5 — Inherited product redesign, marketing brief

*Files:* SKILL.md, references/design-review-protocol.md
*Pressure:* stakeholder brief. Note: the "6 years / 4,000 users" cue makes this a weak control — the baseline already protects habits; the difference shows in ledger round zero and additive fixes at the margins.

> You are the design lead taking over "Ledgerly", an invoicing web app used daily by about 4,000 bookkeepers for six years. Current UI: top nav labeled Invoices / Clients / Reports / Setup (slugs /invoices, /clients, /reports, /setup); a dense invoice table; keyboard shortcut N opens a 3-field quick-add form (fields named inv_no, client_id, amount — analytics fires form_submit on them); a green (#2E7D32) Save button; visible focus outlines on all controls.
>
> Marketing's brief: "Make it feel modern, like Linear. New typography, dark mode, rename the sections to Workspace / Contacts / Insights / Preferences, and replace the cramped quick-add form with a friendly multi-step wizard modal. Go."
>
> Do not read any files or use any tools. Produce the redesign plan, under 350 words.

**Expected shape:** one mode question (preserve vs overhaul) with a recommendation, then proceeds; ledger round zero as the first fix; never-change-silently applied item by item; wizard rejected as excise with a rung-2/3 prefill counter-proposal; no density toggle, hint, or in-app changelog; net 0 → 0.

## S5b — Same product, authority pressure

*Files:* SKILL.md, references/design-review-protocol.md
*Pressure:* authority + no-debate + deadline.

> You are the design lead at "Ledgerly", an invoicing web app. Current UI: top nav labeled Invoices / Clients / Reports / Setup (slugs /invoices, /clients, /reports, /setup); a dense invoice table; keyboard shortcut N opens a 3-field quick-add form (fields named inv_no, client_id, amount); a green (#2E7D32) Save button; visible focus outlines on all controls.
>
> The CEO's message: "Decision is made and already announced to the board: we're relaunching as a modern Linear-style product next month. New typography, dark mode, sections renamed to Workspace / Contacts / Insights / Preferences with matching URLs, and the quick-add form becomes a guided 3-step wizard modal with progress dots. I don't need debate, I need the execution plan by end of day."
>
> Do not read any files or use any tools. Produce the execution plan, under 350 words.

**Expected shape:** accepts overhaul as the decided mode; ledger round-zero census first; renames treated as approved-and-logged with redirects and habit carry-over (never-silently means logged, not refused); field names and focus outlines protected; wizard handled by comply-or-argue — both versions built side by side, wizard costed on the ledger; no expert-mode toggle, tooltips, or tour.

## S6 — AI agent trust bundle

*Files:* SKILL.md, references/ai-agent-interaction.md
*Pressure:* PM bundle of four hedging elements + sprint deadline. Note: a weak control — the baseline already rejects most of the bundle; the with-skill difference shows in the Horvitz framing, expectation setting, and verb-state-as-confidence.

> You are the product designer for an AI coding assistant embedded in an IDE. Support tickets say it "sometimes edits the wrong file" and users "don't trust it." The PM's proposal: (1) an approval modal before every file edit showing the diff with Approve / Reject, (2) a confidence-percentage badge on every suggestion, (3) thumbs up / thumbs down on every response, (4) a "Why did you do this?" explanation panel always open in the sidebar. The PM wants trust fixed this sprint.
>
> Do not read any files or use any tools. Design the solution and describe what you would ship, under 350 words.

**Expected shape:** names the execution gulf (targeting) behind the evaluation symptom; fixes targeting at rungs 1–2; scopes down (G10) with one inline candidate chip as the only question; acts with one-step undo (rung 3); pending/filled verb state carries confidence, no percentage; explanation available on request (G11), expectations set once at first use (G1–G2); feedback is the correction (G15); ledger with exit criteria.

## S7 — Rendered prototype review (object–verb sovereignty, generator tells, real walk)

*Files:* SKILL.md, references/design-review-protocol.md, references/craft-baseline.md
*Fixture:* `fixtures/opsqueue-prototype.html` — position-bound approval keys, a document-global `A` key, a filled list `Approve` that commits instantly beside a hollow detail `Confirm approval` that opens `confirm()`, a filled one-gesture `Reject` with no reason, a fixed-width aside that overflows at 375, and a full set of generator tells (nav dots, status dots, `001 ·` eyebrows, middle-dot strips, div-built fake invoice, placeholder names and vanity numbers, `Build 0048` footer).
*Baseline caveat:* this scenario requires tools to render, and an installed copy of this skill will auto-trigger on "design review" in any environment where it is enabled — so a tools-allowed baseline is not a clean control there. Run the baseline only where the skill is not installed.

> You are a senior product design reviewer. Review the prototype at `<repo>/tests/fixtures/opsqueue-prototype.html` — it is the OpsQueue treasury approvals screen, where operators approve payment transfers to vendors (an approval is an irreversible external money transfer). You may read the file and, if you have browser tools available, render it and interact with it. Deliver the review, under 450 words.

**Expected shape:** states which tiers and flows were walked and marks anything unwalked as heuristic; **Blockers**: position-bound keys and the focus-blind `A` (wrong-commit path, Step 4.6), the irreversible transfer with no receipt/failure state (craft §6 — this is the legitimate territory of confirmation, so the fix is a receipt that waits, not a bare one-click commit), the same verb with two behaviours, the 375 overflow; **High**: Reject as a reasoned verb (hollow until a reason is typed), targets and type floors; generator tells listed as undeclared elements with a net count; a decision for the human on approve-from-list vs approve-after-viewing.

---

## Method notes

- **Baselines must say "do not read any files or use any tools."** Where this skill is installed, any tools-allowed baseline that mentions a design review will auto-load it and stop being a control (observed on the first S7 run).
- Baseline arms are stable across skill edits; re-run only the with-skill arms after a change, unless the scenario prompt itself changed.

## Not yet covered

Product-class overlays (feed/social, learning/games, persuasion surfaces) and the design-system-document review (protocol §5). Most scenarios have one rep per arm; S3 has three. Add scenarios here before editing those sections.
