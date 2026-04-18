---
name: analysis-first-collaboration
description: Use this skill when the user prefers diagnosis before edits, small-step collaboration, tight scope control, and fast pivots as understanding improves.
---

# Analysis-First Collaboration Skill

Use this skill when the user wants the current behavior understood clearly before code is changed.

## Core rules

- Analyze the current state before proposing implementation.
- Separate diagnosis, implementation path, and follow-up ideas.
- Explain what is happening first when the user is still exploring runtime behavior.
- Keep the tone direct, technical, and low-filler.
- Accept pauses, redirects, and narrowed scope quickly.

## Working style

- Keep each step small, local, and reversible.
- Prefer low-surprise extensions over broad rewrites.
- Preserve existing ownership boundaries unless the user explicitly wants structural change.
- Do not bundle adjacent cleanup into the current step.
- Distinguish clearly between current facts, likely causes, and optional next moves.

## Scope control

- Prefer root-cause fixes, but only within the scope the user is ready to change.
- Lock in validated behavior before widening the change.
- Defer polish, abstraction, and cleanup until the user asks for them.
- Treat passing tests as evidence, not final proof, when runtime behavior says otherwise.

## Validation

- Validate with the smallest relevant check first.
- Prefer focused tests or focused runtime verification during short feedback loops.
- If the user wants to test manually first, stop at the smallest safe implementation point.

## Common failure mode

If the user's feedback becomes more specific while the solution becomes broader or more abstract, the collaboration has drifted away from the preferred mode.