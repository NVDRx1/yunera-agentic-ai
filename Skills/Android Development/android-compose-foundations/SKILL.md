---
name: android-compose-foundations
description: "Use when building or reviewing Compose UI foundations."
metadata:
  source: "Adapted from krutikJain/android-agent-skills after review"
  source_url: "https://github.com/krutikJain/android-agent-skills"
---

# Android Compose Foundations

Use this for Jetpack Compose layouts, component structure, modifiers, theming, and UI refinement. Load `android-app-delivery` as well when the task includes packaging, APK work, or runtime delivery.

## Workflow

1. Identify the surface: Compose, Views, or a deliberate interoperability boundary. Inspect the project SDK, Compose BOM, Material version, navigation stack, and existing theme before proposing APIs.
2. Build from reusable design tokens and stable component APIs. Keep leaf components stateless: receive rendered state and event lambdas, not navigation or business logic.
3. Use layout patterns that remain usable with long/localized text, font scaling, RTL, narrow widths, and system insets. Avoid fixed dimensions unless their constraint is intentional.
4. Add meaningful semantics, visible focus order, sufficient contrast, and touch targets appropriate to Android platform guidance. Do not make colour the only carrier of information.
5. Validate the requested behaviour with appropriate tests, UI-hierarchy checks, and screenshots on a real emulator/device when visual fidelity is claimed.

## Guardrails

- Prefer predictable rendering and measured performance over animation, abstraction, or micro-optimisation.
- Keep state at the lowest caller that must control it; model durable UI state separately from transient events.
- Keep `LaunchedEffect`, `DisposableEffect`, and imperative work explicit. Do not perform side effects in a composable body.
- Do not mix Compose and View ownership without declaring the boundary and lifecycle responsibility.
- Do not imitate web UI conventions where Android platform patterns, back navigation, and system integration are expected.
- Check current official Android and AndroidX documentation before using version-sensitive Compose APIs.

## UX review checklist

- One clear primary action and readable visual hierarchy per screen.
- Loading, empty, error, disabled, and success states are intentional and reachable.
- Back returns to the meaningful prior context.
- Layout survives 200% font scale, long strings, RTL, and a narrow phone width.
- Screenshot review verifies spacing, clipping, colour surfaces, and touch-target placement; hierarchy text alone does not.

## Official references

- https://developer.android.com/develop/ui/compose
- https://developer.android.com/develop/ui/compose/layouts/basics
- https://developer.android.com/develop/ui/compose/modifiers
- https://developer.android.com/develop/ui/compose/designsystems/material3
