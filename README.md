# AI Project Starter Template

> Kiro, Claude, Codex, Cursor, Copilot - all AI tools supported with one template.

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

### Steering (Rules)
- **app-development-flow.md**: 9-step dev flow (plan->review->design->spec->implement)
- **code-quality-rules.md**: Pure functions, SRP, DI, modularization

### Hooks (Automation - Kiro only)
- **doc-first-reminder**: Prevents code changes without updating docs first
- **code-quality-check**: Verifies code quality after every writructions.md all contain the same methodology.

## 9-Step Flow
1. Planning Draft
2. Planning Review (AI Multi-Persona)
3. Planning Finalization
4. Design
5. Design Review
6. Design Finalization
7. Dev Spec Discussion
8. Dev Guide
9. Implementation

## Core Philosophy
- Start light, iterate fast
- Server cost $0/month (free tiers only)
- AI multi-persona review for quality
- Docs = source of truth. Update docs before code.
- Pure functions, single responsibility, DI, modularization
