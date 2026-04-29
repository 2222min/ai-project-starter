# Copilot Instructions

이 프로젝트는 AI 기반 9단계 앱 개발 방법론을 따릅니다.

## 개발 플로우 (9단계)

1. 기획 초안 -> docs/planning/v1_기획안.md
2. 기획 리뷰 (AI 멀티 페르소나) -> docs/planning/v1_리뷰.md
3. 기획 확정 -> docs/planning/FINAL_기획안.md
4. 디자인 (Figma / 코드 직행 / 전체 플로우)
5. 디자인 리뷰 (UI/UX/일관성/기획정합성)
6. 디자인 확정 -> docs/dev/개발의뢰서.md
7. 개발 스펙 논의 (비용 $0 목표) -> docs/dev/개발스펙_논의록.md
8. 개발 가이드 작성 -> docs/dev/
9. 구현 (문서 기반 코드 생성 + 자체 리뷰)

## 코드 품질 4원칙

1. 순수 함수: 비즈니스 로직은 순수 함수로. 부수 효과 분리
2. 모듈화: 기능별 파일 분리. 300줄 이하. 느슨한 결합
3. 단일 책임: 함수 하나 = 일 하나. "and" 금지
4. SOLID: Protocol/Interface에 의존. 구체 구현 주입

## 변경 관리

코드를 직접 수정하지 않는다. 반드시 문서부터 업데이트한다.

## Copilot 전용 팁

- /explain 명령으로 기존 코드 분석 후 새 코드 작성
- /fix 명령으로 버그 수정 시 기획안과 비교
- /tests 명령으로 순수 함수 로직부터 테스트
- PROGRESS.md로 현재 진행 단계 파악

## 상세 규칙

.kiro/steering/ 폴더의 steering 파일 참조
