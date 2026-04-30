# Change Management

코드를 직접 수정하지 않습니다. 반드시 문서부터 업데이트합니다.

## 트리거

사용자가 아래처럼 요청하면 이 문서를 먼저 적용합니다.

- "수정해줘"
- "추가해줘"
- "바꿔줘"
- "개선해줘"
- "구현해줘"
- "화면/UI를 바꿔줘"
- "더 직관적으로 바꿔줘"
- "사용성 좋게 바꿔줘"
- "Figma를 수정했어"
- "코드에 맞춰 Figma도 바꿔줘"

## 변경 유형별 순서

| 변경 유형 | 순서 |
|----------|------|
| 기능 추가 | Plan -> Design -> Spec -> Code |
| 기능 수정 | Plan -> Design -> Code |
| UI 변경 | Figma/Design 문서 -> Code |
| 코드에서 UI 변경 발생 | Code 변경 의도 문서화 -> Figma 반영 -> `figma_reference.md` 기록 |
| Figma 변경 발생 | `figma_reference.md` 갱신 -> Design/Dev 문서 갱신 -> Code 반영 |
| 버그 수정 | 관련 기획/스펙 확인 -> Code |

## 예외

- 이미 문서화된 계획을 구현하는 경우에는 해당 문서를 확인한 뒤 코드 수정 가능
- 설정/문서/빌드 보조 파일 수정은 문서 선행 원칙을 상황에 맞게 적용
- 단순 오타, 비시각적 리팩터링, 테스트 코드 변경은 Figma 반영 생략 가능

## 작업 체크리스트

- 코드 파일 수정 전: 관련 문서가 먼저 업데이트되었는지 확인합니다.
- UI 코드 수정 전: Figma 노드 정보와 `docs/design/figma_reference.md` 최신 여부를 확인합니다.
- UI/디자인 변경 전: `docs/agents/ux-design-laws.md`에서 관련 법칙을 확인합니다.
- 코드 작성 후: 순수 함수, 300줄 이하, 단일 책임, 추상화 의존, 올바른 폴더 위치를 점검합니다.
- UI 코드 작성 후: Figma 노드와 화면 구현의 차이를 확인하고 필요한 경우 Figma 또는 코드를 다시 맞춥니다.
- 버그 수정 후: `docs/troubleshooting/log.md`에 Problem, Root Cause, Solution, Prevention 형식으로 기록합니다.
- 단계 완료 시: `PROGRESS.md`의 현재 단계, 다음 할 일, 변경 이력을 갱신합니다.
