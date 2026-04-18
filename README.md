# AI Agent Operating Directives & Skill Toolkit

This repository contains the core operating directives, engineering principles, and modular execution skills designed to guide AI coding assistants (such as Copilot, Cursor, or custom AI agents) when interacting with our codebases. 

By standardizing how AI agents analyze, extend, and debug code, we ensure that AI-assisted development maintains architectural integrity, code stability, and aligns with human developer intuition.

## 🧠 Core Directives (`AGENTS.md`)

The `AGENTS.md` file acts as the primary entry point and system prompt for the AI agent. It defines the high-level operating structure and establishes the non-negotiable boundaries for AI behavior.

Its core structure consists of three main parts:
1. **High-Value Rules (Core Engineering Principles):** Defines the strict architectural constraints, project conventions, and safe refactoring practices the AI must follow.
2. **Skill Routing (Collaboration & Execution Modes):** Acts as a router, providing logical conditions that instruct the AI on when to trigger and load specific modular skill files based on the task's context.
3. **Michael Polanyi Guidance (Tacit Knowledge):** Instructs the AI on how to emulate human developer intuition, prioritize codebase context over generic patterns, and make pragmatic engineering decisions.

## 🧰 Modular Skills (`.skills/`)

The `.skills/` directory contains specialized, scenario-based collaboration protocols. 

Rather than relying on generic programming advice, the AI agent dynamically loads these skill files (as directed by the routing rules in `AGENTS.md`) to execute tasks using precise, step-by-step workflows. These skills cover specific development modes, such as careful analysis, safe runtime extensions, and complex UI debugging.

---
*Note: Do not modify these core directive files without team consensus, as they directly control the safety boundaries and behavior of our AI-assisted development workflows.*
