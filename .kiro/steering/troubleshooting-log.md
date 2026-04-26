---
inclusion: auto
---

# Troubleshooting Log

This file records issues discovered during development and their solutions.
AI must always reference this log before writing code to avoid repeating known issues.

## How to Use

### When Reading (Always)
- Before writing any code, check if a relevant pattern/issue exists here
- Apply known solutions proactively, do not repeat past mistakes
- If a similar issue was solved before, follow the established pattern

### When Writing (After fixing a bug or discovering a pattern)
Add a new entry using this format:

```
## [Issue Number]. [Short Title]

### Problem
[What went wrong and how it manifested]

### Root Cause
[Why it happened]

### Solution
[How it was fixed, with code example if applicable]

### Prevention
[Rule to follow to avoid this in the future]
```

---

## Issue Log

(Issues will be added here as they are discovered during development.)

<!-- Example entry:

## 1. State not updating after async call

### Problem
UI did not reflect new data after API call completed.

### Root Cause
State update was not dispatched on the main thread.

### Solution
Wrapped state update in main thread dispatch:
```
DispatchQueue.main.async { self.items = newItems }
```

### Prevention
All state updates after async operations must be dispatched on main thread.
-->

