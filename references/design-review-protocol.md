# Design review protocol — auditing design work across rounds

How to review screens, prototypes, and design systems — your own or a design agent's — so that discipline survives iteration. Distilled from multi-round agent-driven design practice. Use alongside SKILL.md's ladder and ledger; this file covers what happens *between* rounds.

Contents
1. Render and walk — never review from the notes
2. The craft pass
3. The regression watchlist
4. Reviewing a design system document
5. Self-limiting system rules
6. Working with a design agent: comply-or-argue
7. Review output format
8. Convergence: when to stop designing

---

## 1. Render and walk — never review from the notes

A design agent's notes describe intent; only the render shows what shipped. Every review begins by rendering the actual artifact and walking it as the target user:

- Load prototypes headless (Playwright: `file://` URL, wait ~3.5–5s for JS init, screenshot per frame/section; for interactive builds, click through every navigation destination and every primary flow, capturing before/during/after of each state change).
- Inspect at native scale. Thumbnails hide contrast failures, tint strength, and type below the floor; crop and zoom the regions that matter (the primary card, the panel, the smallest text).
- Walk the flows, don't just view the screens: open the object from *every* surface it appears on (queue, zoomed list, palette, chat card) and verify the same interaction results; fire the exception path; commit and check what the screen does afterwards.
- Compare claims to pixels. If the notes say "auto-collapses on entry" or "net −1 per row," verify by walking; the most dangerous gap is a well-written note describing behaviour that isn't built.
- Check ordered fixes from prior rounds one by one. Items silently dropped ("was ordered cut, still present") get listed by name; agents reliably apply the interesting fixes and shed the housekeeping.
- Walk the responsive tiers — **375 / 768 / 1024 / 1440 / 1920** — and screenshot each. Horizontal scroll, clipped or overlapping content, and navigation that collapses by accident rather than design are findings at the tier where they appear.
- Stress the render: paste a very long string into every text container, load the empty case, and (for anything async) watch the loading state on a slow connection. A layout that only survives the demo data hasn't been reviewed.
- Read the console on every walked flow. Errors, failed requests, and 404 assets are evidence and often explain a visual defect you already screenshotted.
- **No finding without something the walk showed.** If the artifact could not be rendered, say so plainly and mark every remaining observation as heuristic (from reading code or notes) — never present an unrendered judgement as an observed one.

## 2. The craft pass

After the walk, run `craft-baseline.md` over the elements that survive the ladder/ledger audit: contrast at the strongest tint, keyboard and focus order, touch-target sizes, type resilience, the responsive tiers above, confirm-vs-undo, motion, layout stability. Every check there carries a number, so every craft finding is measurable, not a taste call.

Scope discipline: the craft pass judges **quality of existing elements only**. If a craft check appears to demand a new element ("this needs a tooltip / badge / empty-state block"), it is not a craft finding — write it up as a ladder question (which rung actually closes this gulf?) and say so in the report. A review that scores points by adding elements has inverted the skill.

## 3. The regression watchlist

Discipline decays in predictable ways. Check for each by name, every round:

- **Decoration creep.** Icons, glyphs, chips, plates, and hint lines arrive undeclared, usually during restyles or platform-layer work. Any element not in the ledger is either removed or declared — "small" is not a category.
- **Banned patterns returning under new names.** A deleted bell comes back as "Notifications"; a deleted badge count comes back as a nav counter; a deleted confirmation comes back as an "are you sure" panel. Audit *functions*, not names: does anything re-create a checking loop, a second commit path, an interruption channel?
- **Chrome grows fastest at the shell.** Discipline won at the feature level leaks at the platform level (sidebars, global nav, counters), where every addition is multiplied across all future modules. The shell is a frame; it carries a ledger like any frame.
- **Buyer copy on operator screens.** Prose explaining the product's philosophy or roadmap ("the first of several… workflows mount here") belongs in the pitch deck. If a sentence addresses someone who is not the screen's user, cut it.
- **Two sentences for one object.** The same verb or object described differently in collapsed vs expanded vs remote surfaces. One object, one sentence.
- **Fixture drift.** Personas, names, IDs, and sample data silently changing between rounds. Fixtures are test data pinned to a source of truth; renames are diffs to reject.
- **The page replacement.** Under complexity pressure, panels regress to full-page views with back-links, and the object's verb disappears in the new view. Re-verify the panel rule and verb sovereignty on every new surface.
- **The armed look that isn't armed.** A filled/primary-styled control that doesn't commit in one gesture in *this* context (but does elsewhere) is a mode. Same look = same behaviour, every surface.
- **Meaning drift between channels.** A colour reserved for one channel (e.g. urgency) reused for links, branding, or focus. Each colour family belongs to one channel; check new elements against the channel map.

## 4. Reviewing a design system document

A design system is reviewed as an *operating constitution*, not a style sheet:

- Every rule must state a **meaning** ("glow = attention") plus a **never** ("never focus, never hover, never two at once"). A rule without a never is a preference and will be renegotiated.
- Hunt **internal contradictions**: a token contradicting a judgement call recorded earlier in the same document; a motion section banning loops while the loading section specs a shimmer. Documents written across rounds accumulate these.
- Hunt **wrong-commit paths** as P0: any key or gesture that can act on something other than what the user is looking at (e.g. a global commit key bound to a highlighted object while focus is elsewhere); any list that re-sorts under the user's hands; any commit whose failure has no defined state (a "no toasts" rule without a failed-commit rule = silent failure).
- Check **the failure path exists** for every irreversible action: what the user sees when the backend rejects the commit, when the network drops, when permission is denied. "The success animation is the receipt" requires "the receipt waits for acknowledgement."
- Check **density and scale limits** have answers, not just bans ("no compact mode" must be accompanied by what a 10× queue does).
- Check **claims against arithmetic**: contrast ratios at the strongest tint (measure at the tinted edge, not the white centre), type sizes against the declared floor, expansion room for the second language (Vietnamese ≈ +15–25% and taller diacritics).
- Check **platform/module boundaries**: the system defines what an extension may add (vocabulary: verbs, fields, labels, translations, layouts within its own surface) and what it may never add (channels, tiers, tokens, primitives, motions, keystrokes, commit controls, exemptions). A module needing a new primitive is a platform change request, argued centrally, with something retired in exchange.
- Check **document governance**: the system files as an edit/version of the canonical design doc, not a new parallel document; superseded material is archived, not left ambient.

## 5. Self-limiting system rules

The strongest systems constrain their own future. Look for (and add, if missing):

- **Banned list and retired list**, with "do not reintroduce" — the retired list is the memory that stops patterns returning under new names.
- **Exemption budget**: no new exemption without retiring one. Exemptions are where systems rot.
- **"A number rendered because it was available" is banned** — data must earn rendering by serving a decision.
- **One meaning per channel, one channel per meaning** — and any surface may redefine at most one declared channel (e.g. a module's layout redefines what position means on its own canvas) while all others keep their platform meaning.
- **Additions retire something.** Platform-level additions in particular: the shell only grows by exchange.

## 6. Working with a design agent: comply-or-argue

The best agent rounds are not the most obedient ones. Set the expectation explicitly, and review for it:

- **Never silent deviation, never silent compliance.** If the agent believes a spec value is wrong (an alpha too low to see, a rule that starves an element of function), it says so, ships its recommendation *and* the spec'd version side by side, and lets the human pick. Deviating without saying so is a failed round even if the deviation is right.
- **Judgement calls are filed in writing**: what was decided, why, what it trades away — plus an *open questions* list of things the agent noticed but didn't decide. Review these first; they're where the thinking is.
- **Corrections are logged, not buried.** When the agent (or reviewer) discovers a prior round was mis-counted or mis-ruled, the correction appears in the ledger/notes explicitly.
- **The reviewer can be wrong.** When the agent's argument beats the instruction (e.g. a motion rule that violates "nothing moves unless the world changed"), the review says so and the doctrine updates. Ratify good unsolicited changes explicitly — an unratified improvement is a landmine for the next round.
- **Ratify or reject every structural change, by name.** Silent structural changes that survive a round become de-facto doctrine without ever being argued.

## 7. Review output format

Lead with the verdict, in one sentence: **Ship / Ship with fixes / Needs work**, plus whether the round converged or drifted, and which viewports were walked. Then:

1. **Ratify** — good changes (asked-for or not), named explicitly so they enter doctrine.
2. **Violations / regressions** — each written as *observation → rule broken (by name) → fix*, with the evidence (screenshot, measured value, console line — what the walk showed, not what the notes said). Rank in four tiers: **Blocker** (wrong-commit paths, doctrine breaks, craft-baseline accessibility failures — gates shipping), **High** (fix before merge), **Medium** (noticeably better if fixed), **Nit** (prefixed "Nit:", never gates anything). Distinguish "broken" from "I'd prefer" — only Blockers and Highs gate.
3. **Decisions for the human** — genuine trade-offs (axis purity vs control constancy, etc.) stated as a choice with a recommendation, not silently resolved.
4. **The fix block** — a numbered, copy-paste instruction for the next round: fixes first, then new work, then what to deliver as proof. Keep ordered items checkable; next round begins by checking them.
5. **Net element count** for the round.

The biggest removal leads; never a laundry list with the lede buried.

## 8. Convergence: when to stop designing

Watch net element delta per round and the ratio of new-structure to polish. The design has converged when a round completes remaining interactions while adding essentially nothing, and fixes are cosmetic. At that point:

- Freeze as a version of the canonical design doc (edit, not new document).
- The frame notes / interaction specs *are* the acceptance criteria — hand them to implementation with minimal rewriting, and audit implementation against the specs' behavioural sentences ("the verb is the progress bar"), not pixel measurements.
- Ship the remaining open items as ticket zero rather than another design round.
- After the freeze, restyles and motion passes still carry ledgers; convergence is a state to defend, not a finish line.
