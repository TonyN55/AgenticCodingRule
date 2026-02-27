# Skill: Release Quality Gate
Priority: P0 (CRITICAL)
Scope: Any build, release, or deployment action

## Purpose
Prevent low-quality or unreviewed code from being released.
Ensure engineering standards are enforced until the final step.

---

## Release Preconditions (ALL REQUIRED)

Before any release, the agent MUST verify:

- Approved unit tests exist
- Tests were written before implementation
- Tests were not modified post-approval
- All tests are passing
- Initial code review completed
- Refactor completed (if requested)
- Post-refactor review approved
- PR checklist fully satisfied

If ANY condition is missing → RELEASE IS BLOCKED.

---

## Agent Behavior Rules

- The agent MUST ask:
  > “Please confirm all release conditions are satisfied.”

- The agent MUST NOT:
  - Assume readiness
  - Infer approval
  - Skip verification steps

---

## Violation Handling

If release is requested without satisfying conditions:
1. Stop execution
2. List missing conditions
3. Request explicit override

---

## Override Rules (Leader Only)

Release override MUST be explicit:
- “Override release gate for this deployment.”

Overrides apply only to the current release.

---

End of skill.