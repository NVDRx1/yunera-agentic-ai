# Android device interaction

Run `android layout --help` and `android screen --help` before unfamiliar device work.

## Inspect first

`android layout` provides a structured UI dump. Prefer it as the primary inspection method; use `android layout --diff` after actions to isolate actual changes. Typical fields include `text`, `resourceId`, `contentDesc`, `interactions`, `state`, `bounds`, `center`, and `off-screen`.

If WebViews, animation, or rendered imagery make the UI dump incomplete, use `android screen capture -o <path>` or `android screen capture --annotate -o <path>`. Visually examine the resulting PNG before acting.

## Input

Use `adb shell input` only after inspecting the current UI and confirming the intended target. Ensure a text field is focused before entering text. Escape shell metacharacters and represent spaces as `%s` for Android text input.

- Never act on stale coordinates after a screen transition.
- Scroll slowly when an inspected element is scrollable.
- Wait briefly for asynchronous content, then use `layout --diff` to assess the observed change.
