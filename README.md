# 🚀 AI Project Starter Template

> **어떤 AI 코딩 도구든, 아이디어 하나면 앱을 만들 수 있는 범용 프로젝트 템플릿**
>
> Kiro, Claude, Codex, Cursor, Copilot, Windsurf — 모두 지원합니다.

---

## ⚡ 빠른 시작 (3분)

### 1. 템플릿 복사
```bash
cp -r ~/Desktop/ai-project-starter ~/Desktop/내프로젝트이름
cd ~/Desktop/내프로젝트이름
git init
```

### 2. AI 도구 열기

평소 쓰는 AI 도구로 프로젝트 폴더를 열면 설정이 자동 적용됩니다.

| AI 도구 | 설정 파일 | 적용 방식 |
|---------|----------|----------|
| **Kiro** | `.kiro/steering/*.md` | ✅ 자동 (steering) |
| **Claude Code** | `CLAUDE.md` | ✅ 자동 (Project Instructions) |
| **Codex (OpenAI)** | `AGENTS.md` | ✅ 자동 (Agent Instructions) |
| **Cursor** | `.cursorrules` | ✅ 자동 |
| **Copilot** | `.github/copilot-instructions.md` | ✅ 자동 |
| **Windsurf** | `.windsurfrules` | ✅ 자동 |

### 3. 아이디어 말하기

아무 AI 도구에서 아이디어만 말하면 9단계 플로우가 자동 실행됩니다:

```
직장인을 위한 심플한 TODO 앱 만들고 싶어
```

AI가 "앱 개발 플로우를 시작할게요"라고 물어보면 "ㅇㅇ"이라고 답하세요.

---

## 📋 9단계 개발 플로우

```
1. 기획 초안    →  아이디어를 기획안으로
2. 기획 리뷰    →  AI 멀티 페르소나 리뷰 (사용성/가시성/가독성)
3. 기획 확정    →  피드백 반영 → 최종 기획안
4. 디자인       →  Figma / AI 생성 / 코드 직행 선택
5. 디자인 리뷰  →  AI 멀티 페르소나 리뷰 (UI/UX/접근성/기획정합성)
6. 디자인 확정  →  리뷰 반영 → 개발 의뢰서
7. 개발 스펙    →  기술 스택 + 비용 $0 설계
8. 개발 가이드  →  텍스트/컬러/API/에러 처리 가이드
9. 구현         →  문서 기반 코드 생성 + 자체 리뷰
```

### 빠른 경로

- 디자인 건너뛰기: `디자인 건너뛰고 바로 개발 스펙부터 시작하자`
- 바로 코딩: `바로 코딩하자. 기술 스택은 [X]이고, 핵심 기능은 [Y]야.`

---

## 📁 폴더 구조

```
ai-project-starter/
├── .kiro/steering/                     # Kiro 설정 (핵심 엔진)
│   ├── app-development-flow.md         # 9단계 플로우
│   ├── code-quality-rules.md           # 코드 품질 규칙
│   ├── figma-code-reflection.md        # Figma-Code 반영 규칙
│   └── shared-knowledge.md             # 공통 지식 참조
├── .github/copilot-instructions.md     # Copilot 설정
├── CLAUDE.md                           # Claude Code 설정
├── AGENTS.md                           # Codex 설정
├── .cursorrules                        # Cursor 설정
├── .windsurfrules                      # Windsurf 설정
├── PROGRESS.md                         # 진행 상황 추적
├── docs/                               # 산출물 (플로우 진행 시 자동 생성)
│   ├── agents/                         # 모든 AI 에이전트 공통 규칙 원본
│   ├── planning/                       # 기획 문서
│   ├── design/                         # 디자인 문서, Figma 참조 문서
│   ├── dev/                            # 개발 스펙, 가이드
│   ├── troubleshooting/log.md          # 트러블슈팅 로그
│   └── AI_앱개발_방법론_가이드.md        # 상세 방법론 설명서
└── README.md
```

---

## 🧠 핵심 철학

| 원칙 | 설명 |
|------|------|
| 🪶 가볍게 시작 | 최소 기능으로 빠르게. 완벽한 설계보다 빠른 출시 |
| 💰 비용 $0 | 서버 비용 월 $0 목표. BaaS 무료 티어 우선 |
| 🔄 반복 리뷰 | AI에게 여러 역할을 줘서 반복 검토 → 품질 향상 |
| 📄 문서 = 설계도 | 문서 품질 = 코드 품질. AI는 문서를 보고 코드를 생성 |
| 🔒 문서 먼저 | 코드 직접 수정 금지. 반드시 문서부터 업데이트 |
| 🎨 Figma 기준 | UI 변경은 Figma MCP와 `docs/design/figma_reference.md`를 기준으로 반영 |

---

## 🔧 AI 도구별 활용 팁

| 도구 | 강점 |
|------|------|
| **Kiro** | steering 자동 적용, Figma MCP 연동, Hook 자동화 |
| **Claude Code** | 긴 문서 작성, 멀티 페르소나 리뷰, `/init`으로 컨텍스트 파악 |
| **Codex** | 샌드박스 안전 실행, 코드 생성/디버깅/리팩토링 |
| **Cursor** | `@파일명` 참조, Composer 멀티파일 수정 |
| **Copilot** | 인라인 자동완성, `/explain` `/fix` `/tests` 명령 |
| **Windsurf** | Cascade 멀티파일 작업, 코드베이스 전체 컨텍스트 |

---

## 📖 상세 방법론 가이드

9단계 방법론의 상세 설명, 각 단계별 프롬프트 예시, 실전 팁:

→ [`docs/AI_앱개발_방법론_가이드.md`](docs/AI_앱개발_방법론_가이드.md)

## 🤖 공통 에이전트 규칙

모든 AI 도구가 같은 기준을 따르도록 공통 규칙은 `docs/agents/`에 모았습니다.

- [`docs/agents/README.md`](docs/agents/README.md): 읽는 순서와 에이전트별 진입점
- [`docs/agents/workflow-harness.md`](docs/agents/workflow-harness.md): 요청별 작업 하네스
- [`docs/agents/development-flow.md`](docs/agents/development-flow.md): 9단계 플로우와 페르소나 리뷰
- [`docs/agents/figma-code-reflection.md`](docs/agents/figma-code-reflection.md): Figma-Code 반영 규칙
- [`docs/agents/ux-design-laws.md`](docs/agents/ux-design-laws.md): UX 법칙 기반 디자인 체크리스트
- [`docs/agents/change-management.md`](docs/agents/change-management.md): 문서 우선 변경 관리
- [`docs/agents/implementation-planning.md`](docs/agents/implementation-planning.md): 구현 전 작업 계획
- [`docs/agents/test-and-verification.md`](docs/agents/test-and-verification.md): 테스트 우선과 완료 전 검증
- [`docs/agents/debugging.md`](docs/agents/debugging.md): 원인 중심 디버깅
- [`docs/agents/code-quality.md`](docs/agents/code-quality.md): 코드 품질 규칙

---

*이 템플릿은 Todoly 프로젝트의 실제 개발 프로세스를 기반으로 만들어졌습니다.*
