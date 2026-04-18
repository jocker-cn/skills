---
name: maintainable-runtime-extension
description: Use this skill when the user wants to extend runtime-sensitive behavior through small changes, correct owner boundaries, and encapsulated complexity without broad refactors.
---

# Maintainable Runtime Extension Skill

Use this skill when new runtime behavior must be added safely, but the user does not want a broad rewrite of the existing flow.

## Core rules

- Extend the current owner instead of refactoring multiple owners at once.
- Add new behavior through a local seam such as a helper, wrapper, controller, or draft state boundary when that reduces future churn.
- Keep the existing public flow stable unless the user explicitly asks to reshape it.
- Encapsulate new complexity where it belongs instead of spreading conditionals across the current path.
- Prefer add, validate, switch, then remove when replacing legacy behavior.

## When to use this skill

- The current structure is not ideal, but changing it broadly would create unnecessary migration cost.
- The user wants future-safe extension without dragging the current task into a larger refactor.
- Runtime behavior, render stability, or transport timing make ad hoc logic hard to grow safely.
- The user explicitly asks to keep the current structure and only add a method-based or boundary-based extension path.

## Design approach

- Preserve owner boundaries first, then improve local structure inside the owner.
- Move transforms and coordination logic to the boundary that already owns the behavior.
- Keep data contracts stable while letting the new seam absorb complexity.
- Name new state and helpers by behavior, not by temporary implementation detail.
- Prefer one focused extension point over many repeated booleans or conditionals.

## Validation

- Validate the new path before touching cleanup.
- Prove that existing behavior still works alongside the extension path.
- Keep regression checks close to the owner that now contains the seam.
- Stop once the new path is stable unless the user asks to continue into cleanup or consolidation.

## Avoid

- broad structural rewrites during behavior discovery
- leaking new runtime rules across unrelated owners
- one-off flags that duplicate the same decision in multiple places
- replacing stable flows just because the architecture could be cleaner later

## Common failure mode

If the code becomes more scattered while the intent was to contain complexity, the extension boundary was chosen too late or too low in the flow.