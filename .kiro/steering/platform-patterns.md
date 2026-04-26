---
inclusion: auto
---

# Platform-Specific Patterns

This project has platform-specific pattern guides in `.kiro/steering/platforms/`.
When the tech stack is decided (Step 7), copy the relevant platform file
to `.kiro/steering/` so it becomes auto-included.

## Available Platforms
- `platforms/ios-swiftui-patterns.md` — SwiftUI performance patterns & gotchas
- `platforms/flutter-patterns.md` — Flutter patterns (template)
- `platforms/android-compose-patterns.md` — Jetpack Compose patterns (template)
- `platforms/react-native-patterns.md` — React Native patterns (template)
- `platforms/web-react-patterns.md` — React/Next.js patterns (template)

## How to Activate
After deciding the tech stack, copy the relevant file:

```bash
# Example: iOS project
cp .kiro/steering/platforms/ios-swiftui-patterns.md .kiro/steering/
```

Or for Kiro, just reference it in conversation:
`#ios-swiftui-patterns`
