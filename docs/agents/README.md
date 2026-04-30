# AI Agent Rules

이 폴더는 모든 AI 에이전트가 공통으로 따라야 하는 규칙의 원본입니다.

## 읽는 순서

1. `PROGRESS.md`
2. `docs/agents/workflow-harness.md`
3. `docs/agents/development-flow.md`
4. `docs/agents/figma-code-reflection.md`
5. `docs/agents/ux-design-laws.md`
6. `docs/agents/change-management.md`
7. `docs/agents/implementation-planning.md`
8. `docs/agents/test-and-verification.md`
9. `docs/agents/debugging.md`
10. `docs/agents/code-quality.md`
11. 작업과 관련된 `docs/planning/`, `docs/design/`, `docs/dev/`, `docs/patterns/`
12. 구현 또는 버그 수정 전 `docs/troubleshooting/log.md`

## 에이전트별 진입점

| 에이전트 | 진입 파일 |
|----------|-----------|
| Codex | `AGENTS.md` |
| Claude Code | `CLAUDE.md` |
| Cursor | `.cursorrules` |
| Windsurf | `.windsurfrules` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| Kiro | `.kiro/steering/*.md` |

## 우선순위

1. 사용자의 최신 명시 요청
2. 각 에이전트 시스템/도구 제약
3. 이 폴더의 공통 규칙
4. 에이전트별 진입 파일의 도구별 팁
5. 기존 프로젝트 문서와 코드 패턴

충돌이 있으면 더 구체적인 규칙을 따르고, 판단이 필요한 경우 사용자에게 짧게 확인합니다.

## 참고한 방법론

`obra/superpowers`의 핵심 원칙 중 우리 프로젝트에 맞는 부분만 반영했습니다.

- 작업 전 적용할 규칙을 먼저 고르는 하네스
- 구현 전 작은 단위의 계획 작성
- 가능한 범위의 테스트 우선 구현
- 추측보다 원인 조사를 우선하는 디버깅
- 완료 주장 전 검증 결과 확인

우리 프로젝트의 기준은 계속 9단계 플로우, 문서 우선 변경 관리, Figma MCP 기반 UI 반영 규칙입니다.
