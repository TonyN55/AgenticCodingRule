---
name: team-mobile-architecture
description: Use when designing or changing mobile architecture to enforce layering, dependency direction, explicit state, and reusable domain logic.
---

# Skill: Mobile Architecture Standard
Priority: P0 (CRITICAL)
Scope: Mobile apps

## Precedence
- Follow [POLICY.md](/.agent/skills/POLICY.md).
- Respect higher-precedence flow controls from `leader-engineering-gate` and `team-mobile-tdd`.

---

## Architecture Rules

### 1. Layered Architecture
- Presentation: UI only
- Domain: business logic & use cases
- Data: repositories, data sources, APIs

No layer may skip another layer.

---

### 2. State Management
- UI observes state, never owns business logic.
- State must be immutable where possible.
- Side effects must be explicit.

---

### 3. Dependency Direction
- Presentation depends on Domain.
- Domain depends on abstractions only.
- Data implements Domain interfaces.

---

### 4. Navigation
- Navigation logic must not live inside UI components.
- Prefer centralized or coordinator-based navigation.

---

### 5. Reusability
- Extract reusable logic early.
- Do not duplicate business rules across screens.

---

## Output Contract
When this skill applies, the response must include:

1. Target layer(s) touched (presentation/domain/data)
2. Dependency direction check
3. Side-effect placement check
4. Result (pass/fail/blocked) and next action

---

## Valid / Invalid Examples

Valid:
- Presentation calls domain use case interface; data layer implements it.
- Navigation decisions handled in coordinator/router instead of view.

Invalid:
- UI directly calling API client or database.
- Domain layer importing framework-specific UI classes.

End of skill.
