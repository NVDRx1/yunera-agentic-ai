# Android journey evaluation

A journey is an XML test specification made of ordered `<action>` elements. The journey source is authoritative: if the app does not meet its stated action or expectation, the journey fails.

## Evaluation

- Evaluate actions sequentially and exactly as written.
- Split compound actions into individually evaluated sub-actions.
- For `check` or `verify` actions, inspect the current UI without unrelated interaction.
- If an action is malformed or cannot be performed as specified, report the failure and stop.
- If the app exits, crashes, or freezes, stop and report a failed journey.

## Report

Produce a Markdown report with the journey name; each action marked pass or fail; commands actually executed; relevant screenshot paths; and specific observations. Do not claim success unless every action was evaluated successfully.
