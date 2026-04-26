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
- All multi-persona reviews are performed by AI autonomously (not delegated to user)
- User reviews the final result and gives additional feedback if needed

## Code Quality (Steps 7-9)
1. Pure Functions: same input = same output, no side effects in business logic
2. Modularization: split by feature, max 300 lines per file
3. Single Responsibility: one function = one job
4. SOLID: depend on abstractions, inject implementations

---

## Step 1: Planning Draft
Project overview, core features (v1 vs future), screen wireframes (ASCII),
tech requirements (server free tier), data model, non-functional requirements.
Output: `docs/planning/v1_plan.md`

---

## Step 2: Planning Review (AI Multi-Persona)

AI performs review from 3 expert perspectives simultaneously:

### Persona 1: Usability Expert
- Are there inconvenient points in the user flow?
- Are there features with too many steps?
- Suggest quick paths (inline add, shortcuts, etc.)
- Check if common actions require minimal taps

### Persona 2: Visibility Expert
- Is important information visually emphasized?
- Are priority/deadline/status clearly visualized?
- How are empty states handled?
- Is there proper visual hierarchy?

### Persona 3: Readability Expert
- Is information density appropriate?
- Is there proper 1st/2nd level information hierarchy?
- Is one screen trying to show too much?
- How are completed/archived items handled?

Each persona classifies feedback as:
- Red: Must fix (Critical)
- Yellow: Recommended fix

Output: `docs/planning/v1_review.md`

---

## Step 3: Planning Finalization
Apply all Red + valid Yellow items, self-verify.
Output: `docs/planning/FINAL_plan.md`

---

## Step 4: Design
A) Figma (MCP tools)  B) Skip to code (step 7)  C) Full design flow

---

## Step 5: Design Review (AI Multi-Persona)

AI performs review from 4 expert perspectives:

### Persona 1: UI/Visual Expert (Senior, 8yr)
- Visual completeness and polish
- Color palette consistency and contrast
- Typography hierarchy and readability
- Spacing, alignment, and visual rhythm

### Persona 2: UX/Interaction Expert (Senior, 7yr)
- User flow smoothness and intuitiveness
- Touch target sizes (min 44x44pt)
- Interaction feedback (loading, success, error states)
- Navigation patterns and information architecture

### Persona 3: Consistency/Accessibility Expert (Mid, 4yr)
- Font/color/corner-radius consistency across screens
- WCAG accessibility compliance
- Color contrast ratios
- Screen reader compatibility considerations

### Persona 4: Planning Alignment Expert (Mid, 3yr)
- Are all planned features reflected in the design?
- Are there features in the design NOT in the plan?
- Screen-by-screen comparison with planning doc
- Reverse feedback: if missing screens found, update FINAL plan

Output: `docs/design/design_review.md`

---

## Step 6: Design Finalization
Apply review feedback, repeat if needed.
Output: `docs/dev/dev_brief.md`

---

## Step 7: Dev Spec Discussion (AI Multi-Persona)

AI discusses from 2 expert perspectives:

### Persona 1: Senior Developer (Architecture)
- Tech stack selection and justification
- Architecture patterns (layered, feature-based, etc.)
- Cost optimization strategies
- Code quality principles integration

### Persona 2: Server Developer
- Serverless vs BaaS comparison
- Free tier scope analysis (Firebase Spark, Supabase Free, etc.)
- Data structure design (NoSQL/SQL)
- Authentication strategy

Include: tech stack table, data structure, folder structure,
implementation order, timeline, cost comparison.
Cost checklist: Firebase Spark / Supabase Free / Cloudflare Workers Free
Output: `docs/dev/dev_spec.md`

---

## Step 8: Dev Guide
Text handling, color/font, API design, coding conventions as needed.
Output: `docs/dev/` folder

---

## Step 9: Implementation
Order: setup -> models -> pure logic -> protocols -> services -> store -> main UI -> detail UI -> components -> integration

### Implementation Self-Review (after each feature)
AI reviews from senior developer perspective:
- Does it match the planning doc?
- Any performance issues?
- Accessibility met?
- Error handling adequate?
- Pure functions: business logic separated from side effects?
- Modularization: file under 300 lines, split by feature?
- SRP: each function/class has one role?
- SOLID: protocol-based abstraction, dependency injection?

---

## Change Management (Required)
NEVER modify code directly. Always update docs first.

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
