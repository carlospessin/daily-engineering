# Daily Engineering Agents

Markdown instructions for four software engineering agents:

- `RESEARCHER`: investigates the problem and identifies the likely cause.
- `CODER`: implements the smallest safe change.
- `TESTER`: verifies the change and checks for regressions.
- `REVIEWER`: reviews the diff, tests, risks, and maintainability.

An optional `MODEL ROUTER` selects the cheapest capable model for the task and escalates when necessary.

## Workflow

```text
MODEL ROUTER -> RESEARCHER -> CODER -> TESTER -> REVIEWER
```

If a test fails, `TESTER` returns the task to `CODER` with reproduction steps and evidence.

## Installation

Clone the repository into the project:

```bash
git clone https://github.com/carlospessin/daily-engineering.git .daily-engineering
```

Copy `AGENTS.md` to the project root or configure the coding agent to load it.

If the project already has an `AGENTS.md`, keep it and add this block:

```markdown
## Daily Engineering Team

For bugs, investigations, implementation tasks, testing, and reviews, use:

`.daily-engineering/workflows/daily-engineering.md`

Available agents:

- `.daily-engineering/agents/daily/model-router.md`
- `.daily-engineering/agents/daily/researcher.md`
- `.daily-engineering/agents/daily/coder.md`
- `.daily-engineering/agents/daily/tester.md`
- `.daily-engineering/agents/daily/reviewer.md`

Load only the agent required for the current stage.
Follow the host project's conventions before the generic team instructions.
```

## Usage

Submit a task in natural language. Example:

```text
Investigate why deleting an expense shows "No records found" before the success message. Fix it, add regression coverage, and review the change.
```

For a normal task, use the complete workflow. For research-only tasks, stop after `RESEARCHER`. For an already diagnosed task, start with `CODER`.

## Token usage

- Load `AGENTS.md` first.
- Load only the current agent.
- Read only files related to the current task.
- Do not dump the entire repository.
- Use compact handoffs for normal tasks.
- Load the full handoff contract only for high-risk work.

Details: [`docs/TOKEN_EFFICIENCY.md`](docs/TOKEN_EFFICIENCY.md).

## Structure

```text
AGENTS.md
agents/daily/                     Agent instructions
contracts/agent-handoff.md        Handoff format
contracts/definition-of-done.md   Completion checklist
docs/AGENT_ROUTER.md              Agent selection
docs/CONTRIBUTING.md              Contribution rules
docs/OPERATING_MODEL.md           Workflow rules
docs/TOKEN_EFFICIENCY.md          Token rules
config/model-profiles.example.yml Model profile format
templates/problem-report.md       Investigation template
templates/test-report.md          Test report template
workflows/daily-engineering.md    Workflow definition
```

## Completion criteria

A task requires:

- confirmed or documented diagnosis;
- focused code changes;
- relevant tests;
- recorded verification results;
- review decision;
- documented limitations or residual risks.

## License

MIT. See [`LICENSE`](LICENSE).
