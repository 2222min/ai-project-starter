# AI Project Starter Template

> Kiro, Claude, Codex, Cursor, Copilot - all AI tools supported.

## Quick Start
```bash
cp -r ~/Desktop/ai-project-starter ~/Desktop/my-new-project
```
Then tell any AI tool your app idea. The 9-step flow runs automatically.

## AI Tool Config Map

| AI Tool | Config File | Auto-applied |
|---------|------------|-------------|
| Kiro | .kiro/steering/*.md + .kiro/hooks/*.hook | Yes |
| Claude | CLAUDE.md | Yes |
| Codex | AGENTS.md | Yes |
| Cursor | .cursorrules | Yes |
| Copilot | .github/copilot-instructions.md | Yes |

## What is Included

### Steering (Rules - Kiro)
- **app-development-flow.md**: 9-step flow with detailed AI personas
- **code-quality-rules.md**: Pure functions, SRP, DI, modularization

### Hooks (Automation - Kiro)
- **doc-first-reminder**: Prevents code changes without updating docs first
- **code-quality-check**: Verifies code quality after every write

### Agent Instructions (All tools)
CLAUDE.md, AGENTS.md, .cursorrules, copilot-instructions.md
all contain the same full methodology including AI personas.

## 9-Step Flow with AI Personas

| Step | AI Personas |
|------|------------|
| 1. Planning Draft | - |
| 2. Planning Review | Usability + Visibility + Readability experts |
| 3. Planning Finalization | - |
| 4. Design | - |
| 5. Design Review | UI/Visual(8yr) + UX(7yr) + Accessibility(4yr) + Planning(3yr) |
| 6. Design Finalization | - |
| 7. Dev Spec | Senior Architect + Server Developer |
| 8. Dev Guide | - |
| 9. Implementation | Senior Dev self-review |

## Core Philosophy
- Start light, iterate fast
- Server cost $0/month (free tiers only)
- AI multi-persona review for quality
- Docs = source of truth. Update docs before code.
- Pure functions, single responsibility, DI, modularization
