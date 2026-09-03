# Foundations of interaction design — the canon behind the skill

Each entry: the idea, why it argues for less interface, and the source. Read the section you need; don't read it all.

Contents
1. Hutchins, Hollan & Norman — Direct manipulation and the two gulfs (1985/86)
2. Norman — The Design of Everyday Things: principles and the seven stages (1988/2013)
3. Verplank — Interaction Design Sketchbook: Do / Feel / Know (2009)
4. Raskin — The Humane Interface: modes, monotony, habituation (2000)
5. Cooper — About Face: goal-directed design and excise (1995–2014)
6. Saffer — Microinteractions: trigger, rules, feedback, loops & modes (2013)
7. Nielsen — Progressive disclosure (1995→) and heuristics
8. Victor — Magic Ink: interactivity as last resort (2006)
9. Weiser & Brown — Calm technology: center and periphery (1995/96)
10. Krishna — The Best Interface Is No Interface (2015)
11. Shneiderman — Direct manipulation and the golden rules
12. Herigstad — Spatial context, motion as feedback, designing by distance (1994–2014)
13. Quantitative laws worth remembering

---

## 1. Hutchins, Hollan & Norman — Direct Manipulation Interfaces (1985)

*Human-Computer Interaction* 1(4), 311–338. Republished in Norman & Draper (eds.), *User Centered System Design*, 1986.
PDF: https://vis.csail.mit.edu/classes/6.859/readings/pdfs/Hutchins-DirectManipulationInterfaces.pdf
NN/g summary: https://www.nngroup.com/articles/two-ux-gulfs-evaluation-execution/

The paper that gives us the vocabulary. Two gulfs separate the person from the system:

- **Gulf of execution** — from the user's goals to the system state. Bridged by making the actions the system offers match what the user intends.
- **Gulf of evaluation** — from the system state back to the user's goals. Bridged by output the user can read as an answer to "did it work?"

Each gulf has two kinds of distance:

- **Semantic distance** — does the interface's vocabulary match the user's intentions? Large when the user must translate "find the invoice" into a chain of filter commands.
- **Articulatory distance** — does the *form* of the input/output resemble its meaning? Small when moving a slider moves the thing; large when typing `sort -k3 -r`.

Two sources of the feeling of "directness":
- **Distance reduction** — fewer cognitive resources needed to span the gulfs.
- **Direct engagement** — the user feels they act on the objects of interest themselves, under a *model-world* metaphor, rather than talking to an intermediary under a *conversation* metaphor.

Why it argues for less interface: every new control is a new expression in the interface language. Adding controls increases semantic distance unless the control maps directly to a user intention. The cure for a wide gulf is usually a better mapping or better feedback on the existing object, not another intermediary. Note the modern echo: Subramonyam et al. (2024) add a **gulf of envisioning** for LLM systems — users struggle to form intentions when the system is non-deterministic — which is why AI products must set expectations (see ai-agent-interaction.md).

## 2. Norman — The Design of Everyday Things (1988; revised 2013)

Norman turned the gulfs into a design vocabulary. The seven stages of action (goal → plan → specify → perform → perceive → interpret → compare) produce seven principles:

- **Discoverability** — can the user tell what actions are possible and what state the system is in?
- **Feedback** — immediate, informative, proportional information about what happened.
- **Conceptual model** — a simple, correct story about how it works, learned from the design itself.
- **Affordances** — what the object actually allows (a relationship, not a property).
- **Signifiers** — the perceivable marks that communicate where to act. Most "add a label/tooltip/badge" requests are signifier patches for a bad affordance.
- **Mappings** — the relationship between controls and effects. Natural/spatial mappings need no labels.
- **Constraints** — physical, semantic, cultural, logical limits that prevent error. Constraints beat warnings.

Why it argues for less interface: if the affordance, mapping, and feedback are right, discoverability follows and signifiers become nearly unnecessary. Explanatory UI is what you add when one of these is wrong.

## 3. Verplank — Interaction Design Sketchbook (2009)

Bill Verplank (Xerox PARC, Stanford, co-designer of the Xerox Star UI).
PDF: https://ccrma.stanford.edu/courses/250a-fall-2004/IDSketchbok.pdf

"Interaction design is design for human use." The designer answers three questions:

- **How do you DO?** The affordance the person acts on. Key choice: **button vs handle**. A button is discrete and symbolic — press it and the machine takes over; sequences of presses. A handle is continuous and analogic — the person keeps control in space and time; a sequence becomes a gesture.
- **How do you FEEL?** The feedback the machine returns; the sensory quality of the response.
- **How do you KNOW?** The conceptual model. Two kinds: **path** knowledge (a novice needs a path — one step at a time) and **map** knowledge (a learner needs a map — an overview to navigate from).

"The greater the distance from input to output, the more difficult and varied the possible conceptual models; the longer the delay between doing and feeling, the more dependent I am on having good knowledge." — this is the mechanism by which slow or displaced feedback forces explanatory UI into existence.

"Good interactions are the appropriate styles of doing, feeling and knowing plus the freedom to move from one to the other."

Design produces **displays and controls and the behaviors that connect them (mappings)**, organized by a conceptual model (**modes**). Verplank also frames interaction as a *sketching* discipline: alternatives matter; if an idea is criticized before it is expressed it dies prematurely.

## 4. Raskin — The Humane Interface (2000)

Jef Raskin (Macintosh project originator, Canon Cat).
Overview: https://en.wikipedia.org/wiki/The_Humane_Interface

- **Modes.** A mode is a state in which the same input produces a different output. Modes cause errors because of **habituation**: after enough repetitions an action becomes automatic and the user stops checking state. Caps Lock is the canonical example. Raskin's remedy: eliminate modes, or use **quasimodes** — states maintained only by a continuous physical action (Shift held down), which the user cannot forget they are in. Visual feedback alone does *not* fix modes (Aza Raskin, "Is visual feedback enough? Why modes kill").
- **Monotony.** There should be one way to do each thing, so habits form without competition. Multiple paths "for discoverability" sabotage habit formation.
- **Habit formation is the goal.** Whitehead, quoted by Raskin: "Civilization advances by extending the number of important operations which we can perform without thinking about them." Design for the operation you do without thinking.
- **Beginner–expert dichotomy is a myth.** "We're humans first, beginners or experts second" (Nass). Accommodate universal human frailties; don't build separate interfaces for imagined skill tiers.
- **Quantification.** Raskin uses GOMS/keystroke-level models and information-theoretic efficiency to measure interfaces: how much of the user's input is actually necessary information vs overhead. Most interfaces are far below 100% efficient — the overhead is interface.
- Raskin's "first law" (paraphrasing Asimov): a computer shall not harm your work or, through inaction, allow your work to come to harm. Autosave and undo are ethical requirements, not features.

## 5. Cooper — About Face (1995, 4th ed. 2014) and goal-directed design

Alan Cooper, Robert Reimann, David Cronin.
Principle list: https://www.gregbulla.com/TechStuff/Docs/NotesFromAboutFace3.htm

Design principles that directly enforce minimal interface:

- "No matter how cool your interface is, less of it would be better." Users prefer no interface; the UI is an artifact, not the goal.
- **Goals vs tasks.** Design for the user's end state, not the steps. Tasks are how; goals are why. Optimising tasks adds steps; optimising goals removes them.
- **Excise.** Work the software demands that does not advance the goal (logins, confirmations, configuration, navigation). "Eliminate excise wherever possible."
- "Design for the probable; provide for the possible." Optimise the mainline flow; make the rare case reachable but not present.
- "Provide choices; don't ask questions." "Ask for forgiveness, not permission." "Don't make users ask for permission." Act, then let them correct.
- "Don't use dialogs to report normalcy." "Avoid unnecessary reporting." "Provide modeless feedback."
- "Differentiate between command and configuration." Settings are a different, rarer place than actions.
- "Hide the ejector seat levers." Dangerous or irreversible controls are hidden, not confirmed.
- "Enable users to direct, don't force them to discuss." Direct manipulation over dialog.
- "Optimize for intermediates." Nobody wants to remain a beginner; onboarding UI ("training wheels") should not be welded on.
- "Follow users' mental models," not the implementation model. A UI that mirrors the code's structure exposes machinery the user must then learn.
- "Don't stop the proceedings with idiocy." No modal interruptions for things the system could handle.
- **Flow / transparency.** Well-orchestrated interfaces are transparent; the designer must "hear sour notes in the orchestration."

## 6. Saffer — Microinteractions: Designing with Details (2013)

Dan Saffer (Smart Design, Flipboard).
Overview: https://smartdesignworldwide.com/ideas/microinteractions-details-matter/

A microinteraction is a contained product moment that does one small task. Its anatomy is the practical unit for specifying interactions:

- **Trigger** — what starts it. *Manual* (user acts) or *system* (conditions met). Design questions: is it discoverable by the right person at the right moment; does it look like what it does; does it follow existing conventions?
- **Rules** — what happens once triggered; the constraints; the sequence. Rules should be simple enough to be learned from feedback alone.
- **Feedback** — how the user learns the rules. Visual, audio, haptic. Minimum signal that confirms the action; "don't overload with feedback." **Foghorn test**: if the user would need to know this even without looking at the screen, it earns loud/prominent feedback; if not, keep it subtle.
- **Loops & modes** — what happens over time; does it repeat; does the product enter a special state. Modes are to be avoided or made explicit.

Two guidelines from the book that map to ladder rungs 1–2: **"Bring the data forward"** (show relevant information in the trigger itself) and **"Don't start from zero"** (use history and context to prefill).

"The difference between a product you love and a product you tolerate is often the microinteractions you have with it." Signature moments are microinteractions elevated to brand.

## 7. Nielsen — Progressive disclosure and heuristics

NN/g: https://www.nngroup.com/articles/progressive-disclosure/

Introduced 1995. Users want power *and* simplicity. Resolve it by showing the few most important options initially and offering the specialised set only on request. Two variants:

- **Progressive disclosure** — secondary options revealed on demand, in place. Rarely offer multiple ways to reach the secondary set.
- **Staged disclosure** — a linear sequence with a subset at each step (wizards). Works only when steps have little interdependence; harmful when users must alternate between steps.

Related heuristic (#8 of Nielsen's ten): **aesthetic and minimalist design** — every extra unit of information competes with the relevant units and diminishes their visibility.

Nielsen's **noncommand systems** (1993): the computer acts as a side effect of the user's normal actions (pull the car handle and it unlocks — the user would do the same thing locked or unlocked). This is rung 1–3 in its purest form.

## 8. Victor — Magic Ink: Information Software and the Graphical Interface (2006)

Bret Victor. https://worrydream.com/MagicInk/

For **information software** (software whose purpose is to answer a question — most software), the user is not "using" a tool; they are learning something. Interaction is therefore a cost:

- "Interactivity is actually a curse for users and a crutch for designers." Every interactive element is a place where the designer refused to figure out what the user wanted.
- **Three approaches to context-sensitivity, in order of preference:**
  1. **Infer from the environment** — clock, location, device, what's already on screen.
  2. **Infer from history** — what the user did before, what they last looked at, patterns over time ("engineering inference from history").
  3. **Interaction** — the user can suggest what's relevant, but *only as a last resort*.
- "Interaction is a bottleneck." Humans read graphics far faster than they manipulate controls; **information graphic design** (show the data, arrange the data) does most of the work.
- Case studies: a train schedule or airline site redesigned so the answer is visible without a form; a map whose predictions are annotated rather than searched.
- **Mad-lib sentences with editable values** — when input is unavoidable, embed it in the information itself instead of a separate form.

Why it matters for AI agents: an LLM is an inference engine. Using it to *ask more questions* inverts its value. Use it to infer from environment and history, and to show the answer.

## 9. Weiser & Brown — Designing Calm Technology (1995); The Coming Age of Calm Technology (1996)

Xerox PARC. https://calmtech.com/papers/coming-age-calm-technology

Calm technology "informs but doesn't demand our focus or attention." It engages both the **center** and the **periphery** of attention and moves between them:

- The **periphery** is "what we are attuned to without attending to explicitly." It is not unimportant — it is where most awareness lives (the engine noise you notice only when it changes).
- Calm design puts information in the periphery, lets it move to the center when it matters, and back out again. "Enhanced peripheral reach increases our knowledge and so our ability to act without increasing information overload."
- Examples: the Dangling String (network load as a moving string), inner office windows (awareness of the hallway).
- Three principles (as usually stated): attention resides mainly in the periphery; the technology increases the user's use of the periphery; it conveys familiarity and locatedness.

Why it argues for less interface: badges, toasts, banners, and modals are center-of-attention devices. Most status belongs in the periphery. A design that puts everything at the center is not "informative"; it is noise that trains users to ignore all of it.

## 10. Krishna — The Best Interface Is No Interface (2015)

Golden Krishna (Cooper, Samsung, Zappos Labs, later Google).

Three principles for thinking beyond screens:

1. **Embrace typical processes instead of screens.** Start from what the person already does, not from a rectangle. Map the natural process and see where technology can dissolve into it.
2. **Leverage computers instead of serving them.** Computers sense, remember, compute, and act. Making the human do those things (data entry, configuration, confirmation) is serving the computer.
3. **Adapt to individuals.** Systems that learn and adjust remove the need for settings and choices.

Four aims: the best design reduces work; the best computer is unseen; the best interaction is natural; the best interface is no interface. Also: "Overload, clutter, and confusion are not attributes of information, they are failures of design."

## 11. Shneiderman — Direct manipulation (1983) and the Eight Golden Rules

Direct manipulation: continuous representation of the objects of interest; physical actions instead of complex syntax; rapid, incremental, reversible operations whose effect is immediately visible. This is the interaction style that makes rung 4 possible.

Golden rules most relevant here: strive for consistency; enable frequent users to use shortcuts (habit); offer informative feedback; design dialogs to yield closure; permit easy reversal of actions; support internal locus of control; reduce short-term memory load.

## 12. Herigstad — Spatial context, motion as feedback, designing by distance

Dale Herigstad (broadcast motion designer; founder of Schematic → POSSIBLE; four Emmys; part of the *Minority Report* gestural-UI research team — John Underkoffler is the primary credited designer of that film's UI; co-founder of Seespace/InAiR, 2014).
Keynote notes (Raph Koster, 2006): https://www.raphkoster.com/2006/02/20/living-game-worlds-2006-dale-herigstads-keynote/
InAiR: https://www.kickstarter.com/projects/2128859975/inair-the-worlds-1st-augmented-television

A practitioner, not a theorist, and *not* a minimalist: his instinct is rich, layered, moving, branded media ("the interface is the brand"). Borrow his structure, not his aesthetic. Four things transfer:

- **Fixed spatial semantics.** Schematic designed in wireframes and *top views* of the UI, not sitemaps, and "defined the meaning of directions, so that up always consistently means the same thing." This is Norman's mapping applied to space: once the axes mean something, labels, breadcrumbs, and back buttons become unnecessary. For any navigable product, decide what each axis means once and never overload it.
- **Motion planned as a UI element from the beginning**, not decoration added at the end. Motion is the cheapest way to close the gulf of evaluation — it shows where something came from and where it went, so the user does not need a badge or a message telling them. Specify the motion in the interaction spec (Feel), and "sketch the motion quickly" during design.
- **Design by viewing distance and attention state, not by device.** TV is a 10-foot, friends-and-family experience; phone and handheld are one foot; laptop two feet; public screens 25 and 200 feet. Smaller devices are for "snacking." Distance determines how much can be on screen, how big the targets are, and what belongs in the periphery. Ask "how far away is the person and how much attention do they have?" before "what platform?"
- **The TV mindset.** "The TV mindset is not one of high amounts of interaction. MTV… found that people weren't actually creating playlists, they were picking prepackaged playlists even though they had the ability to make their own… an audience that doesn't want to work at it." Evidence that offered interaction goes unused; defaults and curation beat controls. He also names the **"wall of the new"** — automatic rejection of the unfamiliar — as the main obstacle in user testing, which is why a new interaction must reuse existing vocabulary (consistency, Step 4).

InAiR as a ladder example: it identifies what is on screen and pulls related content automatically (rung 1, infer from environment), places it in layers in z-space *in front of* the program as non-disruptive augmentation (periphery/center, calm), and lets the viewer pull a layer forward or dismiss it with a gesture (efficient invocation and dismissal). The lesson is the pattern — infer, layer, don't interrupt — not the 3D TV.

## 13. Quantitative laws worth remembering

- **Hick's law** — decision time grows with the log of the number of choices. Every added option slows every decision on that screen.
- **Fitts's law** — time to acquire a target depends on distance and size. Actions on the object itself (rung 4) are faster than actions in a toolbar.
- **Miller / working memory** — a small number of chunks at a time. Interfaces that require holding state across screens (wizards, modes) exceed it.
- **Keystroke-level model (Card, Moran, Newell; used by Raskin)** — count keystrokes, pointing, homing, and mental preparation. Interface overhead is measurable; measure it.
