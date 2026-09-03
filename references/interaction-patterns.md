# Interaction patterns for recurring state and committed actions

Read this only when a product has many stateful objects, recurring operational work, or actions that commit meaningful consequences. These are derivation methods and adaptable patterns—not universal visual assignments.

## 1. Derive a channel map from the product

A visual channel is a property the design can vary, such as position, luminance, hue, shape, fill, size, or motion. Reusing a channel can reduce discrete chrome, but it still costs perception, learning, privacy, accessibility, and implementation effort.

1. List the meanings people must distinguish to complete the task: priority, ownership, status, progress, urgency, category, selection, focus, error, or another product-specific concept.
2. List channels already claimed by the platform, brand, accessibility behavior, and the product. Do not repurpose link color, focus treatment, validation color, or another established semantic token.
3. Map meanings to channels using task fit and evidence. Position may represent chronology, geography, rank, workflow stage, or something else; it does not inherently mean priority.
4. Avoid conflicting meanings within the same context. Redundancy is appropriate when it improves accessibility or recognition; “one channel per meaning” is not a reason to remove a necessary non-color cue.
5. Test whether people can perceive and interpret the mapping across supported themes, viewports, input modes, localization, color-vision differences, reduced-motion preferences, and privacy contexts.
6. Keep the mapping stable while a person is acting. Defer reordering or movement that could change a focused command's target.

### Queue-style example

In a triage queue, evidence may support this map:

- position = current priority;
- luminance or surface treatment = ownership or workflow hierarchy;
- a continuous tint plus a non-color cue = time pressure;
- fill within one stable region = progress;
- brief motion = a completed state transition.

Use this only when those meanings match the product. A calendar will usually reserve position for time; a map for geography; a feed for ranking or chronology. Derive another map rather than forcing the queue example.

Motion should communicate a state transition or spatial relationship, not merely keep the screen visually active. Do not impose an arbitrary global cap such as “one glow per screen”; limit attention signals according to task priority, simultaneous exceptions, platform conventions, and accessibility needs.

## 2. Keep action semantics stable across surfaces

When the same object appears in a list, detail view, notification, command palette, or collaboration surface:

- Keep the action's identity, authority, target, and material consequence consistent.
- Adapt wording to available space, grammar, locale, and context while preserving meaning. Different phrasing is not itself a mode.
- Do not let identical styling imply different consequences. Conversely, do not assume every primary-looking control commits immediately; follow the product's established component semantics.
- Put an action near its object when doing so improves targeting and comprehension, but use a separate review surface when multiple objects, permissions, or consequences must be considered together.
- External or embedded content must not impersonate trusted product controls. Keep trust boundaries visible, prevent untrusted content from creating privileged commits, and restore focus predictably when the surface closes.
- Keyboard commands must act on the focused or otherwise unambiguous object. Never bind a destructive or consequential action to a position that can reorder beneath the person.

## 3. Choose confirmation, review, and recovery from consequence

Do not decide from visual style or nominal reversibility alone. Check:

- Does the person have authority to act?
- Is the target unambiguous?
- Can the product restore the actual prior state, including external effects?
- Will collaborators see or depend on the intermediate result?
- Is a review, authentication, acknowledgement, or audit step required?
- Can failure be detected and recovered from without support intervention?

Use direct action plus undo when all relevant conditions support it. Otherwise use the smallest preview, review, confirmation, authentication, or scoped-action mechanism that resolves the risk.
