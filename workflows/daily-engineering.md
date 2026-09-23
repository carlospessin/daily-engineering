# Workflow: Daily Engineering

Use this workflow for bugs, technical questions, code investigations, small improvements, and tasks with a known scope.

## Default sequence

0. `agents/daily/model-router.md` — optional model selection.
1. `agents/daily/researcher.md`
2. `agents/daily/coder.md`
3. `agents/daily/tester.md`
4. `agents/daily/reviewer.md`

## Allowed shortcuts

- Pure investigation: `RESEARCHER` may finish without code.
- Confirmed diagnosis with no code change: `RESEARCHER -> REVIEWER`.
- Small, low-risk change: `RESEARCHER -> CODER -> TESTER`; `REVIEWER` remains mandatory before completion.

## Return rule

If a test fails, `TESTER` must record reproduction steps, expected result, actual result, and evidence, then return the task to `CODER`. The cycle ends only when the test passes or the user explicitly accepts the limitation.

## Token policy

Load only the current agent and the files needed for the current hypothesis. Use the compact handoff format unless the issue involves architecture, security, production data, or an incident.

## Model policy

When enabled, `MODEL ROUTER` selects the cheapest capable model before the first task agent. It may escalate after evidence of difficulty, but it never bypasses testing or review.
