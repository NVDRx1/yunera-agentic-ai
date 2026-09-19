---
name: android-app-delivery
description: "Use when building Android apps. Package and verify safely."
---

# Android App Delivery

## Standing rules

- Build, package, sign, or send an installable only when the user explicitly asks for it. Use a debug APK for testing unless a release signing request is explicit.
- Treat supplied artwork as visual reference only unless its licence and clean source are verified. Never incorporate a visible watermark, stock-preview mark, or copied geometry into the app.
- Keep branding assets local and original. Prefer Android XML vector drawables for simple marks: they are crisp at launcher sizes and add no third-party image dependency.
- Do not claim on-device testing unless a device/emulator was actually connected and exercised. Package inspection and signature verification are separate from runtime validation.
- For reference-style Android apps, keep app-wide preferences in Settings and reserve the Home screen for the primary lookup journey. Keep explanatory or marketing-style summaries off Home unless they directly support the next lookup action; do not duplicate a global control in both places; keep data integrity/offline state compact in Settings unless it blocks a primary action.
- Treat every non-Home screen as a navigation destination: provide an explicit, visible Back control in its header and make the system Back action return to its meaningful origin. Track the origin when opening detail content so Back returns to the prior search or browse context rather than always Home.
- For bundled legal/reference data, distinguish a local integrity check from a remote refresh. A launch progress indicator may say it is loading or checking the bundled dataset, but must never imply a download without a configured source and network action.

## Procedure

1. Inspect the app manifest, existing resource layout, module build configuration, repository status, and any project delivery constraints before modifying branding or producing an APK.
2. For an original launcher icon, create:
   - `res/drawable/ic_launcher_foreground.xml` with the vector mark;
   - `res/drawable/ic_launcher_background.xml` and named colour resources;
   - `res/mipmap-anydpi-v26/ic_launcher.xml` as an adaptive icon;
   - `res/mipmap-anydpi-v33/ic_launcher.xml` with `monochrome` when compiling against API 33 or newer.
   Set both `android:icon` and `android:roundIcon` to `@mipmap/ic_launcher` in the application manifest.
3. For UI work that changes theme state or date-dependent content, inspect the runtime state flow before editing: persisted/manual versus system theme selection, every root/window surface, and the selection value passed into repository queries. When the product promises an app-controlled theme, never derive initial mode from `Configuration.uiMode`: default to a defined app mode, persist only the app’s explicit selection, apply an explicit light/dark activity theme before UI creation, and recreate after a toggle. When a redesigned build must reopen in the stated default mode after an update, migrate to a versioned preference key with that default rather than reusing an obsolete Boolean; retained prior state silently defeats the new default. Make the initial date explicit from the device-local current date rather than using a display-only “current” sentinel.
4. When applying a manual light/dark theme, set the palette consistently on the activity window, decor/root background, status bar, and navigation bar; set light system-bar icon flags in light mode. Disable Android Force Dark on API 29+ (`android:forceDarkAllowed=false`) or a dark system theme can transform an intended white manual palette back to black. Put API-gated style items in version-qualified resources (for example, `values-v27/` for light navigation bars and `values-v29/` for Force Dark) to keep min-SDK lint clean. Define a base NoActionBar theme and make every version-qualified `AppThemeLight`/`AppThemeDark` variant inherit it: a qualified style replaces the base style at runtime, so an attribute-only override can silently restore the platform action bar and duplicate the app’s own heading. When visual feedback reports duplicate branding, inspect the system window title separately from in-content text; remove the action bar at the theme level rather than deleting useful in-app hierarchy. An activity theme alone may leave system or decor surfaces in the old palette.
5. For data-heavy offline apps, load and validate the bundled dataset off the UI thread. Show an indeterminate launch progress state until the repository is ready, then render the requested screen. In framework-View screens assembled dynamically, compose all header and body children before attaching the finished scroll/root view with `setContentView`; attaching header-first can leave later body children unmeasured on some device render paths. Follow attachment with a root layout request and invalidation, and keep the safeguard independent of optional cards so removing or rearranging a card cannot remove it. If a visual report shows a header with an empty body, reproduce it with a clean install, assert body text in the UI hierarchy, and inspect a screenshot before diagnosing data loss; repeat the check after selecting the explicit persisted theme reported by the user. Search locally on each query change with no artificial debounce unless profiling proves the corpus needs one; cancel only obsolete queued work.
6. If a future refresh source is not yet configured, expose its state honestly in Settings and keep the control non-destructive: do not add a placeholder endpoint or make a network request. Stage a release manifest contract with a pinned public key, asset size/schema, SHA-256, atomic apply, and last-known-good rollback before enabling remote updates. Do not add `INTERNET` merely for a future feature unless the user has explicitly approved the permission and an update endpoint exists. See [remote dataset refresh](references/remote-dataset-refresh.md).
7. Use the repository's configured user-local JDK and Android SDK. During a cohesive UI iteration, run one focused compile after the edits rather than repeatedly packaging or exercising the full suite. If the user will perform device testing, stop after that focused check unless an APK is explicitly requested. Before copying or sending an APK, run unit tests, Android lint, the requested assembly target, and package/signature inspection.
8. If Gradle fails because the project directory contains a colon, stage a source copy at a path without colons. Refresh that staging directory from the source repository while the shell is outside the staging directory; deleting the active working directory makes the synchroniser lose its current path. Invoke Gradle with the completed staging directory as its *working directory*, not merely as an absolute wrapper path; Gradle resolves its project from the current working directory.
9. After validation, commit only the intended cohesive source changes. Check the repository status immediately before and after the commit; if unrelated changes are present, leave them untouched and report them rather than absorbing them into the delivery commit. When delivering an APK for the committed correction while unrelated work remains, populate the colon-safe staging tree from `git archive HEAD` rather than copying the dirty working tree; this prevents the artifact from silently including changes that were deliberately excluded from the delivery commit.
10. Copy the resulting APK to the explicitly requested project output location, then verify the exact file independently:
   - use `aapt2 dump packagename` and `aapt2 dump badging` for package ID, label, SDK levels, permission declarations, and launcher resource;
   - use `aapt2 dump resources` to confirm the adaptive icon resources were compiled;
   - run `apksigner verify --verbose --print-certs` with the build JDK on `PATH` to validate signing;
   - calculate SHA-256 with `sha256sum` and report it with the delivery path.
11. Deliver the actual APK as `MEDIA:/absolute/path/to.apk`, identify debug versus release signing, state test/lint/build results, and limit caveats to unperformed checks that materially matter. When delivering a corrective APK intended to replace an installed build, increment `versionCode` (and the user-visible version) before assembly so Android accepts it as an upgrade. Never describe an APK as containing a change until its staged source was refreshed, assembled, and inspected after that change.

## Verification pitfalls

- Do not infer icon packaging from source files alone; inspect the assembled APK because manifest and resource-merging errors can leave the old launcher resource in place.
- Export `JAVA_HOME` and prepend `$JAVA_HOME/bin` before running `apksigner`; the Android build-tools script delegates to `java` and otherwise may fail after a successful build.
- Refresh staged sources before every staged build and clear staged build outputs when Gradle reports misleading up-to-date state; stale outputs can validate code that is no longer in the repository.
- Keep raw official legal/reference data separate from branding or APK claims: do not represent a test APK as containing a corpus until it has actually been parsed and packaged.
- Do not claim theme rendering is visually verified from build, lint, or package checks; require an exercised emulator/device for that claim because framework-window and OEM rendering are runtime behaviour.
- For a reported alignment change, preserve controls not named by the request and verify the exact installed screen with a screenshot; hierarchy text proves presence, not spacing, clipping, or touch-target layout.

See [launcher icon design](references/launcher-icons.md) for a compact vector-art direction and adaptive-icon checks.
