# Daily Engineering Operating Model

## Roles

The agents are specialists, but they share context through artifacts. The coordinator must not silently rewrite decisions; it must update the artifact or request clarification.

## Gates

### Gate 0 — Context

Input: problem or technical question.

Output: project context, objective, constraints, and open questions.

### Gate 1 — Diagnosis ready

Output: reproducible problem, evidence, probable cause, scope, and proposed fix.

### Gate 2 — Change implemented

Output: focused diff, tests, and implementation handoff.

### Gate 3 — Verification complete

Output: test commands, results, evidence, and residual risk.

### Gate 4 — Review complete

Output: `APPROVE`, `REQUEST_CHANGES`, or `BLOCK`.

## Return policy

- Functional failure: `TESTER -> CODER`.
- Unclear scope or diagnosis: `TESTER -> RESEARCHER`.
- Security or architecture risk: `REVIEWER -> the responsible engineer`.
- Missing evidence: `REVIEWER -> the responsible stage`.

## Durable artifacts

Use these directories in the host project when durable documentation is needed:

```text
docs/discovery/
docs/specs/
docs/design/
docs/architecture/
docs/plans/
docs/testing/
docs/releases/
```

Never use the conversation as the only record of an important decision.
