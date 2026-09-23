# Token-Efficient Operation

This framework uses progressive disclosure: load only what is necessary for the current decision.

## Coordinator rules

1. Read only `AGENTS.md` and the user's request first.
2. Classify the task as `BUG`, `RESEARCH`, `BUILD`, `TEST`, or `REVIEW`.
3. Load only one primary agent at a time.
4. Search project files surgically; never dump entire directories.
5. Prioritize the user-mentioned file, symbol definition, related tests, and directly involved configuration.
6. After a handoff, discard the previous agent prompt and retain only the compact summary.
7. Do not reload instructions already applied in the current stage.
8. Avoid long narratives. Use facts, decisions, actions, and evidence.
9. Do not invoke unrelated agents.
10. For small tasks, roles may be combined, but preserve `TESTER` and `REVIEWER` for code changes.

## Minimal routing

| Intent | Initial agent | Next |
|---|---|---|
| Research or bug | `RESEARCHER` | `CODER` or `REVIEWER` |
| Implementation | `CODER` | `TESTER` |
| Failing test | `TESTER` | `CODER` |
| Review | `REVIEWER` | responsible agent |

## Compact handoff

Use at most 12 lines unless risk is elevated:

```text
STATUS: <done|blocked|needs-review>
OBJECTIVE: <one line>
FACTS: <up to 3 items>
DECISION: <one line>
CHANGED: <files>
TESTS: <commands and result>
RISK: <none or description>
NEXT: <agent and action>
```

Use the full contract only for architecture, security, production data, incidents, or difficult decisions.

## Expand context only when

- the current hypothesis does not explain the evidence;
- a test or build fails;
- the change crosses module boundaries;
- there is a security, data, or production risk;
- the user requests a complete analysis.

## Waste prohibition

Do not list every project file, repeat the user's request, copy existing documents, or load agents that will not participate in the current stage.
