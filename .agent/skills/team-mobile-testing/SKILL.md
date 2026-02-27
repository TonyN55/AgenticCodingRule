---
name: team-mobile-testing
description: Use when writing or reviewing mobile code to keep business logic and view-model behavior testable without UI coupling.
---

# Skill: Mobile Testing Standard
Priority: P1 (HIGH)

## Precedence
- Follow [POLICY.md](/.agent/skills/POLICY.md).
- This skill defines testability principles only.
- For strict execution workflow, approval gates, and test immutability, follow `team-mobile-tdd`.

---

## Testing Rules

- Business logic must be unit-testable.
- ViewModels must be testable.
- Avoid logic that requires UI to test.
- Write code assuming tests will be added.

---

## Output Contract
When this skill applies, the response must include:

1. Testability assessment (what is testable and what is coupled)
2. Gaps found (if any)
3. Recommended test seams (interfaces, injected dependencies, state observability)
4. Result (pass/fail/blocked) and next action

---

## Valid / Invalid Examples

Valid:
- Inject dependencies into ViewModel to enable unit tests.
- Keep business rules in use cases or pure functions.

Invalid:
- Put decision logic inside UI callbacks that require rendering to test.
- Hardcode singletons in business logic paths that block isolation.

End of skill.
