# Assignment Rubric: Code Quality & Maintainability

**Course:** CS 340-26  
**Assignment:** Code Quality — Part 2 of 3  
**Total Points:** 100  
**Evaluated in:** `code_quality_grade.md` in each project repository

---

## Overview

This assignment evaluates whether your code is *readable, organized, and built to last*. Code is written once and read many times — by teammates, future maintainers, and evaluators. This rubric rewards teams that write code another developer could pick up and continue without help, regardless of whether it runs correctly.

The four sub-criteria are evaluated independently and combined for a total score.

---

## Sub-Criterion 2a — Readability & Style (25 points)

Consistent style is a signal that the team communicated and worked as a unit. Inconsistent naming or leftover development artifacts indicate code that was not reviewed before submission.

| Points | Criteria |
|--------|----------|
| 23–25 | Consistent naming conventions throughout the entire codebase (all Python in snake_case, all React components in PascalCase, etc.). Consistent indentation and spacing. No dead code, commented-out blocks, leftover debug strings, or placeholder links in submitted work. Files are reasonably sized (no 600-line monoliths where 100 lines would do). |
| 18–22 | Generally consistent style with isolated exceptions — e.g., one file using a different convention, one leftover `console.log`, or one placeholder comment that was not cleaned up. |
| 12–17 | Style inconsistencies visible across multiple files or between contributors. Development artifacts present in submitted code: TODO comments acknowledging known bugs, placeholder URLs, debug `print()` / `console.log()` output that runs in production. |
| 6–11 | Multiple naming convention conflicts, inconsistent indentation, significant dead code or placeholder content throughout. Code appears to have been submitted without a final review pass. |
| 0–5 | Code is unreadable due to style issues, or so minimal (< 50 lines) that style cannot be meaningfully assessed. |

**Language-specific conventions evaluators enforce:**

| Language | Convention |
|---|---|
| Python | PEP 8: snake_case variables/functions, PascalCase classes, 4-space indent, `class Foo:` not `class Foo :` |
| JavaScript / JSX | camelCase for variables and functions, PascalCase for React components and classes |
| TypeScript | Same as JS; also: prefer `interface` over `type` for object shapes |
| Java | PascalCase classes, camelCase methods/variables, Javadoc format for public APIs |
| GDScript | snake_case variables/functions, PascalCase class names, `@export` for designer-facing variables |
| C | lowercase_with_underscores for functions, `ALL_CAPS` for macros, no magic numbers inline |
| C# | PascalCase for public methods and classes, camelCase for private fields |

---

## Sub-Criterion 2b — Documentation (25 points)

Good documentation explains the *why* behind a decision, not just *what* the code does. A reader who already knows the language should be able to understand *why* a function exists, *why* a particular algorithm was chosen, and *what* the expected inputs and outputs are — without having to reverse-engineer the logic.

| Points | Criteria |
|--------|----------|
| 23–25 | Every non-trivial function and class has a docstring or header comment explaining: purpose, parameters, return values, and error conditions. Module-level comments explain the overall design intent. Non-obvious decisions (e.g., why a particular algorithm, why a particular data structure, why a fallback exists) are explained inline. |
| 18–22 | Most functions documented. Complex logic has inline comments. Module structure is explained somewhere. Minor gaps — e.g., a few short utility functions without comments, or one module with no header. |
| 12–17 | Some comments present but inconsistent — some files well-documented, others completely bare. Complex logic (async chains, pointer arithmetic, state machine transitions) is uncommented. |
| 6–11 | Minimal documentation. Most functions have no comments. The team's intent cannot be understood without deeply reading the code. |
| 0–5 | No documentation of any kind, or comments that only restate what the code already says (`# increment i` above `i += 1`). |

**What evaluators look for:**
- Module-level docstring explaining what the file does and how it fits into the project
- Function-level docstring with parameter types, return type, and notable side effects
- Inline comments before non-obvious logic blocks (not every line)
- Explanation of workarounds, known limitations, or `TODO` items with issue references

---

## Sub-Criterion 2c — Modularization (30 points)

A well-modularized codebase separates concerns so that each file, class, and function has one clear job. This makes code independently testable, reusable, and replaceable without breaking unrelated features.

| Points | Criteria |
|--------|----------|
| 27–30 | Code organized into small, single-responsibility functions and classes. Each module has a clear, narrow purpose. Shared functionality is extracted into reusable utilities — no copy-pasted logic. Architecture follows the established pattern for the framework (see below). No file exceeds ~200 lines without a strong justification. |
| 21–26 | Good modularization with minor violations — e.g., one function that does two things, a small amount of duplication that could be factored out, or one file slightly over the size threshold. |
| 13–20 | Mostly modular but with one or more significant violations: a 300–500 line monolithic file, a component defined in two places with different signatures, API calls embedded inside UI components, or business logic inside a controller. |
| 6–12 | Large monolithic files or classes. Significant duplication. No clear separation of concerns — data logic mixed with rendering logic, all routes in one file, all game logic in one script. |
| 0–5 | All code in a single file or function. No evidence of modularization. |

**Framework-specific modularization patterns evaluators check:**

| Framework | Expected Pattern |
|---|---|
| Django | `models.py` (data), `views.py` (HTTP), `services.py` (business logic), `stats.py` (pure functions), `management/commands/` (CLI) |
| Flask | Blueprint-based route separation; one Blueprint per domain; models in `models/`; logic not in `app.py` |
| FastAPI | Router files per domain; Pydantic schemas separate from route handlers |
| React | Pages in `src/pages/`; shared UI in `src/components/`; API calls in `src/services/` or `src/lib/`; auth state in a Context provider |
| Spring Boot | Entity / Repository / Service / Controller per domain package; DTOs for API responses |
| Godot | One script per node; signal-based communication between nodes; no direct `get_parent()` calls for cross-node logic |
| C (embedded) | One `.c`/`.h` pair per module; no `#include` of `.c` files; headers expose only the public API |

---

## Sub-Criterion 2d — Complexity (20 points)

Simple code is correct code. Unnecessary complexity — deep nesting, over-engineered abstractions, magic numbers — makes bugs harder to find and features harder to add.

| Points | Criteria |
|--------|----------|
| 18–20 | Logic is as simple as the problem allows. Functions rarely exceed 30 lines. Nesting depth rarely exceeds 3 levels. All magic numbers are named constants or `@export` / `const` variables. Long logic chains are broken into named helper functions that read like English. |
| 14–17 | Generally simple. One or two places where a helper function would reduce nesting, or a named constant would replace a magic number. |
| 9–13 | Some functions are too long (50+ lines) or deeply nested (4+ levels). Magic numbers appear throughout. A few places where the logic could be significantly simplified. |
| 4–8 | Multiple functions with excessive length or nesting. Logic is difficult to follow without a debugger. Unnecessary intermediate variables or abstractions add confusion. |
| 0–3 | Logic is incomprehensible due to unnecessary complexity, or so minimal (< 50 lines total) that complexity cannot be meaningfully assessed. |

**What evaluators flag:**
- Functions longer than 50 lines without a clear justification
- Nesting depth > 4 (if/for/try/match inside each other)
- Inline magic numbers: `if (count > 37)` instead of `const MAX_RESULTS = 37`
- Redundant overrides: e.g., `get_queryset()` returning `Model.objects.all()` (the default)
- Copy-pasted logic that could be a loop or a utility function

---

## Score Sheet

| Sub-Criterion | Max | Score |
|---|---|---|
| 2a — Readability & Style | 25 | |
| 2b — Documentation | 25 | |
| 2c — Modularization | 30 | |
| 2d — Complexity | 20 | |
| **Total** | **100** | |

**Letter grade conversion:**

| Score | Grade |
|-------|-------|
| 93–100 | A |
| 90–92 | A− |
| 87–89 | B+ |
| 83–86 | B |
| 80–82 | B− |
| 77–79 | C+ |
| 73–76 | C |
| 70–72 | C− |
| 60–69 | D |
| < 60 | F |
