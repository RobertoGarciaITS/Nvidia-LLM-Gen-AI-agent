# Agent Configuration Workspace

## Configuration model
```yaml
agent:
  id: example-agent
  objective: ""
  model:
    provider: ""
    name: ""
    temperature: null
  instructions: []
  context: []
  tools: []
  state: {}
  memory: {}
  retrieval: {}
  guardrails: {}
  evaluation: {}
```

Learn and test each component independently before integrating a complete agent.

## Planned artifacts
- `agent.schema.yaml`
- `model-registry.yaml`
- `tool-contract.schema.yaml`
- `examples/`
- `evaluations/`
