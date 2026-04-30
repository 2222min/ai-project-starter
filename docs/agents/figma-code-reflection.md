# Figma-Code 반영 규칙

Figma MCP를 디자인의 기본 소스로 사용합니다. 코드와 디자인 중 한쪽이 바뀌면 다른 쪽에도 반영하고, 참조 문서에 기록합니다.

## 기준 문서

| 문서 | 역할 |
|------|------|
| `docs/design/figma_reference.md` | Figma 파일, 노드, 코드 매핑, 반영 상태 기록 |
| `docs/dev/개발의뢰서.md` | 확정 디자인과 화면/상태/흐름 설명 |
| `docs/dev/개발스펙_논의록.md` | 기술 스택, 구조, 구현 순서 |

## `figma_reference.md` 필수 항목

- Figma 파일명과 파일 URL
- 주요 화면별 Frame 노드 ID와 노드 URL
- 공통 컴포넌트별 Component 노드 ID와 노드 URL
- 화면/컴포넌트와 코드 파일 경로 매핑
- 마지막 반영 확인 일시
- 변경 출처: Figma 변경, 코드 변경, 기획 변경 중 하나
- 반영 완료 기록
- 반영 대기 항목과 후속 작업

## 코드에서 UI가 바뀔 때

1. UI 변경 의도를 관련 문서에 먼저 기록합니다.
2. Figma MCP로 해당 Frame/Component를 수정합니다.
3. `docs/design/figma_reference.md`의 노드 정보와 반영 확인 일시를 갱신합니다.
4. 코드에 반영합니다.
5. 화면 구현 후 Figma 노드와 코드가 일치하는지 자체 리뷰합니다.

## Figma가 바뀔 때

1. Figma MCP로 변경된 노드의 ID/URL과 변경 범위를 확인합니다.
2. `docs/design/figma_reference.md`를 먼저 갱신합니다.
3. 필요하면 `docs/dev/개발의뢰서.md` 또는 개발 가이드를 갱신합니다.
4. 코드에 반영합니다.
5. 반영 후 UI/UX/일관성/기획정합성 페르소나와 `docs/agents/ux-design-laws.md` 기준으로 자체 리뷰합니다.

## 반영 예외

- 단순 오타, 비시각적 리팩터링, 테스트 코드 변경은 Figma 반영을 생략할 수 있습니다.
- Figma MCP 접근이 불가능하면 `docs/design/figma_reference.md`의 반영 대기 항목에 이유와 후속 작업을 기록합니다.
