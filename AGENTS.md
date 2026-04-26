# Agent Instructions (Codex)

This project follows a 9-step AI app development methodology.

## 9-Step Development Flow

When user describes an app idea, execute this flow automatically:

1. **Planning Draft** -> docs/planning/v1_plan.md
   - Project overview, core features (v1 vs future), ASCII wireframes
   - Tech requirements (server free tier), data model, non-functional requirements

2. **Planning Review** (AI Multi-Persona) -> docs/planning/v1_review.md
   - Usability / Visibility / Readability experts
   - Red (must fix) / Yellow (recommended)

3. **Planning Finalization** -> docs/planning/FINAL_plan.md

4. **Design** (Figma / Skip to code / Full flow)

5. **Design Review** (UI/UX/Consistency/Planning alignment)
   - Reverse feedback: update FINAL plan if missing screens found

6. **Design Finalization** -> docs/dev/dev_brief.md

7. **Dev Spec Discussion** (cost $0 target) -> docs/dev/dev_spec.md
   - Tech stack, data structure, folder structure, implementation order
   - Cost checklist: Firebase Spark / Supabase Free / Cloudflare Workers Free

8. **Dev Guide** -> docs/dev/

9. **Implementation** (doc-based code generation + self-review)

Get user confirmation at each step before proceeding.

## Code Quality 4 Principles (Required for all code)

1. **Pure Functions**: Business logic as pure functions. Separate side effects.
   - Same input = same output. No external state mutation.
   - Store/ViewModel calls pure logic, applies results.

2. **Modularization**: Split by feature. Max 300 lines per file. Loose coupling.
   - domain/ depends on nothing (pure layer)
   - features/ never depend on each other

3. **Single Responsibility**: One function = one job.
   - View = rendering, Logic = computation, Store = state management

4. **SOLID**: Depend on Protocol/Interface. Inject concrete implementations.

## Folder Structure
```
src/
  app/              Entry point, routing
  core/components/  Shared UI components
  core/extensions/  Utilities, helpers
  data/store/       State management
  data/services/    External services
  domain/models/    Data models
  domain/logic/     Pure function business logic
  domain/protocols/ Abstractions
  features/         Per-screen/feature modules
```

## Data Flow
```
User Action -> View -> Store.method()
  -> domain/logic (pure) -> new state -> Store update -> UI re-render
```

## Change Management (Required)

**NEVER modify code directly. Always update docs first.**

```
Change request -> Analyze scope -> Update docs -> Modify code
```

| Change Type | Scope |
|------------|-------|
| Add feature | Plan -> Design -> Spec -> Code |
| Modify feature | Plan -> Design -> Code |
| UI change | Design -> Code |
| Bug fix | Verify plan -> Code only |

## Cost Minimization
- Server cost $0/month target (free tiers only)
- BaaS over custom implementation (Firebase/Supabase)
- v1 = core features only

## Self-Checklist
1. Business logic in pure functions?
2. File under 300 lines?
3. Each function does one thing?
4. Depends on abstractions, not concrete types?
5. Side effects separated from pure logic?
6. New file in correct folder?
