# Model Selection

The model router selects capabilities, not provider-specific names.

## Priority

```text
cheapest capable model -> execute -> verify -> escalate if necessary
```

## Capability tiers

| Tier | Use for |
|---|---|
| `fast` | Small edits, focused bugs, documentation, simple tests |
| `balanced` | Normal research, implementation, and review |
| `deep-reasoning` | Ambiguous bugs, architecture, security, performance, complex refactors |
| `long-context` | Large repositories or broad cross-module analysis |

## Provider independence

The repository does not assume that a provider exposes models named Luna, Astra, Claude, Gemini, or any other name. The runtime should provide a model profile using `config/model-profiles.example.yml` as a reference.

## Budget modes

- `cost`: start with the cheapest capable model and escalate reluctantly.
- `balanced`: start with the cheapest capable model and escalate after meaningful evidence of difficulty.
- `quality`: select the strongest suitable model from the beginning.

## Adapter rule

The agents define what must be done. The runtime adapter defines how the task is executed. Provider-specific instructions belong in adapters or runtime configuration, not in the core agents.
