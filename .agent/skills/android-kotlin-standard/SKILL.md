---
name: android-kotlin-standard
description: Use when modifying Kotlin or Android code to enforce UI separation, immutable state, coroutine safety, and architecture consistency.
---

# Skill: Android Kotlin Engineering Standard
Priority: P0 (CRITICAL)
Scope: Kotlin / Android files

## Precedence
- Follow [POLICY.md](.agent/skills/POLICY.md).
- Applies after core architecture and quality-gate constraints.

---

## Kotlin Rules

### 1. UI Responsibility
- UI renders state only.
- No business logic in Activities/Composables.
- Use ViewModel as single source of truth.

---

### 2. State Management
- State must be immutable.
- Use sealed classes for UI state.
- Avoid mutable shared state.

---

### 3. Coroutines
- Use structured concurrency.
- Never launch coroutines without scope.
- Handle cancellation and errors explicitly.

---

### 4. Architecture
- Follow MVVM or MVI strictly.
- Use UseCases for business logic.
- Repositories abstract data sources.

---

### 5. Kotlin Style
- Prefer expression over statements.
- Avoid nullable chains without handling.
- Avoid !! operator.

---

## Output Contract
When this skill applies, the response must include:

1. UI boundary check (View/Compose vs ViewModel/use case)
2. Coroutine safety check (scope/cancellation/error handling)
3. State model check (immutability/sealed UI state)
4. Result (pass/fail/blocked) and next action

---

## Valid / Invalid Examples

Valid:
- Launch work in `viewModelScope` and handle cancellation explicitly.
- Model screen state as immutable sealed classes.

Invalid:
- Run business rules directly inside composables/activities.
- Use `!!` on nullable API responses in production paths.

End of skill.
