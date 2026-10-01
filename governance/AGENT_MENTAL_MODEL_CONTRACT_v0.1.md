# Agent Mental Model Contract

**ID:** NVIDIA-AGENT-MENTAL-MODEL-CONTRACT-001  
**Version:** 0.1  
**Status:** ACTIVE  
**Date:** 2026-09-30  
**Scope:** NVIDIA LLM / GenAI Agent Learning Repository

## 1. Purpose

This contract establishes the canonical mental model used in this repository to explain how an AI agent is configured, isolated, operated, observed, and connected to inference, tools, and memory.

It is a **project learning and architecture contract**. It defines vocabulary, conceptual boundaries, flows, and invariants for future lessons, labs, diagrams, code reviews, and architectural discussions.

It is not a substitute for vendor implementation documentation. Product-specific behavior must be verified against the relevant official source before being promoted to a validated implementation claim.

## 2. Canonical components

### 2.1 User

The user defines the objective, task, context, and restrictions, and receives the result or artifact.

### 2.2 NemoClaw — lifecycle and configuration

Mental-model role:

```text
NemoClaw
├── configures Agent
├── configures OpenShell
├── configures Provider
├── configures Policies
├── configures Credentials
└── manages Lifecycle
```

Canonical interpretation:

> NemoClaw = assembly/configuration + lifecycle management layer.

NemoClaw MUST NOT be described as the LLM that performs neural inference.

### 2.3 OpenShell — security and execution boundary

OpenShell is represented as the security and execution boundary around agent activity.

Conceptual controls:

```text
OpenShell
├── Sandbox
├── Policy Engine
├── Network Gateway
├── Credential Management
├── Filesystem Control
├── Process Control
└── Inference Routing
```

Every privileged or external action SHOULD be reasoned about as a request evaluated against an explicit execution/security policy.

### 2.4 AI Agent — orchestration layer

The agent is the component that receives the objective and orchestrates work.

Core responsibilities:

- understand the objective;
- maintain state and context;
- plan;
- decide the next action;
- consult memory;
- select tools;
- request inference when reasoning is required;
- process observations;
- determine task completion.

Canonical loop:

```text
OBSERVE → REASON → DECIDE → ACT → OBSERVE
```

### 2.5 Tools — operational capabilities

Tools represent capabilities the agent can invoke, such as:

- shell;
- Git;
- filesystem;
- browser;
- APIs;
- MCP;
- Python;
- database queries;
- custom functions.

A tool invocation does not inherently require an LLM inference call.

### 2.6 Memory

Memory MUST NOT be treated as a single database.

The project mental model distinguishes:

- session / working memory;
- structured memory;
- semantic memory;
- relational memory;
- artifact / persistent memory.

Technical persistence/retrieval patterns may include:

```text
SQL          → structured records/state
Vector / RAG → semantic retrieval
Graph        → entities and relationships
```

### 2.7 Model / inference provider

The model/provider is responsible for model inference.

Canonical flow:

```text
Agent
  ↓ inference request
OpenShell
  ↓ routing / policy / credentials
Provider
  ↓
Model
  ↓ inference
Response
  ↑
Agent
```

The model MUST NOT be conflated with the agent, its tools, its memory, or its business workflow.

### 2.8 NeMo Agent Toolkit — instrumentation and agent-engineering layer

The project represents NeMo Agent Toolkit as a cross-cutting layer for:

- integration;
- instrumentation;
- profiling;
- evaluation;
- workflow support;
- observability hooks.

It MUST NOT be conflated with NemoClaw.

### 2.9 Observability

Observability systems receive execution telemetry such as:

- traces and spans;
- LLM calls;
- tool calls;
- token usage;
- latency;
- errors;
- metadata;
- evaluation results.

Examples used in this repository may include LangSmith, Phoenix, Langfuse, and OpenTelemetry.

Observability systems are conceptually observers of execution; they are not the agent itself.

## 3. Canonical connection model

```text
USER
  │ Goal / Prompt
  ▼
NemoClaw
  │ lifecycle / configuration
  ▼
OpenShell
  │ sandbox / policies
  ▼
AI AGENT
  │
  ├──────────────► TOOLS
  │                   │
  │                   └──► policy check ► execution ► observation
  │
  ├──────────────► MEMORY
  │                   ├── SQL
  │                   ├── Vector / RAG
  │                   └── Graph
  │
  └──────────────► INFERENCE
                      │
                      ▼
                  OpenShell
                      │
                      ▼
                   Provider
                      │
                      ▼
                     LLM
```

Parallel telemetry path:

```text
EXECUTION
   ↓
NeMo Agent Toolkit / instrumentation
   ↓
telemetry / traces
   ↓
LangSmith / Phoenix / Langfuse / OpenTelemetry
```

## 4. Three-loop architecture

All future explanations SHOULD preserve the distinction between three interacting loops.

### 4.1 Agent loop

```text
OBSERVATION
   ↓
STATE
   ↓
REASON
   ↓
DECISION
   ↓
TOOL / MEMORY / INFERENCE
   ↓
ACTION
   └──────────────► next OBSERVATION
```

### 4.2 Security loop

```text
REQUEST
   ↓
IDENTIFY
   ↓
POLICY
   ↓
ALLOW / DENY
   ↓
EXECUTE
   ↓
AUDIT
```

### 4.3 Observability loop

```text
EXECUTION
   ↓
TRACE
   ↓
METRICS
   ↓
EVALUATION
   ↓
ANALYSIS
   ↓
IMPROVEMENT
   ↓
NEW VERSION
```

## 5. Canonical execution sequence

1. User submits a task.
2. Agent receives the objective.
3. Agent loads state/context.
4. Agent consults memory when needed: SQL, vector/RAG, graph.
5. Agent evaluates available information.
6. Agent determines whether reasoning/inference is required.
7. If inference is required, the request passes through the configured OpenShell/provider path and the model returns a response.
8. Agent decides the next action.
9. Agent requests a tool/capability when required.
10. OpenShell evaluates the action against policy: allow or deny.
11. The resulting observation returns to the agent loop.
12. When the goal is complete, the agent produces output/artifacts for the user.

## 6. Conceptual invariants

The following separations are normative for repository documentation:

```text
Agent ≠ Model
NemoClaw ≠ Agent
OpenShell ≠ Model
NeMo Agent Toolkit ≠ NemoClaw
Tool ≠ Inference
Memory ≠ Model context only
Observability ≠ Execution authority
Container ≠ complete security policy
```

A document, diagram, lab, or implementation may refine these relationships, but MUST explicitly document any deviation or superseding architecture decision.

## 7. Validation rules

An artifact using this model is internally consistent when:

1. the component responsible for inference is distinct from the agent orchestrator;
2. external actions pass through an explicit capability/security boundary;
3. memory type is identified when material to the design;
4. tool execution and LLM inference are not treated as identical operations;
5. observability is represented separately from execution;
6. lifecycle/configuration is represented separately from runtime decision-making;
7. product-specific claims cite or register an authoritative source before being labeled VALIDATED.

## 8. Related artifact

- `docs/agents/AGENT_MENTAL_MODEL_v0.1.md`
- `docs/agents/assets/AGENT_MENTAL_MODEL_v0.1.webp`

## 9. Change control

- v0.x: evolving mental model.
- Material changes to component boundaries, trust boundaries, or core loops require version review.
- A significant architectural change SHOULD be accompanied by an ADR.
- Promotion to v1.0 requires review against current official NVIDIA/OpenShell/NemoClaw/NeMo Agent Toolkit documentation.
