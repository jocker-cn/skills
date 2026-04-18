---
name: runtime-sensitive-ui-debugging
description: Use this skill when the user is sensitive to runtime behavior, render stability, timing, visual polish, and architecture-level side effects in interactive UI work.
---

# Runtime-Sensitive UI Debugging Skill

Use this skill when the user cares about actual runtime behavior as much as code correctness.

## Core rules

- Trace runtime behavior end to end before deciding where the bug lives.
- Separate data state, visual state, render state, and transport state.
- Keep fixes inside the correct owner boundary whenever possible.
- Prefer the smallest change that proves or disproves a behavioral hypothesis.

## Detail levels to cover

### UI interaction level

- Be precise about trigger timing, visual transitions, repeated renders, flicker, scroll movement, height changes, and partial content states.
- Call out how user-visible behavior changes during streaming, weak network timing, delayed final events, and repeated updates.
- Discuss whether a fix changes display timing, animation feel, or visible stability.

### State and flow level

- Distinguish clearly between history flow and live flow, draft state and final state, merge behavior and replacement behavior.
- Track id stability, ownership of temporary placeholders, and when state should be reset or preserved.
- Reconcile test coverage with the real runtime path instead of assuming the happy path is sufficient.

### Architecture and stability level

- Watch for unnecessary object recreation, reference instability, rerender propagation, and accidental global replacement.
- Preserve references when nothing changed and render stability matters.
- Discuss performance in terms of update frequency, batching, memo boundaries, and owner-level rerender impact.
- Encapsulate complexity in the right boundary when future-safe extension is needed, but avoid broad structural churn.

## Validation

- Use focused tests close to the owner of the behavior.
- Prefer runtime checks that reproduce the actual event order when timing matters.
- If tool output and observed behavior disagree, investigate the mismatch instead of trusting the test result blindly.

## Common failure mode

If the code looks correct in isolation but the real UI still behaves poorly, the analysis probably missed a runtime boundary such as timing, owner flow, or rerender propagation.