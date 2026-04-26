---
inclusion: auto
---

# AI App Development Flow (9 Steps)

This steering is always active for all app development requests.

## Trigger
When user describes an app idea, start this 9-step flow with confirmation.

## Rules
- Save deliverables as files at each step
- Get user confirmation before proceeding
- Cost minimization: server cost $0/month, BaaS first, v1 core features only

## Code Quality (Steps 7-9)
1. Pure Functions: same input = same output, no side effects in business logic
2. Modularization: split by feature, max 300 lines per file
3. Single Responsibility: one function = one job
4. SOLID: depend on abstractions, inject implementations

## Step 1: Planning Draft
Project overview, core features (v1 vs future), screen wireframes (ASCII),
tech requirements (server free tier), data model, non-functional requirements.
Output: docs/planning/v1_plan.md

## Step 2: Planning Review (AI Multi-Persona)
Usability / Visibility / Readability experts.
Red (must fix) / Yellow (recommended).
Output: docs/planning/v1_review.md

## Step 3: Planning Finalization
Apply Red + valid Yellow, self-verify.
Output: docs/planning/FINAL_plan.md

## Step 4: Design
A) Figma (MCP tools)  B) Skip to code (step 7)  C) Full design flow

## Step 5: Design Review (AI Multi-Persona)
- UI/Visual expert (8yr senior): visual polish, color, typography
- UX/Interaction expert (7yr senior): flow, touch targets
- Consistency/Accessibility expert (4yr mid): WCAG, consistency
- Planning alignment expert (3yr mid): missing/extra vs plan
- Reverse feedback: update FINAL plan if missing screens found

## Step 6: Design Finalization
Output: docs/dev/dev_brief.md

## Step 7: Dev Spec Discussion
- Senior dev (architecture): tech stack, cost optimization
- Server dev: serverless vs BaaS, free tier analysis
- Include: tech stack table, data structure, folder structure, implementation order, cost comparison
- Cost checklist: Firebase Spark / Supabase Free / Cloudflare Workers Free
Output: docs/dev/dev_spec.md

## Step 8: Dev Guide
Text handling, color/font, API design, coding conventions as needed.
Output: docs/dev/ folder

## Step 9: Implementation
Order: setup -> models -> pure logic -> protocols -> services -> store -> main UI -> detail UI -> components -> integration
Self-review after each feature: plan alignment, performance, accessibility, code quality.

## Change Management (Required)
NEVER modify code directly. Always update docs first.
Change request -> Analyze scope -> Update docs -> Modify code

| Change Type | Scope |
|------------|-------|
| Add feature | Plan -> Design -> Spec -> Code |
| Modify feature | Plan -> Design -> Code |
| UI change | Design -> Code |
| Bug fix | Verify plan -> Code only |

## Pause/Resume
- Stop here -> summarize, pause
- Continue -> resume from last step
- Skip design -> jump to step 7
- Just code -> fast track from step 7
