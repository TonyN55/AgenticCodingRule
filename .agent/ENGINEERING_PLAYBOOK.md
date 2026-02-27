# Engineering Playbook

Version: 1.0  
Last updated: 2026-02-26  
Scope: Mobile engineering workflow for this repository

## 1. Muc tieu
- Tao quy trinh ky thuat ro rang, nhat quan, co the audit.
- Giam loi do thieu gate chat luong, thieu test, va xung dot quy trinh.
- Dam bao AI/human cung lam viec theo cung mot contract.

## 2. Nguyen tac van hanh
- Evidence before assertions: moi ket luan "done/pass" phai co bang chung.
- Test-first cho logic: logic thay doi -> test contract thay doi co kiem soat.
- Separation of concerns: UI render state, logic o ViewModel/UseCase, data o repository/data source.
- Security by default: xu ly secrets, input, token, log theo checklist.
- Explicit approvals: cac gate quan trong phai co approval ro rang.

## 3. Nguon quy tac chuan
- [skills/POLICY.md] (/.agent/skills/POLICY.md)
- [skills/leader-engineering-gate/SKILL.md] (/.agent/skills/leader-engineering-gate/SKILL.md)
- [skills/team-mobile-tdd/SKILL.md] (/.agent/skills/team-mobile-tdd/SKILL.md)
- [skills/team-mobile-core/SKILL.md] (/.agent/skills/team-mobile-core/SKILL.md)
- [skills/team-mobile-architecture/SKILL.md] (/.agent/skills/team-mobile-architecture/SKILL.md)
- [skills/android-kotlin-standard/SKILL.md] (/.agent/skills/android-kotlin-standard/SKILL.md)
- [skills/ios-swiftui-standard/SKILL.md] (/.agent/skills/ios-swiftui-standard/SKILL.md)
- [skills/team-mobile-security/SKILL.md] (/.agent/skills/team-mobile-security/SKILL.md)
- [skills/team-mobile-testing/SKILL.md] (/.agent/skills/team-mobile-testing/SKILL.md)

## 4. Rule precedence (bat buoc)
Ap dung theo thu tu:
1. `leader-engineering-gate`
2. `team-mobile-tdd`
3. `team-mobile-core`
4. `team-mobile-architecture`
5. Platform skill (`android-kotlin-standard` hoac `ios-swiftui-standard`)
6. `team-mobile-security`
7. `team-mobile-testing`

Neu conflict:
1. Follow skill co precedence cao hon.
2. Ghi ro conflict trong review note.
3. Chi override khi co explicit approval.

## 5. Delivery lifecycle (end-to-end)

### Phase A: Intake
- Mo ta problem statement 1-2 cau.
- Xac dinh pham vi thay doi: logic/UI/security/data.
- Xac dinh skill se apply theo precedence.

### Phase B: Test Approval Gate
- Propose test cases.
- Liet ke expected behaviors.
- Gui explicit approval prompt.
- Dung lai cho den khi co approval ro rang.

### Phase C: TDD Execution
1. Viet test tu approved test cases.
2. Run test de fail (red).
3. Implement toi thieu de pass (green).
4. Initial review (khong doi test).
5. Refactor implementation.
6. Re-review sau refactor.

### Phase D: Quality + Security Validation
- Architecture checks.
- Platform-specific code checks.
- Security checklist checks.
- Testability checks.

### Phase E: Merge Readiness
Chi duoc declare "Ready for merge" khi:
- Test approved.
- Test pass.
- Initial review done.
- Refactor/re-review done va approved.

## 6. Definition of Ready (DoR)
Task chi duoc vao implementation khi:
- Co acceptance criteria ro.
- Co expected behavior list.
- Co owner/reviewer.
- Xac dinh scope la logic hay UI-only.
- Co quyet dinh testing strategy.

## 7. Definition of Done (DoD)
Task duoc coi la done khi:
- Dat acceptance criteria.
- Qua cac quality gate theo precedence.
- Khong con critical/high issues mo.
- Co changelog/notes neu can.
- Co evidence commands hoac artifacts.

## 8. Output contracts (bat buoc cho moi response ky thuat)
Moi response thuc thi phai co:
1. Applied skill(s)
2. Checks performed
3. Result (`pass`/`fail`/`blocked`)
4. Next action

Khi `leader-engineering-gate` apply, bo sung:
1. Proposed test cases
2. Expected behaviors
3. Explicit approval prompt
4. Current state (`waiting_for_approval`/`in_review`/`blocked`/`ready_for_merge`)

## 9. Architecture playbook
- Presentation: UI render state, khong chua business logic.
- Domain: UseCase/business rules, phu thuoc abstractions.
- Data: repository/data source/API, implement domain interfaces.
- Navigation: khong dat logic dieu huong trong UI component.
- Side effects: explicit, de trace.

Checklist:
- Co layer nao skip layer khac khong?
- Domain co import framework UI khong?
- UI co call truc tiep API/database khong?

## 10. Testing & TDD playbook
- Mot test = mot hanh vi.
- Test deterministic, isolated, khong phu thuoc UI render.
- ViewModel phai inject dependencies.
- Sau khi test cases duoc approve, test bi lock (chi mo bang explicit override).

Test review checklist:
- Co test cho happy path?
- Co test cho error path?
- Co test state transitions?
- Co test edge cases input invalid?

## 11. Platform implementation standards

### Android/Kotlin
- Dung structured concurrency.
- Coroutine phai co scope.
- Handle cancel/error explicit.
- Tranh `!!`.
- UI state immutable, uu tien sealed classes.

### iOS/SwiftUI
- View declarative, gon nhe.
- Logic/state chinh o ViewModel.
- `@State` chi cho local UI state.
- Async/await dung cach, khong block main thread.
- Tranh force unwrap.

## 12. Security playbook

### 12.1 Secret storage
- Chi dung Keychain/Keystore.
- Cam secrets trong source, logs, analytics payloads, plain preferences.

### 12.2 Logging & telemetry
- Redact token, credential, session id, personal identifiers.
- Khong dump full auth headers hoac sensitive payloads.

### 12.3 Transport security
- Bat buoc TLS.
- Co policy certificate pinning cho high-risk endpoints.

### 12.4 Token/session lifecycle
- Access token short-lived neu co the.
- Co refresh/revoke/logout invalidation.
- Clear sensitive in-memory/local state khi logout.

### 12.5 Input/trust boundaries
- Validate deep link, push payload, API data, import data.
- Khong trust client-side state cho authorization.

Security severity rubric:
- Critical: lo secret/token, bypass auth.
- High: trust boundary violation, logging sensitive data.
- Medium: missing validation, weak session cleanup.
- Low: hardening/recommendation.

## 13. Code review playbook

Thu tu review:
1. Correctness vs approved tests.
2. Regression risk.
3. Architecture/layering.
4. Security checklist.
5. Readability/maintainability.

Review output format:
- Findings first (theo severity).
- File + line reference.
- Assumptions/open questions.
- Change summary ngan.

## 14. Incident & hotfix mode
- Chi su dung khi production impact.
- Van phai giu security checks bat buoc.
- Co the xin explicit override cho mot so gate, nhung phai log ly do.
- Sau hotfix: mandatory post-incident review + bo sung tests.

## 15. Metrics can theo doi hang tuan
- Lead time (idea -> merge).
- Reopen rate sau review.
- Defect escape rate (bug vao production).
- Test coverage cho Domain/ViewModel.
- Security findings theo severity.
- % PR pass ngay lan review dau.

## 16. Template su dung nhanh

### 16.1 Approval prompt template
```text
Please approve these test cases before I proceed.
Waiting for explicit approval to implement.
```

### 16.2 Engineering status template
```text
Applied skill(s): ...
Checks performed: ...
Result: pass|fail|blocked
Next action: ...
```

### 16.3 Merge readiness template
```text
State: ready_for_merge
Evidence:
- Tests approved: yes/no
- Tests passing: yes/no
- Initial review complete: yes/no
- Post-refactor review approved: yes/no
```

## 17. Governance & update process
- Owner: Engineering lead hoac delegate.
- Review cadence: 2 tuan/lan hoac khi co thay doi process lon.
- Moi thay doi playbook phai:
1. Co ly do
2. Co tac dong mong doi
3. Update references toi skill files

## 18. Quick start cho task moi
1. Xac dinh scope (logic hay UI-only).
2. Chon applied skills theo precedence.
3. Neu co logic: vao Test Approval Gate ngay.
4. Chay TDD + review loop.
5. Chay security + architecture checks.
6. Declare merge readiness khi du evidence.
