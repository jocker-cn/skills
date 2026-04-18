**Core AI Operating Directives**
This document defines the strict, non-negotiable engineering principles and architectural constraints that the AI agent must strictly adhere to during all coding, debugging, and refactoring processes. These rules override generic programming advice to ensure codebase stability and architectural integrity.

## 1) High-Value Rules (Core Engineering Principles)

- **Configuration Management:** Access configuration through the designated central configuration manager or environment loader. Do not hardcode environment-specific branches (e.g., `if dev`) directly into feature logic. Centralize config models in a dedicated directory and use standard typing/annotations to bind them.
- **Service & API Conventions:** Standardize external calls. All new API or service requests must use the project's shared HTTP client wrappers or request-factory patterns. Do not bypass shared interceptors (such as auth headers, logging, or error handling) without explicit justification.
- **Build & Pipeline Stability:** Preserve core build, compilation, and dependency configuration files (e.g., Webpack, Maven, Gradle, requirements.txt) and their existing behaviors. Do not alter aliases, base paths, or build profiles unless the task explicitly demands it.
- **Environment Isolation:** Never mutate production configuration instances at runtime. Keep development-only overrides strictly within local development workflows.
- **State & Architecture:** Place new application state or domain models in the currently approved architectural directories. Treat legacy state management or outdated service folders strictly as deprecated bridges; do not add new logic there.
- **Legacy Refactoring:** Replace legacy logic incrementally using the Strangler Fig pattern: add the new implementation, validate it alongside the old, switch the call sites, and finally remove the legacy code. Do not rewrite everything at once.
- **Source of Truth for Version Control:** When resolving Git merge conflicts, `pull` rebases, or PR syncs, treat the target branch (e.g., `main` or `develop`) as the definitive source of truth. If the correct resolution is ambiguous, stop immediately and request human guidance. Do not guess.

## 2) Skill Routing (Collaboration & Execution Modes)

- Always pair repo-specific work with `.github/skills/gpbw-project/SKILL.md`.
- Use `.skills/analysis-first-collaboration/SKILL.md` when the user wants diagnosis before edits and prefers small, reversible steps to understand the root cause before proposing broad solutions.
- Use `.skills/maintainable-runtime-extension/SKILL.md` when the user wants new behavior added safely without a broad refactor, especially in complex or runtime-sensitive flows where logic should be added through local seams.
- Use `.skills/runtime-sensitive-ui-debugging/SKILL.md` when runtime behavior, performance stability, timing, flicker, memory leaks, or reference stability are central to the task, rather than just static syntax correctness.

## 3) Michael Polanyi Guidance: Use Tacit Knowledge Directly

Michael Polanyi's principle applies here: *we know more than we can fully spell out.* The AI must emulate this by observing repository context:

- **Context is King:** After analyzing nearby working code, use informed tacit knowledge to choose the smallest, most natural architectural pattern that fits the existing repository style.
- **Pragmatism over Dogma:** Do not force every engineering judgment into a strict, generic design pattern (like forcing Factory/Observer patterns unnecessarily) if the local codebase already demonstrates a clear, pragmatic approach that works.
- **Emulate Developer Intuition:** Recognize module boundaries, naming conventions, acceptable levels of duplication (knowing when to duplicate vs. when to abstract), and understand when a simple inline fix is preferable to creating a complex new abstraction.
- **Evidence-Based Reasoning:** Always ground your decisions in tangible repository evidence first. Tacit knowledge is a tool for completing your reasoning and adapting to the project's specific flavor, not an excuse to skip thorough code inspection.