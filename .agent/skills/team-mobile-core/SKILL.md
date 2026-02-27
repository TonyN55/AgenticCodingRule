---
name: team-mobile-core
description: Use when working on any mobile task in this repository to enforce baseline product, readability, error handling, and separation-of-concerns standards.
---

# Skill: Team Mobile Core Standard
Priority: P0 (CRITICAL)
Scope: All mobile projects (iOS & Android)

## Purpose
Ensure consistency, maintainability, and product-focused development
across the entire mobile team.

This skill sets baseline standards for mobile work in this repository.

---

## Precedence
- Follow [POLICY.md](/.agent/skills/POLICY.md).
- This skill is a baseline and must not override `leader-engineering-gate` or `team-mobile-tdd`.

---

## Core Rules (ALWAYS APPLY)

### 1. Product First
- Always optimize for user experience and clarity.
- Prefer simple, predictable flows over clever abstractions.
- Do not add features or layers unless clearly justified.

---

### 2. Code Ownership & Readability
- Code must be readable by another engineer in 3 minutes.
- Avoid magic numbers, unclear flags, or implicit behavior.
- Prefer explicit state over implicit side effects.

---

### 3. Separation of Concerns
- UI renders state only.
- Business logic lives outside UI.
- Data access is never coupled to UI.

---

### 4. Naming Rules
- Names must describe intent, not implementation.
- Avoid abbreviations unless platform-standard.
- Booleans must read naturally (isEnabled, hasError).

---

### 5. Error Handling
- Never silently fail.
- Errors must be observable and debuggable.
- User-facing errors must be human-readable.

---

### 6. AI Constraints
- Do not hallucinate APIs or platform features.
- Ask before making assumptions.
- Prefer platform-native solutions.

---

## Output Contract
When this skill applies, the response must include:

1. Applied skill(s)
2. Core constraints used (product/readability/separation/error handling)
3. Result (pass/fail/blocked)
4. Next action

---

## Valid / Invalid Examples

Valid:
- Move business logic from UI into ViewModel/use case.
- Add explicit error states instead of silent failure.

Invalid:
- Add hidden side effects in UI event handlers.
- Introduce unclear flags like `mode = 2` without semantic naming.

End of skill.
