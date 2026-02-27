---
name: leader-engineering-gate
description: Use when implementing or reviewing logic-heavy changes that require explicit test approval, staged reviews, and merge-readiness gates.
---

# Skill: Leader Engineering Quality Gate
Priority: P0 (CRITICAL)
Scope: All feature implementation involving logic

## Purpose
Enforce leadership-level control over the engineering process.
Guarantee correctness, quality, and consistency across AI-assisted development.

This skill defines the default quality gate workflow for this repository.

---

## Precedence
- Highest-precedence skill. Follow [POLICY.md](/.agent/skills/POLICY.md).
- If any other skill conflicts with this flow, this gate flow wins unless explicit override is given.

---

## Core Leadership Principles

- Tests define behavior (contract).
- Code implements behavior.
- Reviews validate quality.
- Refactor improves design.
- No step may be skipped.
- The agent has no authority to self-approve.

---

## 1. Test Approval Gate (ABSOLUTE)

Before implementing any feature involving logic, the agent MUST:

1. Propose unit test cases
2. Clearly list expected behaviors
3. Explicitly request approval
4. STOP execution

Implementation MUST NOT begin without explicit approval.

Silence, vague confirmation, or implied consent does NOT count as approval.

---

## 2. What Requires Test Approval

Approval is REQUIRED for:
- New features
- UseCases
- ViewModels
- Business rules
- State transitions
- Error handling logic
- Auth, payment, sync, or core flows

Approval is NOT required for:
- UI-only layout or styling
- Formatting or renaming
- Documentation changes
- Pure boilerplate

---

## 3. Mandatory Development Flow (ENFORCED)

The agent MUST follow this exact order:

1. Propose unit tests
2. Request approval
3. Write unit tests
4. Ensure tests fail (red)
5. Implement code to pass tests (green)
6. Initial review (tests unchanged)
7. Refactor implementation
8. Request re-review of refactored code
   - If NOT approved → refactor again
   - If approved → proceed
9. Merge readiness declared only after re-review approval

At no point may approved tests be modified.

---

## 4. Review Authority Rules

### Initial Review
- Validate correctness against tests
- Detect hacks or shortcuts
- Ensure architectural compliance

### Post-Refactor Review (MANDATORY)
- Validate code quality improvement
- Ensure refactor improves readability and structure
- Confirm no hidden side effects
- Confirm architecture is preserved

Passing tests does NOT imply merge readiness.

---

## 5. Approval Language (MANDATORY)

The agent MUST use explicit approval requests.

Required phrases include:
- “Please approve these test cases before I proceed.”
- “Waiting for explicit approval to implement.”
- “Please review the refactored implementation.”

Without these phrases, the agent must remain idle.

---

## 6. Violation Handling

If the user asks to:
- Skip tests
- Implement immediately
- Modify approved tests
- Merge after tests without review
- Skip re-review after refactor

The agent MUST:
1. Stop execution
2. Explain the violation
3. Request explicit override from the leader

---

## 7. Override Rules (Leader Only)

Overrides MUST be explicit and intentional.

Valid override examples:
- “Override test approval gate for this task.”
- “Proceed without re-review for this change.”

Overrides apply ONLY to the current task.
They do NOT change global rules.

---

## 8. AI Authority Constraints

- The agent cannot approve its own work.
- The agent cannot skip steps for speed.
- The agent cannot reinterpret approval.
- The agent cannot merge or declare readiness without approval.

---

## 9. Merge Readiness Declaration

The agent may declare:
> “Ready for merge.”

ONLY if:
- Tests are approved
- Tests pass
- Initial review is completed
- Refactor (if any) is completed
- Post-refactor review is approved

Otherwise, the agent must remain in review/refactor loop.

---

## Output Contract
When this skill applies, the response must include:

1. Proposed test cases
2. Expected behaviors
3. Explicit approval request text
4. Current state: `waiting_for_approval`, `in_review`, `blocked`, or `ready_for_merge`
5. Next action required from user/reviewer

---

## Valid / Invalid Examples

Valid:
- "Please approve these test cases before I proceed."
- Stop after proposing tests until explicit approval is received.

Invalid:
- Start implementation after implicit confirmation.
- Declare merge readiness immediately after green tests without post-refactor review approval.

---

End of skill.
