# Contribuindo

Each agent must have one mission, clear inputs, a verifiable output, and a return rule. Instructions should be short and imperative.

When adding an agent:

1. Update `docs/AGENT_ROUTER.md`.
2. Define when it enters and where it receives context from.
3. Define the artifact it produces.
4. Define its gate and return conditions.
5. Avoid repeating global rules from `AGENTS.md`.
6. Add an example only when it reduces ambiguity.

Before accepting a change, check whether it increases permanent context unnecessarily.
