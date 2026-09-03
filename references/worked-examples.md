# Worked examples — request → element-first response → interaction-first response

Read when you want to see the ladder applied to a concrete request, or to calibrate a review against a known-good answer. Each example names the rung chosen and the net element count.

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

**"Users keep accidentally deleting tasks — add a confirmation dialog."** (from the pressure suite)
Element-first: `alertdialog` with Cancel / Delete.
Interaction-first (rung 3, craft §6): soft-delete; row leaves immediately; peripheral "Task deleted · Undo" that persists long enough to use and restores position; rapid deletes coalesce; server rejection returns the row in place with the retry path. Confirmation stays reserved for effects undo cannot reach. Elements added: one transient. Removed: the modal, permanently.

**"Brand refresh: restyle the cards in brand purple and add an 'urgent' flag icon on near-deadline cards."** (from the pressure suite)
Element-first: purple card backgrounds + a flag glyph.
Interaction-first (rung 5.5): urgency is the heat channel — the card tint warms as a continuous function of time remaining, deadline text darkens as its non-colour twin; purple goes on the committable verb and focus ring only, never on state-carrying surfaces. Elements added: none. Restyle net zero; declined element logged in the ledger with its reasoning.
