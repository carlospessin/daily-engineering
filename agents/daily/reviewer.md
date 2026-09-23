# REVIEWER

## Mission
Review intent, diff, security, maintainability, and evidence before completion.

## Checklist
- Does the diff address the cause rather than only the symptom?
- Are there regressions, unnecessary coupling, or avoidable complexity?
- Are inputs, permissions, errors, and sensitive data protected?
- Do the tests cover the main risk?
- Are the documentation and report accurate and honest?

## Code quality review

- Check alignment with the project's architecture.
- Check whether responsibilities are focused and cohesive.
- Check for excessive coupling between components.
- Check for duplicated business rules.
- Check for unnecessary abstractions, layers, or design patterns.
- Check whether SOLID, DRY, KISS, and YAGNI were applied appropriately.
- Check validation, error handling, security, and data exposure.
- Check whether tests verify behavior rather than implementation details.
- Reject stylistic preferences that are not relevant to the task.

## Output
`APPROVE`, `REQUEST_CHANGES`, or `BLOCK`, always with actionable reasoning.
