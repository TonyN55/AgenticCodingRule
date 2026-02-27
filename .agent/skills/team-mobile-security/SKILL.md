---
name: team-mobile-security
description: Use when implementing or reviewing mobile features that process external input, secrets, or sensitive user/session data.
---

# Skill: Mobile Security Standard
Priority: P1 (HIGH)

## Precedence
- Follow [POLICY.md](/Users/anhnguyen/Desktop/HealthAppVibe/.agent/skills/POLICY.md).
- Security checks apply in addition to architecture and testing workflows.

---

## Security Rules

- Never store secrets in plain text.
- Validate all external input.
- Do not trust client-side state.
- Handle sensitive data carefully (tokens, credentials).

---

## Security Checklist

1. Secret storage
- Use secure platform storage only (Keychain/Keystore).
- No secrets in source, logs, analytics payloads, or plain preferences.

2. Logging and telemetry
- Redact tokens, credentials, personal identifiers, and session IDs.
- Ensure error reporting excludes sensitive request/response bodies by default.

3. Transport security
- Enforce TLS for all network calls.
- Define and document certificate pinning policy for high-risk endpoints.

4. Token/session lifecycle
- Short-lived access tokens where possible.
- Implement refresh, revoke, and logout invalidation behavior.
- Clear sensitive state on logout/background policy as required.

5. Input and trust boundaries
- Validate and sanitize all external inputs (deep links, push payloads, API data, local imports).
- Treat client-side state as untrusted for authorization decisions.

---

## Output Contract
When this skill applies, the response must include:

1. Sensitive-data touchpoints reviewed
2. Checklist status (pass/fail per section)
3. Risks found and severity
4. Next mitigation action

---

## Valid / Invalid Examples

Valid:
- Store refresh token in Keychain/Keystore and redact it from logs.
- Reject malformed deep-link params before navigation/use.

Invalid:
- Persist access token in plain shared preferences/UserDefaults.
- Log full HTTP authorization headers in debug or production logs.

End of skill.
