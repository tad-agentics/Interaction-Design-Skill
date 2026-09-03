# Changelog

## 0.3.1 — 2026-09-03

- Tests are re-runnable from the repo: `tests/scenarios.md` carries the verbatim prompts and expected shapes for every scenario, `tests/fixtures/ledger-opsqueue.md` the S4 fixture.
- Amershi et al. citation gains a DOI alongside the PDF link.
- Scope-by-product-type now points at the precedence section's conversion-surface carve-out instead of restating the boundary.
- Removed the unbacked license claim from `plugin.json` (no LICENSE file yet); marketplace manifest gains a description; `.gitignore` added.
- SKILL.md describes the Amershi guidelines reference accurately (titles with glosses, not full text).

## 0.3.0 — 2026-09-03

- Review protocol: new "Inheriting a UI (redesign rounds)" section — detect preserve vs. overhaul first, the audit becomes ledger round zero, habits are load-bearing, a never-change-silently list (slugs, nav labels, form field names/order, tracked IDs, logo, legal copy, accessibility wins), levers from lowest risk upward.
- Review protocol: "Generator tells" added to the regression watchlist — elements that arrive from the model's priors, checked against the ledger like any addition.
- Workflow Step 1: the one-question rule for the agent's own clarifying questions (one question, with choices, only when reads diverge; otherwise declare the read and proceed).
- Plugin packaging (`.claude-plugin/`) and this changelog.

## 0.2.1 — 2026-09-03

- Craft baseline §6: confirm-vs-undo predicate made observable ("data destroyed with no restore path"; build the restore path instead of the dialog) after pressure tests.
- `tests/pressure-log.md` records the scenario suite and outcomes.

## 0.2.0 — 2026-09-03

- Three-layer precedence: existence (ladder + ledger) → quality (craft baseline) → style, in that order; craft and style can never create an element.
- New `references/craft-baseline.md`: measurable exit criteria from WCAG 2.2 AA, Apple HIG, and Material Design, scoped to elements that survived the ledger.
- Review protocol: viewport tiers, stress and console checks, a scoped craft pass, no-finding-without-evidence, Blocker/High/Medium/Nit severity with a Ship verdict.
- Element ledger persists at `design/LEDGER.md` with read-before-write and never-regenerate rules.

## 0.1.0 — 2026-09-03

- Initial skill: interaction-first stance, the Ladder of Least Interface, the element ledger, channel physics, object–verb sovereignty, AI-agent guidance, and the design review protocol, with foundations and references.
