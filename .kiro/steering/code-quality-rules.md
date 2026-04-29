---
inclusion: auto
---

# Code Quality Rules

Always active when generating or modifying code.

Canonical shared rule: `docs/agents/code-quality.md`

## 1. Pure Functions (Required)
- Business logic MUST be pure functions
- Same input = same output. No external state mutation
- Store/ViewModel calls pure logic and applies results
- Side effects (notifications, network, DB) separated from pure logic

```
GOOD: filterActiveTodos(todos) -> new array (no state change)
BAD:  filterActiveTodos() -> self.filteredList changed + UI update (side effects mixed)
```

## 2. Single Responsibility (Required)
- One file = one role. Split if over 300 lines
- One function = one job. Split if name contains "and"
- View = rendering, Logic = computation, Store = state management

```
GOOD: validateTitle(title), saveTodo(todo), sendNotification(todo)
BAD:  validateAndSaveTodoAndNotify(title)
```

## 3. Protocol/Interface DI (Required)
- Services define Protocol/Interface, inject concrete implementation
- Store/ViewModel depends on abstractions, not concrete types

```
GOOD: class Store { constructor(private svc: NotificationService) }
BAD:  class Store { private svc = new FirebaseNotificationService() }
```

## 4. Modularization
- Split by feature. Minimize inter-module dependencies
- Extract common utilities into separate modules

## Folder Structure (Layered + Feature-based)
```
src/
  app/              Entry point, routing
  core/components/  Shared UI components
  core/extensions/  Utilities, helpers
  data/store/       State management (calls pure logic -> applies results)
  data/services/    External services (Protocol/Interface implementations)
  domain/models/    Data models
  domain/logic/     Pure function business logic
  domain/protocols/ Abstractions (Protocol/Interface)
  features/         Per-screen/feature modules
```

## Dependency Direction (Never violate)
```
features --> domain <-- data
    |            ^
    +---> core --+
app --> everything
```
- domain depends on nothing (pure layer)
- features never depend on each other (communicate via Store)

## Data Flow
```
User Action -> View -> Store.method()
  -> domain/logic (pure function) -> new state
  -> Store update -> UI auto re-render
```

## Self-Checklist (after writing code)
1. Business logic in pure functions?
2. Each file under 300 lines?
3. Each function does one thing?
4. Function name tells its role?
5. Depends on abstractions, not concrete types?
6. New file in correct folder?
7. Side effects separated from pure logic?
8. Can add features without modifying existing code?

## Adding New Features
1. Create features/[name]/ folder
2. Models -> domain/models/
3. Business logic -> domain/logic/ (pure functions)
4. External service -> domain/protocols/ + data/services/
5. Store extension -> data/store/
6. Shared UI -> core/components/
