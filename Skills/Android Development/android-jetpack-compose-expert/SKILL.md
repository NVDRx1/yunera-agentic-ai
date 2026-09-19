---
name: android-jetpack-compose-expert
description: "Use for Compose state, navigation, and performance work."
metadata:
  source: "Adapted from sickn33/agentic-awesome-skills after review"
  source_url: "https://github.com/sickn33/agentic-awesome-skills"
---

# Android Jetpack Compose Expert

Use for production Compose architecture, lifecycle-aware screen state, side effects, type-safe navigation, and measured recomposition work. Do not use this skill as a substitute for inspecting the target project's actual AndroidX and Kotlin versions.

## Architecture

- Expose immutable screen state from a `ViewModel`, commonly as read-only `StateFlow`; keep mutable state private to its owner.
- Collect flows lifecycle-aware at the screen boundary. Pass state and explicit callbacks into child composables rather than passing a `ViewModel` down the hierarchy.
- Represent loading, content, empty, and recoverable error states deliberately. Keep retry actions explicit.
- Use one-shot events and durable screen state separately. Use explicit Compose effects for transient UI work such as navigation or snackbars.

## Navigation

- Keep route models small, serializable, and free of sensitive or oversized payloads. Pass an identifier, then load the detail data at its destination.
- Use the project's existing Navigation Compose approach; verify the installed version before proposing type-safe navigation APIs.
- Preserve meaningful back-stack behaviour and test system Back from detail, search, and settings contexts.

## Performance

- Measure before optimising. Use Android Studio tooling, tracing, or targeted benchmarks rather than guessing at recomposition cost.
- Hoist and stabilise state where it materially reduces unnecessary work. Use `remember` or `derivedStateOf` only where their invalidation behaviour is correct.
- Avoid expensive sorting, filtering, I/O, and object graph creation in composable bodies. Compute from stable inputs or move work to the appropriate state layer.
- Do not claim a type is stable or immutable unless its fields and mutation model genuinely meet that contract.

## Verification

1. Compile against the project’s actual dependency set.
2. Exercise normal, loading, empty, error, long-text, font-scale, RTL, and configuration-change paths relevant to the edited screen.
3. Run UI tests when present and inspect screenshots on a connected emulator/device before declaring visual or navigation behaviour verified.
4. For releases or APK delivery, follow `android-app-delivery` in addition to this skill.

## Common failures

- Recomposition loops caused by writing state during composition.
- ViewModels or navigation callbacks leaking into reusable leaf components.
- New navigation APIs copied without checking the installed AndroidX version.
- Overusing `remember`, which can preserve stale data when keys are wrong.
- Treating a successful build as proof of accessible or visually correct UI.

## Official references

- https://developer.android.com/develop/ui/compose/state
- https://developer.android.com/develop/ui/compose/side-effects
- https://developer.android.com/develop/ui/compose/performance
- https://developer.android.com/jetpack/compose/navigation
