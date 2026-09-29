# NVIDIA Voice RAG ↔ NemoClaw / OpenClaw / OpenShell Mapping

**ID:** NVIDIA-MAP-VOICE-RAG-NEMOCLAW-001
**Version:** 0.1
**Status:** DRAFT

## Purpose
Prevent category errors when combining the Voice RAG tutorial with the NemoClaw stack. The tutorial describes an AI application workflow; NemoClaw/OpenClaw/OpenShell describe agent runtime, integration, lifecycle and execution-control boundaries.

## Layer mapping

| Voice RAG concern | OpenClaw | NemoClaw | OpenShell | Boundary |
|---|---|---|---|---|
| User/agent interaction | Agent interface/runtime | Onboards/configures supported runtime | Hosts sandbox boundary | Runtime |
| Agent behavior/tools/memory | Owns assistant runtime behavior | Adds integration/plugin/config | Enforces execution policy | Agent |
| ASR / RAG / VLM / reasoning / safety calls | Application integration can invoke services | Can configure managed inference path | Proxies controlled inference | AI services |
| Model/provider selection | Consumes configured model reference | Onboarding + blueprint/inference profiles | Routes request to provider | Inference |
| Credentials | Runs without needing raw upstream credentials | Declares/manages integration intent | Holds provider credentials outside sandbox | Security |
| Network/filesystem/process controls | Operates inside permitted environment | Supplies reference-stack policy/config | Enforcement engine | Sandbox |
| Lifecycle | Agent-specific state | onboarding/status/rebuild/snapshot orchestration | sandbox primitives | Operations |
| RAG index/data lifecycle | Application responsibility unless explicitly integrated | Not inherently the document-RAG pipeline | Not inherently the vector database | Knowledge |

## Correct stack interpretation

VOICE RAG APPLICATION WORKFLOW
ASR -> Retrieve -> Rerank -> Vision -> Reason -> Safety
                         |
                         v
OPENCLAW
assistant runtime / tools / memory / behavior
                         |
                         v
NEMOCLAW
reference-stack onboarding + blueprint + agent integration
+ managed inference/integrations + lifecycle
                         |
                         v
OPENSHELL
sandbox + credential boundary + network/filesystem/process policy
+ inference routing
                         |
                         v
MODEL / INFERENCE PROVIDERS

This is a conceptual layering map. It does not claim that the Voice RAG tutorial is implemented by NemoClaw.

## Request path when adapted to the stack

Candidate future integration:

User -> OpenClaw-based agent/application -> Voice/RAG workflow node -> inference.local / managed route -> OpenShell gateway -> configured provider/model -> workflow state -> safety -> response

Exact support for each specialized model must be validated against the current NemoClaw inference catalog before implementation.

## Responsibility boundaries

### OpenClaw
NVIDIA documentation describes OpenClaw as the assistant layer: runtime, tools, memory, and behavior inside the container. It does not define the host sandbox or gateway.

### OpenShell
NVIDIA documentation describes OpenShell as the execution environment and enforcement boundary: sandbox lifecycle, network/filesystem/process policy, credential custody, and inference routing.

### NemoClaw
NVIDIA documentation describes NemoClaw as the NVIDIA reference stack combining host CLI, versioned blueprint, agent-specific integration, managed inference/integrations, readiness and lifecycle operations.

### Voice RAG application
Owns the domain workflow: speech transcription, indexing/retrieval/reranking, multimodal context assembly, reasoning and application-level safety behavior.

## Critical distinction: two kinds of safety

CONTENT / MODEL SAFETY:
Nemotron Safety Guard -> content / PII / policy-category evaluation.

EXECUTION / RUNTIME SAFETY:
OpenShell -> network / filesystem / process / credentials / inference boundary.

They are complementary and must not be represented as equivalents.

## Critical distinction: two kinds of memory

AGENT MEMORY:
conversation/workspace/runtime memory -> OpenClaw concern.

KNOWLEDGE RETRIEVAL:
documents/images -> embeddings -> vector index -> retrieved evidence -> RAG application concern.

Do not infer that OpenClaw memory search is automatically an enterprise multimodal RAG ingestion pipeline.

## Candidate integration contract

- application.workflow: voice_rag
- agent_runtime.implementation: openclaw
- reference_stack.implementation: nemoclaw
- execution_boundary.implementation: openshell
- ai_services: ASR, embedding, reranking, vision-language, reasoning, content-safety are configurable
- knowledge.index: application_owned
- knowledge.provenance: required
- controls.network_policy: openshell
- controls.filesystem_policy: openshell
- controls.process_policy: openshell
- controls.credential_custody: openshell
- controls.lifecycle: nemoclaw

This contract is a project design artifact, not an NVIDIA-published configuration.

## Validation gates before implementation

1. Verify current NemoClaw/OpenShell compatibility.
2. Verify each required model/provider through the selected inference path.
3. Verify ASR streaming requirements separately from text inference.
4. Define RAG storage/index ownership and persistence.
5. Define tool/network allowlists.
6. Run preflight and smoke tests.
7. Capture latency, retrieval, safety and policy evidence independently.
8. Only then promote the architecture from DRAFT toward VALIDATED.

## Sources

- https://developer.nvidia.com/blog/how-to-build-a-voice-agent-with-rag-and-safety-guardrails/
- https://docs.nvidia.com/nemoclaw/user-guide/openclaw/about/how-it-works
- https://docs.nvidia.com/nemoclaw/user-guide/openclaw/about/ecosystem
- https://docs.nvidia.com/nemoclaw/latest/user-guide/openclaw/reference/architecture
