# NVIDIA Voice RAG Agent Reference Architecture

**ID:** NVIDIA-ARCH-VOICE-RAG-001  
**Version:** 0.1  
**Status:** DRAFT  
**Source:** NVIDIA Technical Blog, "How to Build a Voice Agent with RAG and Safety Guardrails" (2026-01-05)

## Objective
Normalize the tutorial into a reusable reference architecture and separate source facts from project interpretation.

## Source-derived runtime
```text
Voice input
  -> ASR
  -> multimodal retrieval
       -> embedding
       -> vector search
       -> reranking
       -> optional image description
  -> reasoning
  -> safety guard
  -> response
```

## Component / model matrix

| Component | Tutorial model | Architectural responsibility |
|---|---|---|
| ASR | `nemotron-speech-streaming-en-0.6b` | streaming speech-to-text |
| Embedding | `llama-nemotron-embed-vl-1b-v2` | semantic representation of text/images |
| Reranking | `llama-nemotron-rerank-vl-1b-v2` | reorder retrieved candidates |
| Vision-language | `nemotron-nano-12b-v2-vl` | describe retrieved images in context |
| Reasoning | `nemotron-3-nano-30b-a3b` | answer generation over query + retrieved context |
| Safety | `llama-3.1-nemotron-safety-guard-8b-v3` | content-safety / PII guardrail |

The article reports about 6–7% retrieval-accuracy improvement for the reranker in its cited evaluation context; this is not treated as a universal system guarantee.

## Two-pipeline RAG model

### A. Knowledge / indexing path
```text
Enterprise data
  -> parse / prepare
  -> text, image, or text+image objects
  -> multimodal embedding
  -> vectors
  -> FAISS index
```

### B. Online query path
```text
User query
  -> query embedding
  -> FAISS candidate retrieval
  -> reranking
  -> selected evidence
  -> optional image description
  -> context assembly
  -> reasoning
```

**Invariant:** indexing and online inference are different lifecycle paths.

## Architectural planes

1. **Interaction plane** — voice/user interface and response.
2. **Perception plane** — ASR and vision-language interpretation.
3. **Knowledge plane** — embedding, vector index, retrieval, reranking.
4. **Intelligence plane** — context assembly and reasoning.
5. **Trust plane** — safety/PII checks.
6. **Orchestration plane** — graph/state/routing of the application workflow.

## State contract

A provider-neutral state representation for later labs:

```yaml
request_id: string
input:
  modality: voice|text
  audio_ref: optional
query:
  transcript: string
retrieval:
  query_embedding_ref: optional
  candidates: []
  reranked_context: []
vision:
  image_descriptions: []
reasoning:
  context: []
  candidate_response: optional
safety:
  input_result: optional
  output_result: optional
response:
  text: optional
  audio_ref: optional
telemetry:
  latency_ms: {}
  errors: []
```

This schema is a **project interpretation**, not a schema published by the tutorial.

## Control-flow abstraction

```text
START
  -> perceive
  -> input guard (recommended project extension)
  -> retrieve
  -> rerank
  -> [images?] describe_images
  -> assemble_context
  -> reason
  -> output_guard
  -> respond
END
```

The explicit input/output guard split above is a normalized project design. Preserve this distinction when comparing it with the tutorial implementation.

## Reusable design patterns

- Specialized models behind explicit interfaces.
- Retrieve broadly, then rerank narrowly.
- Convert modality-specific evidence into normalized context before reasoning.
- Keep the reasoning model separate from retrieval.
- Treat safety as a control boundary rather than an LLM prompt convention.
- Keep ingestion/indexing separate from request-time inference.
- Maintain workflow state explicitly so nodes can be tested independently.

## Production gaps to evaluate

The tutorial is a learning reference, not a complete enterprise control plane. Before production use, evaluate at minimum: authentication/authorization, secrets, provenance/citations, document and index versioning, observability/tracing, evaluation, retries/timeouts, fallbacks, cost/latency telemetry, audit evidence, deployment security, and human approval where required.

## Source vs interpretation

**SOURCE:** model names, stated purposes, tutorial pipeline, FAISS usage, multimodal RAG, safety/reasoning composition.  
**INTERPRETATION:** six architectural planes, normalized state contract, input/output guard split, production-gap checklist.  
**LAB/RESULT:** none yet. No claim is made here that this architecture has been executed in this repository.

## Primary source

https://developer.nvidia.com/blog/how-to-build-a-voice-agent-with-rag-and-safety-guardrails/
