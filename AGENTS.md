# Agent Instructions (Codex)

항상 한국어로 답변하고, 사용자가 다른 언어를 명시할 때만 변경합니다.

이 프로젝트는 AI 기반 9단계 앱 개발 방법론을 따릅니다.

## 시작 전 필수 확인

- 작업 시작 시 `PROGRESS.md`를 읽고 현재 단계와 다음 할 일을 파악합니다.
- 구현 단계 또는 버그 수정 전에는 `docs/troubleshooting/log.md`에서 관련 이슈를 먼저 확인합니다.
- 구현 단계에서는 대상 플랫폼에 맞는 `docs/patterns/` 문서를 먼저 확인합니다.
- 앱 아이디어가 들어오면 9단계 플로우를 시작하되, 각 단계 완료 후 사용자 확인을 받고 다음 단계로 진행합니다.
- "이어서 하자" 요청이 오면 `PROGRESS.md`의 현재 상태에서 재개합니다.
- "멈춰", "여기까지", "stop here" 요청이 오면 현재 결과와 다음 할 일을 `PROGRESS.md`에 기록하고 중단합니다.

## 개발 플로우 (9단계)

1. **기획 초안** -> docs/planning/v1_기획안.md
2. **기획 리뷰** (AI 멀티 페르소나) -> docs/planning/v1_리뷰.md
3. **기획 확정** -> docs/planning/FINAL_기획안.md
4. **디자인** (Figma / 코드 직행 / 전체 플로우)
5. **디자인 리뷰** (UI/UX/일관성/기획정합성)
6. **디자인 확정** -> docs/dev/개발의뢰서.md
7. **개발 스펙 논의** (비용 $0 목표) -> docs/dev/개발스펙_논의록.md
8. **개발 가이드 작성** -> docs/dev/
9. **구현** (문서 기반 코드 생성 + 자체 리뷰)

각 단계 완료 후 사용자 확인을 받고 다음 단계로 진행합니다.

## 단계별 산출물 기준

### 1. 기획 초안

- 프로젝트 개요
- 핵심 기능: v1 범위와 향후 기능 분리
- 화면 와이어프레임: 필요 시 ASCII로 작성
- 기술 요구사항: 서버 비용 무료 티어 우선
- 데이터 모델
- 비기능 요구사항

### 2. 기획 리뷰

AI가 멀티 페르소나로 자율 리뷰합니다. 사용자가 각 페르소나 역할을 수행하지 않습니다.

- 사용성 전문가: 흐름 불편, 단계 과다, 빠른 경로, 주요 액션 탭 수 검토
- 가시성 전문가: 중요 정보 강조, 우선순위/마감/상태 시각화, 빈 상태, 시각 계층 검토
- 가독성 전문가: 정보 밀도, 1/2차 정보 계층, 한 화면 과밀, 완료/보관 항목 처리 검토

피드백은 `Red: 필수 수정`, `Yellow: 권장 수정`으로 분류합니다.

### 3. 기획 확정

- Red 전체와 타당한 Yellow 항목을 반영합니다.
- 반영 후 자체 검증 결과를 포함합니다.

### 4. 디자인

- 선택지: Figma, 코드 직행, 전체 디자인 플로우
- 사용자가 디자인을 건너뛰면 7단계 개발 스펙으로 이동합니다.

### 5. 디자인 리뷰

AI가 4개 관점으로 자율 리뷰합니다.

- UI/Visual: 완성도, 색상/대비, 타이포그래피 계층, 간격/정렬/리듬
- UX/Interaction: 흐름, 최소 44x44pt 터치 영역, 로딩/성공/오류 피드백, 내비게이션
- Consistency/Accessibility: 폰트/색상/라운드 일관성, WCAG, 대비, 스크린 리더 고려
- Planning Alignment: 기획 반영 여부, 기획에 없는 기능 여부, 화면별 기획 비교, 누락 화면 발견 시 FINAL 기획 업데이트

### 6. 디자인 확정

- 디자인 리뷰 피드백을 반영합니다.
- 필요하면 리뷰와 수정을 반복합니다.
- 개발의뢰서에는 구현자가 바로 이해할 수 있는 화면/상태/흐름을 정리합니다.

### 7. 개발 스펙 논의

AI가 2개 관점으로 자율 논의합니다.

- 시니어 개발자: 기술 스택, 아키텍처, 비용 최적화, 코드 품질 원칙 반영
- 서버 개발자: Serverless vs BaaS, 무료 티어 범위, 데이터 구조, 인증 전략

반드시 포함:

- 기술 스택 표
- 데이터 구조
- 폴더 구조
- 구현 순서
- 예상 일정
- 비용 비교
- 무료 비용 체크리스트: Firebase Spark, Supabase Free, Cloudflare Workers Free 등

### 8. 개발 가이드

- 텍스트 처리, 색상/폰트, API 설계, 코딩 컨벤션 등 구현에 필요한 지침을 `docs/dev/`에 작성합니다.

### 9. 구현

권장 순서:

1. 프로젝트 설정
2. 모델
3. 순수 비즈니스 로직
4. Protocol/Interface
5. 서비스 구현
6. Store/ViewModel
7. 메인 UI
8. 상세 UI
9. 공통 컴포넌트
10. 통합

각 기능 구현 후 시니어 개발자 관점으로 자체 리뷰합니다.

- 기획 문서와 일치하는가?
- 성능 이슈가 없는가?
- 접근성을 충족하는가?
- 오류 처리가 충분한가?
- 비즈니스 로직이 순수 함수로 분리되었는가?
- 파일이 300줄 이하이고 기능별로 분리되었는가?
- 함수/클래스가 단일 책임을 지키는가?
- Protocol/Interface 기반 추상화와 의존성 주입을 사용하는가?

## 코드 품질 4원칙

1. **순수 함수**: 비즈니스 로직은 순수 함수로. 부수 효과 분리
2. **모듈화**: 기능별 파일 분리. 300줄 이하. 느슨한 결합
3. **단일 책임**: 함수 하나 = 일 하나. "and" 금지
4. **SOLID**: Protocol/Interface에 의존. 구체 구현 주입

## 권장 폴더 구조

```text
src/
  app/              Entry point, routing
  core/components/  Shared UI components
  core/extensions/  Utilities, helpers
  data/store/       State management
  data/services/    External service implementations
  domain/models/    Data models
  domain/logic/     Pure business logic
  domain/protocols/ Abstractions
  features/         Per-screen/feature modules
```

## 의존성 방향

```text
features --> domain <-- data
    |            ^
    +---> core --+
app --> everything
```

- `domain`은 다른 레이어에 의존하지 않습니다.
- `features`끼리는 직접 의존하지 않고 Store/ViewModel 또는 라우팅 경계를 통해 연결합니다.
- Store/ViewModel은 순수 로직을 호출하고 결과를 상태에 반영합니다.
- 네트워크, DB, 알림 등 부수 효과는 `data/services/`로 분리합니다.

## 데이터 흐름

```text
User Action -> View -> Store/ViewModel.method()
  -> domain/logic pure function -> new state
  -> Store/ViewModel update -> UI re-render
```

## 변경 관리 (필수)

코드를 직접 수정하지 않는다. 반드시 문서부터 업데이트한다.

| 변경 유형 | 순서 |
|----------|------|
| 기능 추가 | Plan -> Design -> Spec -> Code |
| 기능 수정 | Plan -> Design -> Code |
| UI 변경 | Design -> Code |
| 버그 수정 | 관련 기획/스펙 확인 -> Code |

예외:

- 이미 문서화된 계획을 구현하는 경우에는 해당 문서를 확인한 뒤 코드 수정 가능
- 설정/문서/빌드 보조 파일 수정은 문서 선행 원칙을 상황에 맞게 적용
- 버그를 고친 뒤 원인이나 재발 방지 지식이 생기면 `docs/troubleshooting/log.md`에 기록

## Codex 작업 체크리스트

Kiro hook이 Codex에서는 자동 실행되지 않으므로 아래를 수동으로 지킵니다.

- 코드 파일 수정 전: 관련 문서가 먼저 업데이트되었는지 확인합니다.
- 코드 작성 후: 순수 함수, 300줄 이하, 단일 책임, 추상화 의존, 올바른 폴더 위치를 점검합니다.
- 버그 수정 후: `docs/troubleshooting/log.md`에 Problem, Root Cause, Solution, Prevention 형식으로 기록합니다.
- 새 패턴 발견 시: 관련 `docs/patterns/` 문서에 추가합니다.
- 단계 완료 시: `PROGRESS.md`의 현재 단계, 다음 할 일, 변경 이력을 갱신합니다.

## Codex 전용 팁

- 샌드박스 환경에서 안전하게 실행
- PROGRESS.md를 확인해서 현재 진행 단계 파악
- docs/dev/개발스펙_논의록.md의 기술 스택과 폴더 구조를 따르세요
- 트러블슈팅 이슈는 docs/troubleshooting/log.md에 기록

## 상세 규칙

`.kiro/steering/` 폴더의 steering 파일을 원천 규칙으로 참조합니다. AGENTS.md와 steering이 충돌하면 더 구체적인 steering 규칙을 우선합니다.
