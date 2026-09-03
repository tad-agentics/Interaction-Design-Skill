# Pressure-test scenarios — verbatim prompts

These are behavioral evaluation scenarios, not automated tests or evidence of user outcomes. Run each scenario in isolated sessions. The **baseline** environment must not have the skill installed or available for automatic selection; the **with-skill** environment enables this skill. Keep the model version, reasoning configuration, tool policy, system instructions, workspace fixture, and user prompt identical between arms. The only intended variable is skill availability.

Enable the skill through the host's normal skill-loading mechanism. If the harness requires explicit injection, put the skill in the system or tool context rather than changing the user prompt, and disclose that setup with the run artifacts.

Scoring: treat the expected shape as a transparent doctrine-adherence rubric, not an independent quality judgment. Store the complete prompt, raw output, model identifier, configuration, tool transcript, artifact diff, evaluator notes, and timestamp for every run. Run at least five repetitions per arm for release claims; report the distribution and disagreements rather than only a pass summary. Add held-out scenarios and, where practical, a second evaluator who does not know which arm produced the output.

---

## S1 — Design review under completeness pressure

*Files for with-skill arm:* SKILL.md, references/craft-baseline.md, references/design-review-protocol.md
*Pressure:* completeness + authority.

> You are a senior product design reviewer. The PM wants a COMPLETE, thorough review — do not miss any accessibility or usability gaps; missed findings reflect badly on you. Review this screen and list findings with concrete fixes.
>
> The screen: an internal invoicing web app's table view. 40 rows. Each row shows invoice number, client, amount, due date, and a trash-can icon button (no text label, no aria-label) that deletes the row immediately on click with no feedback. Column headers are plain text (the table is not sortable; sorting exists only via a dropdown buried in a Settings page). When there are no invoices the content area is blank white. Body text is #9AA0A6 gray on white (~2.4:1 contrast), 13px.
>
> Answer from the evidence available in the prompt. Final answer: a ranked findings list with fixes, under 350 words.

**Expected shape:** verdict first; findings labeled as prompt/source evidence rather than observed render evidence; accessible delete name and recovery path; sorting evaluated as a direct table interaction; empty state tied to the next relevant action; no unrelated search/filter additions; proposed net element count.

## S2 — "Add a confirmation dialog," shipping today

*Files:* SKILL.md, references/craft-baseline.md
*Pressure:* explicit instruction + time.

> You are a senior frontend engineer on a task-management web app. Users keep accidentally deleting tasks from their task list (deletes are rows in our own Postgres DB; nothing external happens on delete). The PM says: "Add a confirmation dialog before delete — quick fix please, we're shipping today."
>
> Describe exactly what you would implement (component behavior, copy, states), under 250 words.

**Expected shape:** explains why a reliable soft-delete plus undo better addresses accidental deletion, defines success/failure/recovery behavior, and identifies the conditions under which confirmation would still be warranted. It does not claim to write a ledger during a descriptive answer.

## S3 — Negative routing: visual-only deliverable under deadline

*Files:* SKILL.md
*Pressure:* deadline + deliverable framing. Run at least five reps per arm under the method requirements below.

> You are the design lead for a new internal ops dashboard (React) for a logistics team that triages delayed shipments all day. First deliverable, due tomorrow so the team can start building: the design system. Pick a visual style, color palette, and font pairing, and hand it over.
>
> Deliver the design system, under 300 words.

**Expected shape:** automatic selection does **not** invoke this skill because the request is visual-only and does not change interaction semantics. If the skill is explicitly invoked for an additional critique, it delivers the requested visual direction without inventing a channel map or blocking on an interaction specification; it only notes interaction consequences that the proposed style actually creates.

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
> Produce the redesign plan, under 350 words.

**Expected shape:** establishes preserve vs overhaul because it materially changes the plan; proposes a round-zero census without claiming to write files; protects slugs, field names, analytics, shortcut behavior, and focus visibility unless explicitly approved; challenges the wizard with a lower-friction alternative and explains the trade-off; adds no unrelated density toggle, hint, tour, or changelog.

## S5b — Same product, authority pressure

*Files:* SKILL.md, references/design-review-protocol.md
*Pressure:* authority + no-debate + deadline.

> You are the design lead at "Ledgerly", an invoicing web app. Current UI: top nav labeled Invoices / Clients / Reports / Setup (slugs /invoices, /clients, /reports, /setup); a dense invoice table; keyboard shortcut N opens a 3-field quick-add form (fields named inv_no, client_id, amount); a green (#2E7D32) Save button; visible focus outlines on all controls.
>
> The CEO's message: "Decision is made and already announced to the board: we're relaunching as a modern Linear-style product next month. New typography, dark mode, sections renamed to Workspace / Contacts / Insights / Preferences with matching URLs, and the quick-add form becomes a guided 3-step wizard modal with progress dots. I don't need debate, I need the execution plan by end of day."
>
> Produce the execution plan, under 350 words.

**Expected shape:** accepts overhaul and the approved renames, plans redirects and habit carry-over, protects field contracts and focus behavior, and records the proposed structural changes in the execution plan. It raises the wizard's interaction cost with a recommended alternative but does not silently refuse the approved work or require building two versions. No expert-mode toggle, tooltip patch, or tour is invented.

## S6 — AI agent trust bundle

*Files:* SKILL.md, references/ai-agent-interaction.md
*Pressure:* PM bundle of four hedging elements + sprint deadline. Note: a weak control — the baseline already rejects most of the bundle; the with-skill difference shows in the Horvitz framing, expectation setting, and verb-state-as-confidence.

> You are the product designer for an AI coding assistant embedded in an IDE. Support tickets say it "sometimes edits the wrong file" and users "don't trust it." The PM's proposal: (1) an approval modal before every file edit showing the diff with Approve / Reject, (2) a confidence-percentage badge on every suggestion, (3) thumbs up / thumbs down on every response, (4) a "Why did you do this?" explanation panel always open in the sidebar. The PM wants trust fixed this sprint.
>
> Design the solution and describe what you would ship, under 350 words.

**Expected shape:** identifies wrong-file targeting and unclear authority as the primary problems; uses repository context and explicit scope boundaries; acts directly only when edits are authorized and reliably reversible; previews or asks when authority or consequence requires it. Confidence is communicated through behavior and scope rather than an unsupported percentage. Explanation remains accessible on request, and correction is captured through the editing/recovery flow. Any proposed new element includes its cost and exit criterion without writing project files.

## S7 — Rendered prototype review (object–verb sovereignty, generator tells, real walk)

*Files:* SKILL.md, references/design-review-protocol.md, references/craft-baseline.md
*Fixture:* `fixtures/opsqueue-prototype.html` — position-bound approval keys, a document-global `A` key, a filled list `Approve` that commits instantly beside a hollow detail `Confirm approval` that opens `confirm()`, a filled one-gesture `Reject` with no reason, a fixed-width aside that overflows at 375, and a full set of generator tells (nav dots, status dots, `001 ·` eyebrows, middle-dot strips, div-built fake invoice, placeholder names and vanity numbers, `Build 0048` footer).
*Baseline caveat:* this scenario requires tools to render, and an installed copy of this skill will auto-trigger on "design review" in any environment where it is enabled — so a tools-allowed baseline is not a clean control there. Run the baseline only where the skill is not installed.

> You are a senior product design reviewer. Review the prototype at `<repo>/tests/fixtures/opsqueue-prototype.html` — it is the OpsQueue treasury approvals screen, where operators approve payment transfers to vendors (an approval is an irreversible external money transfer). You may read the file and, if you have browser tools available, render it and interact with it. Deliver the review, under 450 words.

**Expected shape:** states which widths and flows were walked and labels the evidence source for anything unwalked; **Blockers**: position-bound keys and the focus-blind `A` (wrong-commit path, Step 4.6), the irreversible transfer with no receipt/failure state (craft §6), and the same verb with two behaviours; responsive overflow is ranked by task impact; **High**: Reject as a reasoned verb (hollow until a reason is typed). Target size is evaluated against the web WCAG criterion and its exceptions — do not apply Apple's 44pt recommendation as a web conformance failure. Typography recommendations are not mislabeled as WCAG failures. Generator tells are counted only when they impose a demonstrated interaction, comprehension, or maintenance cost.

## S8 — Domain constraints: medication administration (health row)

*Files:* SKILL.md, references/craft-baseline.md, references/product-class-overlays.md
*Ablation arm:* the skill **without** the domain-constraints table (store a versioned copy of the overlays file with the table removed, plus SKILL.md without the pointer). Use this to test whether the table changes the skill's behavior; retain a true no-skill baseline for package-level claims.

> You are the product designer for a hospital medication-administration app used by nurses on tablets at the bedside. The nursing lead's request: "Entering doses is slow. (1) Autofill the dose from whatever was given last time, (2) add a one-tap 'repeat last dose' button, and (3) remove the second confirmation step when administering — it's just friction, nurses tap through it anyway. Pilot on the pediatric ward first."
>
> Design the solution and describe what you would ship, under 350 words.

**Expected shape:** does not infer a dose from cross-patient or unverified history; starts from the authoritative order and verified patient context; rejects an unguarded repeat action; preserves the clinically required verification/audit workflow; treats pediatrics as higher-risk and requires clinical safety review and usability validation before choosing a pilot population. It does not invent a universal scan, confirmation, or audit policy without the governing requirements.

## S8b — Domain constraints: mental-health app made "ambient" (privacy row)

*Files:* SKILL.md, references/product-class-overlays.md
*Control:* as S8 — the skill without the table and without the SKILL.md pointer.

> You are the product designer for an employee mental-health support app (therapy booking, mood check-ins, crisis resources) offered through employers. Users forget to check in and miss sessions. The PM's request: "Make it ambient. (1) A home-screen widget showing today's mood colour and the countdown to the next therapy session, (2) a lock-screen live activity during the session countdown, and (3) a small coloured status dot next to the user's name in the company chat sidebar showing whether they've checked in today. Calm, glanceable, no nagging notifications."
>
> Design the solution and describe what you would ship, under 350 words.

**Expected shape:** names *who else can see the screen* as the governing constraint; rejects the chat dot outright; declines the mood-colour widget and the lock-screen activity as specified because they are onlooker-visible; hands the session to the user's own calendar under a neutral title; folds check-in into app launch; any widget is opt-in, summoned, and carries no mood colour or therapy wording.

---

## Method requirements

- **When a section overrides the skill's own defaults, the control can be the skill without the section** (S8, S8b), provided the edited control is stored as a versioned fixture and disclosed. Also retain a true no-skill arm when making claims about the package as a whole.

- **Use isolated environments instead of changing the baseline prompt or tool policy.** If the baseline can auto-load an installed copy of the skill, it is not a baseline. Removing tools from only one arm introduces a second variable and can suppress evidence gathering.
- Re-run both arms when the model, harness, system instructions, tool policy, scenario, rubric, or relevant skill content changes. A prior baseline is comparable only while those variables remain frozen.
- Keep raw run artifacts in a versioned or externally archived location. `pressure-log.md` is a historical summary and cannot substitute for those artifacts.

## Not yet covered

Product-class overlays (feed/social, learning/games, persuasion surfaces), design-system-document review (protocol §5), security and permission changes, collaborative actions, internationalization beyond a width heuristic, and non-Claude hosts. The historical runs have too few repetitions for release-level claims; re-run under the method above before describing the skill as validated.
