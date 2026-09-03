# Element ledger — OpsQueue

<!-- Test fixture for scenario S4. Copy to <project>/design/LEDGER.md before running; the agent must append a Round 3 without altering Rounds 1–2 or the correction. -->

## Round 1 (2026-08-12)
NEW ELEMENT: approve verb (filled button on queue card)
Closes gulf: execution
Why rungs 0–5.5 fail: commit requires explicit user gesture; irreversible external transfer
Replaces / removes: approval modal (removed)
Who sees it, when: operators, on every actionable card
Cost: attention, layout
Exit criteria: none — core verb

REMOVED: approval confirmation modal (−1)
REMOVED: status badge per card — state moved to luminance channel (−1)

Net round 1: −1

## Round 2 (2026-08-20)
NEW ELEMENT: peripheral saved tick
Closes gulf: evaluation
Why rungs 0–5.5 fail: commit needs a receipt; periphery chosen over toast
Replaces / removes: success toast (removed)
Who sees it, when: operator who just committed, fades in 2s
Cost: attention (minimal)
Exit criteria: remove if commit latency ever < 100ms perceived

CORRECTION: round 1 counted the card tint as +1 — wrong, tint is a property (0). Net round 1 restated: −2.

Net round 2: 0 (net to date: −2)
