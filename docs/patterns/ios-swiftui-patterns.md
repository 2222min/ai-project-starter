# iOS SwiftUI Performance Patterns

Real-world SwiftUI issues and solutions discovered during development.
Reference this before writing any SwiftUI code.

---

## 1. Debounce: Do NOT use Just(query)

### BAD
```swift
.onReceive(Just(query).debounce(for: .milliseconds(300), scheduler: RunLoop.main)) { value in
    debouncedQuery = value
}
```
- Just creates new publisher on every body re-eval, debounce resets each time

### GOOD: onChange + Task.sleep
```swift
@State private var searchTask: Task<Void, Never>?
.onChange(of: query) { _, newValue in
    searchTask?.cancel()
    searchTask = Task { @MainActor in
        try? await Task.sleep(for: .milliseconds(200))
        guard !Task.isCancelled else { return }
        // execute search
    }
}
```

---

## 2. Cache computed results in @State

### BAD: recompute in body
```swift
private var results: some View {
    let items = filter(query, store.items) // runs every body eval
}
```

### GOOD: cache in @State, update on change
```swift
@State private var searchResults: [Item] = []
// compute once on debounce completion
searchResults = filter(query, store.items)
```
WARNING: @State cache does not auto-update when store changes.
Add .onChange(of: store.items.count) to refresh.

---

## 3. Never swap ScrollView with if/else

### BAD: ScrollView destroyed and recreated
```swift
if condition { ScrollView { sectionA } }
else { ScrollView { sectionB } }
```

### GOOD: one ScrollView, swap content inside
```swift
ScrollView {
    VStack(spacing: 0) {
        if condition { sectionA }
        if !condition { sectionB }
    }
}
```

---

## 4. Keyboard focus: delay onAppear

```swift
// BAD: may be ignored before render completes
.onAppear { isSearchFocused = true }

// GOOD: slight delay ensures render is done
.onAppear {
    DispatchQueue.main.asyncAfter(deadline: .now() + 0.05) {
        isSearchFocused = true
    }
}
```

---

## 5. TextField: disable autocorrect for search
```swift
TextField("Search", text: $query)
    .autocorrectionDisabled()
    .textInputAutocapitalization(.never)
```

---

## 6. Touch area overlap: contentShape scale() danger

### BAD
```swift
.contentShape(Circle().scale(1.8)) // touch area bleeds into adjacent elements
```

### GOOD
```swift
.contentShape(Circle()) // no scale, use frame size only
// Section headers: block tap propagation
HStack { Text("Section"); Spacer() }
    .contentShape(Rectangle())
```
Rule: contentShape scale() must be <= 1.0 or not used at all.

---

## 7. TextEditor: always set foregroundColor explicitly
```swift
TextEditor(text: $memo)
    .foregroundColor(.primary) // MUST specify
    .scrollContentBackground(.hidden)
    .background(Color.gray.opacity(0.06))
```
Without explicit color, text may become invisible on light backgrounds.

---

## 8. Tab switching flicker: use opacity, not switch/if

### BAD: view destroyed/recreated on tab change
```swift
Group { switch tab { case .a: ViewA(); case .b: ViewB() } }
```

### GOOD: pre-create all tabs, toggle opacity
```swift
ZStack {
    ViewA().opacity(tab == .a ? 1 : 0)
    ViewB().opacity(tab == .b ? 1 : 0)
}
.animation(.none, value: tab)
```
Tab switch should have NO animation. Local icon animation only.

---

## 9. iOS 26 Liquid Glass: toolbar auto-styling

NavigationStack toolbar items get liquid glass automatically in iOS 26.
toolbarBackground cannot override individual item glass.

### Solution: replace NavigationStack toolbar with custom header
```swift
VStack(spacing: 0) {
    HStack { /* custom header buttons */ }
        .padding(.horizontal, 16).padding(.vertical, 10)
        .background(Color.white)
    ScrollView { /* content */ }
}
.navigationBarHidden(true)
```

---

## 10. TextField placeholder visibility
```swift
// BAD: default placeholder may be invisible on light bg
TextField("placeholder", text: $value)

// GOOD: use prompt parameter
TextField("placeholder", text: $value,
    prompt: Text("placeholder").foregroundColor(.secondary))
    .foregroundColor(.primary)
```

---

## 11. Empty state centering in leading VStack
```swift
// In VStack(alignment: .leading), centered views need:
.frame(maxWidth: .infinity) // override parent alignment
```
multilineTextAlignment(.center) only affects text wrapping, not view position.

---

## 12. Wheel Picker: text visibility + min height
```swift
Picker("", selection: $value) {
    ForEach(items) { item in
        Text(item.label)
            .foregroundColor(.primary) // must specify
            .tag(item)
    }
}
.pickerStyle(.wheel)
.frame(width: 80, height: 150) // min 150 height for usability
.clipped()
```

---

## 13. glassEffect + Button gesture conflict
```swift
// BAD: interactive() steals touch from Button
.glassEffect(.regular.interactive(), in: .circle)

// GOOD: visual only, no interactive
.glassEffect(.regular, in: .circle)
```
Never use interactive() on elements that need tap handling.

---

## 14. Animation conflict: stagger + withAnimation

Do NOT combine .animation(value:) stagger with withAnimation on same view.
.animation may fire unexpectedly on body re-eval even when value unchanged.

### Solution
- Data change animation: explicit withAnimation { }
- View transition animation: .id(value) + .transition()
- Never overlap both on same view

---

## 15. onTapGesture vs Button in cards

### BAD: card-level onTapGesture steals button taps
```swift
HStack { Button { toggle() } label: { ... }; Text(title) }
    .onTapGesture { showDetail() } // steals checkbox tap
```

### GOOD: separate tap areas
```swift
HStack {
    CheckboxButton { toggle() } // independent button
    VStack { Text(title) }
        .frame(maxWidth: .infinity, alignment: .leading)
        .contentShape(Rectangle())
        .onTapGesture { showDetail() } // text area only
}
```
Rule: never put onTapGesture on parent when child has Button.

---

## 16. Bottom padding for tab bar
Last section in ScrollView needs .padding(.bottom, 24) minimum
to avoid content hiding behind tab bar.

---

## 17. Swipe + checkbox: remove duplicate interactions
If checkbox toggle exists, remove swipe-to-complete.
Leftover swipe code (offset, background) causes visual artifacts on state change.
