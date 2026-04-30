---
inclusion: auto
---

# Figma-Code Reflection Rules

Always active for design and UI implementation work.

## Canonical Rule

Follow `docs/agents/figma-code-reflection.md`.

## Required Behavior

- Treat Figma MCP as the default design source.
- Record Figma file URL, screen node IDs/URLs, component node IDs/URLs, and code mapping in `docs/design/figma_reference.md`.
- If UI code changes, update the design docs and Figma reference before or together with code.
- If Figma changes, update `docs/design/figma_reference.md`, then update design/dev docs, then update code.
- For design or UI judgment, use `docs/agents/ux-design-laws.md`.
- Use easy status terms in documents:
  - `반영 완료 기록`
  - `반영 대기 항목`
- If Figma MCP is unavailable, record the reason and next action under `반영 대기 항목`.
