# Code Quality Rules

코드를 생성하거나 수정할 때 항상 적용합니다.

## 4원칙

| 원칙 | 규칙 |
|------|------|
| 순수 함수 | 비즈니스 로직은 같은 입력에 같은 출력을 반환하고 부수 효과를 갖지 않습니다. |
| 모듈화 | 기능별 파일로 분리하고, 파일은 300줄 이하를 목표로 합니다. |
| 단일 책임 | 함수 하나는 한 가지 일만 합니다. 이름에 `and`가 들어가면 분리 후보입니다. |
| SOLID | Protocol/Interface에 의존하고 구체 구현은 주입합니다. |

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

## 구현 후 자체 점검

- 기획 문서와 일치하는가?
- 성능 이슈가 없는가?
- 접근성을 충족하는가?
- 오류 처리가 충분한가?
- 비즈니스 로직이 순수 함수로 분리되었는가?
- 파일이 300줄 이하이고 기능별로 분리되었는가?
- 함수/클래스가 단일 책임을 지키는가?
- Protocol/Interface 기반 추상화와 의존성 주입을 사용하는가?
- 새 파일이 올바른 폴더에 있는가?
- 기능 추가 시 기존 코드를 과도하게 수정하지 않고 확장 가능한가?

## 트러블슈팅과 패턴

- 구현 또는 버그 수정 전 `docs/troubleshooting/log.md`에서 관련 이슈를 확인합니다.
- 버그를 고친 뒤 원인이나 재발 방지 지식이 생기면 `docs/troubleshooting/log.md`에 기록합니다.
- 새 패턴을 발견하면 관련 `docs/patterns/` 문서에 추가합니다.
