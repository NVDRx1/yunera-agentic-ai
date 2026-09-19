---
name: android-cli
description: Use for Android SDK, device, emulator, and build work.
---

# Android CLI

Use this skill for the Android development stack: SDK components, Gradle-based project builds, physical devices, emulators, APK deployment, UI inspection, screenshots, Android Studio integration, and current Android documentation.

## Source and scope

This local skill is derived from the Google LLC `android/skills` repository, upstream commit `b1f707d90904129b5972b3cc6436b568583effe5` (2026-09-18), `devtools/android-cli`.

Use the official `android` CLI when it is present. It supports:

- SDK package management: `android sdk list`, `android sdk install`, `android sdk update`, and `android sdk remove`.
- Project creation and discovery: `android create` and `android describe`.
- Emulator control: `android emulator create|start|stop|list|remove`.
- Build, deployment, and launch: `android run`, `android install`.
- Device UI inspection: `android layout` and `android screen capture`.
- Current Android documentation: `android docs search` and `android docs fetch`.
- Android Studio integration: `android studio check`, `open-file`, `analyze-file`, `render-compose-preview`, and `version-lookup`.

## Safety boundary

Do not install or update the Android CLI, Android SDK packages, an emulator image, an APK, or any system-wide configuration without the user’s explicit approval for that action.

If the CLI is absent, state that clearly. The upstream installation command downloads and executes a remote installer; do not run it silently. First tell the user what it would change and request approval.

Do not use this skill to replace the existing Compose architecture, Compose foundations, or Android delivery skills. It complements them with concrete SDK/device/CLI execution.

## Project workflow

1. Inspect the project first: use its Gradle wrapper and existing build configuration. Do not impose a new project layout.
2. Before changing SDK packages or Gradle versions, identify the project’s declared `compileSdk`, `minSdk`, Android Gradle Plugin, and Kotlin/Compose dependencies.
3. Build with the project wrapper where available, such as `./gradlew assembleDebug` or the project’s documented task.
4. Use `android describe --project_dir=<path>` when available to locate build targets and artifacts.
5. Treat APK installation and launching as a separate side effect: obtain user approval when it targets a physical device or modifies an emulator state.

## Device and UI workflow

Before `android layout` or `android screen`, read `references/interact.md`.

- Prefer `android layout` to inspect accessible UI structure.
- Use `android layout --diff` to reduce noisy output after a change.
- If a WebView, image, or animation makes the layout unreliable, capture a screenshot and visually inspect it.
- Never interact with a device based solely on assumed coordinates; inspect the current UI first.

## Journey tests

Before evaluating an XML journey test, read `references/journeys.md`.

Evaluate each journey action in order, report a failure precisely, and do not turn a test-evaluation task into open-ended debugging unless requested.

## Documentation

For changing Android APIs, libraries, or platform behavior, prefer `android docs search` when installed. Its official knowledge base is a current source; do not rely only on stale model knowledge.

## Verification

For a build or delivery request, report only results actually produced by the executed build, device inspection, test, or deployment command. Include relevant artifact paths, version identifiers, and failure output when applicable.
