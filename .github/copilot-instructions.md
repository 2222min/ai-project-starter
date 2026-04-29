# Copilot Instructions

항상 한국어로 답변하고, 사용자가 다른 언어를 명시할 때만 변경합니다.

## 필수 참조 문서

작업 시작 시 아래 문서를 순서대로 확인합니다.

1. `PROGRESS.md`
2. `docs/agents/README.md`
3. `docs/agents/workflow-harness.md`
4. `docs/agents/development-flow.md`
5. `docs/agents/figma-code-reflection.md`
6. `docs/agents/change-management.md`
7. `docs/agents/implementation-planning.md`
8. `docs/agents/test-and-verification.md`
9. `docs/agents/debugging.md`
10. `docs/agents/code-quality.md`

## Copilot 작업 규칙

- 코드를 직접 수정하지 않고, 관련 문서를 먼저 업데이트합니다.
- 수정/추가/구현 요청은 `docs/agents/workflow-harness.md`를 먼저 적용합니다.
- UI 변경은 Figma MCP와 `docs/design/figma_reference.md`를 기준으로 반영합니다.
- 구현 또는 버그 수정 전 `docs/troubleshooting/log.md`와 관련 `docs/patterns/` 문서를 확인합니다.
- 완료 보고 전 방금 실행한 검증 결과를 확인합니다.
- 단계 완료 시 `PROGRESS.md`를 갱신합니다.
- Kiro steering과 충돌하면 더 구체적인 규칙을 우선합니다.

## Copilot 전용 팁

- `/explain`으로 기존 코드를 분석한 뒤 새 코드를 작성합니다.
- `/fix`로 버그를 수정할 때 기획/스펙 문서와 비교합니다.
- `/tests`는 순수 함수 로직부터 우선 작성합니다.
