# Human–AI interaction research, mapped to reducing interface

Read this when designing any product where a model infers intent, generates content, or takes actions on the user's behalf. The sources are the validated guideline sets; the mapping to "less interface" is this skill's synthesis.

Contents
1. Horvitz — Principles of Mixed-Initiative User Interfaces (CHI 1999)
2. Amershi et al. — Guidelines for Human-AI Interaction (CHI 2019), full 18
3. Google PAIR — People + AI Guidebook (2019→)
4. Nielsen — AI as the third UI paradigm (2023)
5. Decision procedure for every agent action point
6. Control surface: the minimum set

---

## 1. Horvitz — Principles of Mixed-Initiative User Interfaces (CHI 1999)

Eric Horvitz, Microsoft Research. https://interruptions.net/literature/Horvitz-CHI99-p159-horvitz.pdf

Context: a debate between "interface agents" (automation) and "direct manipulation" (Shneiderman, Maes). Horvitz's answer is an *elegant coupling* of the two, governed by expected utility. Key problems with agents: poor guessing about goals, ignoring the cost/benefit of automated action, poor timing, and no way for the user to guide invocation or refine results.

The twelve principles:

1. **Developing significant value-added automation** — genuine value over what direct manipulation already gives.
2. **Considering uncertainty about a user's goals** — model it explicitly; don't pretend to know.
3. **Considering the status of a user's attention in the timing of services** — defer action to when it will be less distracting.
4. **Inferring ideal action in light of costs, benefits, and uncertainties** — act when the expected value of acting beats inaction.
5. **Employing dialog to resolve key uncertainties** — and weigh "the costs of potentially bothering a user needlessly."
6. **Allowing efficient direct invocation and termination** — the user can always start or stop the service.
7. **Minimizing the cost of poor guesses about action and timing** — timeouts, natural gestures for rejecting service.
8. **Scoping precision of service to match uncertainty** — "A preference for 'doing less' but doing it correctly under uncertainty can provide users with a valuable advance towards a solution and minimize the need for costly undoing or backtracking."
9. **Providing mechanisms for efficient agent–user collaboration to refine results** — assume the user will complete or refine.
10. **Employing socially appropriate behaviors** — the sensibility of "an intuitive, courteous butler" who notices when you're busy and gets out of the way.
11. **Maintaining working memory of recent interactions** — so users can refer to shared short-term context.
12. **Continuing to learn by observing.**

The decision model: for each possible action, compare expected utility of **acting**, **asking (dialog)**, and **doing nothing**. Two thresholds fall out: below p*₁ do nothing; between p*₁ and p*₂ ask; above p*₂ act. Thresholds shift with context — the cost of an unwanted action rises when the user is deep in another task and falls when the action is easily reversible or screen space is plentiful.

Lookout (the testbed): reads an email, infers whether the user wants to schedule. High confidence → opens a pre-filled appointment. Low confidence → opens the *right week* of the calendar rather than guessing a time — the user finishes with one direct-manipulation step. Very low → does nothing; a tray icon lets the user invoke manually. "Even when Lookout guesses incorrectly, the user is placed in an approximately correct position." If it asks and the user ignores it, it waits proportionally to its confidence, then "makes a respectful, apologetic gesture and evaporates."

**Interface implication:** the act/ask/wait model replaces approval dialogs, confidence badges, and plan viewers with one mechanism: scope the action to the confidence, show the result in place, make refinement direct.

## 2. Amershi et al. — Guidelines for Human-AI Interaction (CHI 2019)

Saleema Amershi, Dan Weld, Mihaela Vorvoreanu, Adam Fourney, Besmira Nushi, Penny Collisson, Jina Suh, Shamsi Iqbal, Paul Bennett, Kori Inkpen, Jaime Teevan, Ruth Kikin-Gil, Eric Horvitz. Microsoft. CHI 2019 Honorable Mention.
PDF: https://www.microsoft.com/en-us/research/wp-content/uploads/2019/01/Guidelines-for-Human-AI-Interaction-camera-ready.pdf

Synthesised from 168 recommendations across 20 years; validated by 49 practitioners against 20 products; 8 of the 18 map to Horvitz 1999. Each guideline is a verb phrase with no conjunctions so it can be checked as applied/violated in an interface.

**Initially**
- **G1 Make clear what the system can do.** Help the user understand what the AI system is capable of doing.
- **G2 Make clear how well the system can do what it can do.** Help the user understand how often it may make mistakes. (Example application: hedging language — "we think you'll like".)

**During interaction**
- **G3 Time services based on context.** Time when to act or interrupt based on the user's current task and environment.
- **G4 Show contextually relevant information.** Display information relevant to the user's current task and environment.
- **G5 Match relevant social norms.**
- **G6 Mitigate social biases.**

**When wrong**
- **G7 Support efficient invocation.** Make it easy to invoke or request the AI's services when needed.
- **G8 Support efficient dismissal.** Make it easy to dismiss or ignore undesired services. (Example: "unobtrusive, below the fold, easy to scroll past.")
- **G9 Support efficient correction.** Make it easy to edit, refine, or recover when the AI is wrong. (Example: drag the pin to fix the parked-car location; one click to revert a spelling correction.)
- **G10 Scope services when in doubt.** Engage in disambiguation or gracefully degrade when uncertain. (Example: autocomplete offers 3–4 suggestions instead of completing for you.)
- **G11 Make clear why the system did what it did.** Enable the user to *access* an explanation. (Most-violated guideline in the study; also the one where explanations were often present but inadequate.)

**Over time**
- **G12 Remember recent interactions.** Short-term memory; efficient references to it.
- **G13 Learn from user behavior.** Personalise over time.
- **G14 Update and adapt cautiously.** Limit disruptive changes. (Violation example: browsing one camera after tennis balls and the entire recommendation list flips.)
- **G15 Encourage granular feedback.** During regular interaction.
- **G16 Convey the consequences of user actions.** Immediately show how an action affects future behaviour.
- **G17 Provide global controls.** Customise what the system monitors and how it behaves.
- **G18 Notify users about changes.** When capabilities are added or updated.

Study findings that matter for design: G1, G4, G12 are widely implemented; G2, G11, G17 are relevant but widely violated; G3, G5, G6 are hardest for designers to see from their own vantage point.

**Mapping to less interface**

| Guideline | Element-first reading | Interaction-first reading |
|---|---|---|
| G1–G2 | Persistent "AI" badges, disclaimers on every output | Expectation-setting at first use and in the empty state; hedged wording in the output itself |
| G3 | Toasts, proactive pop-ups | Wait for a natural pause; surface in the periphery |
| G4 | More panels | Fewer, contextual: show only what fits the current object |
| G7 | A prominent "Ask AI" button everywhere | Selection + one keystroke; the trigger is the object |
| G8 | Close buttons on suggestions | Ignoring *is* dismissal; nothing blocks |
| G9 | Regenerate / reject / retry buttons | Edit the result directly; the edit is the correction |
| G10 | Confirmation dialog | Scoped action (do the certain part, position the rest) |
| G11 | "Why?" panel always open | "Why" available on request, near the result |
| G14 | — | Don't re-layout what the user is looking at |
| G15 | Thumbs up/down on every message | The correction is the feedback; explicit rating only where correction is impossible |
| G16 | Explainer toast after every action | One inline note the first time; then silent |
| G17 | Settings page with many toggles | On/off + scope; everything else learned (G13) |

## 3. Google PAIR — People + AI Guidebook (2019→)

https://pair.withgoogle.com/guidebook/

Six chapters: **User needs + defining success; Data collection + evaluation; Mental models; Explainability + trust; Feedback + control; Errors + graceful failure.**

Guidance most relevant to interface restraint:

- *Find the intersection of user needs and AI strengths.* Solve a real problem where AI adds unique value; if a rule or a default solves it, use the rule.
- *Automation vs augmentation.* Automate tasks that are difficult, unpleasant, or need scale and where people agree on the "correct" way; augment tasks people enjoy, that carry social capital, or where there is no agreed correct way. (Automation removes interface; augmentation adds interaction — choose deliberately.)
- *Explain the benefit, not the technology.* *Explain what's important.* *Tie explanations to user actions.* *Note special cases of absent or comprehensive explanation* — not every output needs an explanation.
- *Set expectations for adaptation.* Tell users the system will change with use, once.
- *Feedback: explicit and implicit.* Implicit feedback (what the user does next) is usually enough; design explicit feedback so its consequence is clear and immediate.
- *Control.* Let users take over when they prefer or when the system fails — this is G7–G9 again.
- *Errors and graceful failure.* Design the failure path as carefully as the success path; a scoped fallback beats an error dialog.

## 4. Nielsen — AI: First New UI Paradigm in 60 Years (2023)

https://www.nngroup.com/articles/ai-paradigm/

Three paradigms: **batch processing** (specify the whole workflow up front), **command-based interaction** (issue a command, see the state, issue the next — GUI and CLI both), and now **intent-based outcome specification** — the user states the desired result, not the steps; locus of control reverses.

Two consequences Nielsen draws:

- Rounds of *gradual refinement* ("I don't like the space suits") are the interaction to design and are "currently poorly supported." That is: the refinement loop, not the configuration surface.
- Intent-based UIs are not yet *noncommand* systems (Nielsen 1993), where the computer acts as a side effect of normal user behaviour. Noncommand is the ceiling — the point at which interface disappears.

Nielsen also notes the accessibility cost: intent-based UIs demand articulate users. Inference from context and history (Victor's rungs 1–2) lowers that demand; forms and prompts raise it.

## 5. Decision procedure for every agent action point

Run this at each place the agent could act:

1. **Confidence?** Estimate honestly (model calibration, ambiguity of the request, quality of context).
2. **Cost of being wrong?** Reversible in one gesture = low. Destructive, external side-effect, or expensive to notice = high.
3. **User's attention?** Mid-flow = raise the bar for interruption; idle or waiting = lower it.
4. Choose:
   - High confidence, low cost → **act**, show the result in place, undo available.
   - Medium confidence, low cost → **act on the certain subset**, position the rest for direct completion (Lookout: open the right week).
   - Any confidence, high cost, reversible by design possible → **make it reversible, then act**.
   - Low confidence, high cost, not reversible → **ask with choices** (max one question, inline, dismissible by ignoring; a timeout that evaporates).
   - Low confidence, low value, user busy → **wait**; leave a peripheral affordance for manual invocation.
5. After the user corrects: apply G16 once (show the consequence), G13 (learn), G14 (don't disrupt).

## 6. Control surface: the minimum set

For most AI features, the complete control surface is:

- **Invoke** (G7) — selection, keystroke, or the natural next action on an object. Not a floating button.
- **Dismiss** (G8) — ignore, Esc, or scroll past. Never a modal.
- **Correct** (G9) — edit the output in place. The edit is the feedback (G15) and the learning signal (G13).
- **Undo** — one gesture, always, for anything the agent did.
- **Why** (G11) — on request, near the output.
- **Scope** (G17) — one global control over what the agent may touch; one on/off.

If a design needs more than these six, it is almost certainly compensating for an action that should have been scoped down (G10) or made reversible.
