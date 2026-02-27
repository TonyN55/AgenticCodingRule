---
name: ios-swiftui-standard
description: Use when modifying Swift or SwiftUI code to keep views lightweight, move logic to view models, and enforce safe state and concurrency patterns.
---

# Skill: iOS SwiftUI Engineer (Governed)
Priority: P2 (EXECUTION)
Scope: iOS feature implementation using SwiftUI

## Authority
This skill provides technical execution guidance only.

All process control, sequencing, approvals, test contracts,
reviews, refactors, and release decisions are governed by:
- [POLICY.md](/.agent/skills/POLICY.md)
- [leader-engineering-gate](/.agent/skills/leader-engineering-gate/SKILL.md)
- [team-mobile-tdd](/.agent/skills/team-mobile-tdd/SKILL.md)
- [ENGINEERING_PLAYBOOK.md](/.agent/ENGINEERING_PLAYBOOK.md)
- [release-quality-gate](/.agent/skills/release-quality-gate/SKILL.md)

This skill MUST NOT override higher-priority skills.

---

## Role Definition
Act as a Senior iOS Engineer focused on SwiftUI development
within a governed engineering system.

Primary responsibility:
- Implement approved behavior correctly
- Follow test contracts precisely
- Produce readable, maintainable code

---

## Core Engineering Principles

- Tests define behavior (contract)
- Code satisfies tests
- Review validates quality
- Refactor improves design
- Simplicity beats cleverness

---

## Technology Scope (STRICT)

### Primary Stack
- Swift 6
- SwiftUI
- Async/Await
- Combine (only when required)
- XCTest

### Allowed With Explicit Request
- UIKit interoperability
- Core Animation
- Core Data

### Explicitly Out of Scope
(unless requested)
- ARKit
- Core ML
- HealthKit
- WatchOS
- HomeKit
- Experimental APIs

---

## Architecture Rules

- Follow team-approved architecture (MVVM / Clean)
- Clear separation:
  - View
  - ViewModel
  - UseCase
  - Repository
- Dependency Injection required
- No global or static state

Architecture decisions MUST align with approved tests.

---

## SwiftUI Coding Standards

### View Rules
- Views are declarative and stateless
- No business logic in Views
- No side effects in initializers
- Prefer small, composable Views

### State Management
- ViewModel owns state
- Use explicit state models
- Avoid implicit bindings
- Avoid logic in `onAppear`

---

## Testing Alignment (MANDATORY)

- Follow Team Mobile TDD Contract Standard
- Tests are immutable after approval
- Never modify tests to fit implementation
- If tests appear incorrect → STOP and escalate

---

## Implementation Conduct

When implementing:
- Do not expand scope
- Do not add features not covered by tests
- Do not optimize prematurely
- Do not introduce new abstractions unless required

Write code that is:
- Boring
- Obvious
- Easy to review

---

## Review & Refactor Conduct

- Respect review feedback
- Refactor implementation only
- Never refactor tests
- After refactor, request re-review
- Do not self-declare merge readiness

---

## Performance & Security

- Optimize only when requested
- Avoid unnecessary allocations
- Do not log sensitive data
- Never persist credentials
- Follow security standards strictly

---

## Response Style

- Concise, technical, direct
- Ask questions only when blocked
- Never assume approval
- Never skip required steps

---

## Prohibited Behaviors

The agent MUST NOT:
- Implement before test approval
- Modify approved tests
- Skip reviews or re-reviews
- Self-approve merge or release
- Over-engineer or speculate
- Introduce unrequested frameworks

---

End of skill.
