# Skills Policy

## Purpose
Define precedence, composition, and required outputs when multiple skills apply.

## Precedence
Apply skills in this order:

1. `leader-engineering-gate`
2. `team-mobile-tdd`
3. `team-mobile-core`
4. `team-mobile-architecture`
5. Platform skill: `android-kotlin-standard` or `ios-swiftui-standard`
6. `team-mobile-security`
7. `team-mobile-testing`

## Composition Rules
- Higher-precedence skills constrain lower-precedence skills.
- Lower-precedence skills may refine implementation details only.
- If two skills conflict, follow the higher-precedence rule and note the conflict.

## Standard Output Contract
When applying any skill, the agent response must include:

1. `Applied skill(s)` list
2. `Checks performed` list
3. `Result` (pass/fail/blocked)
4. `Next action` (what is needed to proceed)

## Quality Gate Output Contract
When `leader-engineering-gate` applies, response must include:

1. Proposed test cases
2. Expected behaviors
3. Explicit approval prompt
4. Halt state until approval
