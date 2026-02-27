---
name: team-mobile-tdd
description: Use when implementing mobile domain or view-model logic with a strict test-first contract and mandatory re-review after refactoring.
---

# Skill: Team Mobile TDD Contract Standard
Priority: P1 (HIGH)
Scope: Mobile Domain & ViewModel layers

## Purpose
Enforce Test-Driven Development with tests acting as behavior contracts.
Tests define expected behavior and MUST NOT change during implementation review.

This skill modifies AI behavior before, during, and after implementation.

---

## Precedence
- Follow [POLICY.md](/.agent/skills/POLICY.md).
- This skill defines strict test-first execution under `leader-engineering-gate`.
- `team-mobile-testing` is complementary and must not replace this workflow.

---

## Core TDD Rules (STRICT)

### 1. Test-As-Contract Principle
- Tests define the expected behavior.
- Once tests are written and approved, they become immutable contracts.
- Implementation must adapt to tests, never the opposite.

---

### 2. Mandatory Development Flow
The following order MUST be followed:

1. Propose unit test cases and request explicit approval
2. Write unit tests from approved test cases
3. Ensure tests fail (red)
4. Implement code to pass tests (green)
5. Initial review (tests unchanged)
6. Refactor implementation
7. Re-review refactored code
   - If not approved → refactor again
   - If approved → proceed

After test cases are approved, tests may not be modified unless the user gives explicit override approval.

---

### 3. Review & Refactor Rules
- Refactoring is mandatory after initial green state when requested.
- Refactored code MUST be reviewed again.
- Passing tests does NOT imply merge readiness.
- Merge is allowed only after post-refactor review approval.

---

### 4. What Must Be Tested
Unit tests are REQUIRED for:
- UseCases
- Business rules
- ViewModels (state transitions, error cases)

Unit tests are OPTIONAL for:
- UI Views
- Platform boilerplate
- Simple data mapping

---

### 5. Test Design Rules
- One test verifies one behavior.
- Tests must be deterministic and isolated.
- Avoid testing implementation details.
- Prefer input → output and state transition verification.

---

### 6. ViewModel Testing Rules
- ViewModels must be testable without UI.
- Dependencies must be injectable.
- State changes must be observable and verifiable.

---

### 7. AI Behavior Constraints
- Always propose test cases before writing implementation.
- After test cases are approved, do NOT modify tests without explicit user override.
- After refactoring, MUST request re-review.
- Never self-approve merge readiness.

---

## Output Contract
When this skill applies, the response must include:

1. Test cases (or test file references if already written)
2. Current phase: red/green/review/refactor/re-review
3. Test immutability status (approved and locked/unlocked by override)
4. Result (pass/fail/blocked)
5. Next action

---

## Valid / Invalid Examples

Valid:
- Write tests from approved cases, confirm red, then implement to green.
- Keep tests unchanged through review/refactor unless explicit override is given.

Invalid:
- Implement feature logic before red tests exist.
- Edit approved tests to fit current implementation without override.

End of skill.
