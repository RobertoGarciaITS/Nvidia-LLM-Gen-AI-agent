# Agent Mental Model Baseline Comparison — V0.2 vs V0.3

**Report ID:** NVIDIA-AGENT-MENTAL-MODEL-BASELINE-COMPARISON-001  
**Version:** 0.1  
**Status:** COMPLETE  
**Baseline:** AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png  
**Candidate:** AGENT_MENTAL_MODEL_v0.3_candidate_1537x1023.png  
**Contract:** NVIDIA-AGENT-MENTAL-MODEL-CONTRACT-001

## 1. Decision summary

V0.3 successfully restores practical legibility and preserves the mental-model architecture at the semantic level.

It is **not promoted** to controlled baseline in this review because two governance requirements remain unresolved:

1. the candidate does not preserve the exact locked raster aspect ratio;
2. generation metadata does not prove strict image-to-image derivation from V0.2.

Current decision:

~~~text
LEGIBILITY                 = PASS
SEMANTIC MODEL             = PASS
ARCHITECTURE TOPOLOGY      = PASS
COMPONENT COVERAGE         = PASS
VISUAL STRUCTURE           = PASS_WITH_VARIANCE
STRICT ASPECT RATIO        = FAIL
STRICT BASELINE LINEAGE    = NOT VERIFIED
BASELINE PROMOTION         = BLOCKED
~~~

## 2. Resolution and aspect-ratio gate

| Artifact | Resolution | Aspect ratio |
|---|---:|---:|
| V0.2 controlled master | 2048 × 1364 | 1.5014662757 |
| Locked base profile | 512 × 341 | 1.5014662757 |
| V0.3 candidate | 1537 × 1023 | 1.5024437928 |

Relative ratio variance:

~~~text
≈ +0.065104%
~~~

The variance is visually small, but the project resolution contract declares aspect ratio LOCKED. Therefore the strict geometry gate does not pass.

## 3. Legibility gate

Visual review at normal viewing size shows a clear improvement in V0.3:

- headings are sharply readable;
- small card labels and bullets are readable;
- execution-flow steps are readable;
- responsibility descriptions are readable;
- provider/model labels are readable;
- telemetry labels are readable.

A diagnostic edge-sharpness comparison also shows materially stronger high-frequency detail in V0.3. This metric is diagnostic only; the acceptance decision is based on visual usability, not on sharpness score alone.

Result:

~~~text
LEGIBILITY = PASS
~~~

## 4. Component coverage gate

The V0.3 candidate retains the major component groups required by the mental-model contract:

- Usuario;
- NemoClaw — Lifecycle & Configuration;
- OpenShell Sandbox — Seguridad y Aislamiento;
- AI Agent;
- Planificación;
- Estado;
- Herramientas / Tools;
- inference local;
- OpenShell Gateway;
- Modelo / Proveedor de Inferencia;
- Herramientas del Sistema;
- RAG / Vector DB;
- Graph Memory;
- Bases de Datos;
- APIs Externas;
- Observabilidad y Evaluación;
- NeMo Agent Toolkit;
- LangSmith;
- Arize Phoenix;
- Langfuse;
- OpenTelemetry;
- Flujo de Ejecución;
- Responsabilidades por Componente;
- Beneficios de esta arquitectura.

Result:

~~~text
COMPONENT COVERAGE = PASS
~~~

## 5. Semantic invariants

The candidate preserves the normative separations:

~~~text
Agent ≠ Model
NemoClaw ≠ Agent
OpenShell ≠ Model
NeMo Agent Toolkit ≠ NemoClaw
Tool ≠ Inference
Memory ≠ Model context only
Observability ≠ Execution authority
Container ≠ complete security policy
~~~

Observed architecture remains consistent with the contract:

- the AI Agent is the orchestrator;
- the model/provider is separate and performs inference;
- OpenShell is represented as security/control/routing infrastructure;
- NemoClaw is represented as lifecycle/configuration;
- tools and memory are distinct capabilities;
- inference requests and model responses have distinct paths;
- observability is shown as a separate cross-cutting layer;
- NeMo Agent Toolkit is not conflated with NemoClaw.

Result:

~~~text
SEMANTIC MODEL        = PASS
ARCHITECTURE TOPOLOGY = PASS
~~~

## 6. Execution-flow review

The V0.3 candidate retains an eight-step example flow:

~~~text
1. Usuario solicita una tarea
2. Agente analiza y planifica
3. Consulta memoria (RAG / Graph / DB)
4. Decide acción (tool o inferencia)
5. OpenShell aplica políticas y ejecuta
6. Modelo realiza la inferencia
7. Agente procesa la respuesta
8. Genera resultado y artifacts
~~~

This remains consistent with the canonical distinction among orchestration, memory, tools, security/policy and inference.

## 7. Visual-structure review

V0.3 preserves the recognizable high-level composition:

~~~text
Observability
     ↓
NemoClaw boundary
     ↓
OpenShell sandbox
     ↓
AI Agent ↔ inference routing ↔ provider/model
     ↓
Tools / Memory / Databases / APIs
     ↓
Execution flow
     ↓
Responsibilities + Benefits
~~~

However, V0.3 is a newly generated raster image rather than a proven strict image-to-image edit. Exact geometry, spacing and raster pixels therefore cannot be asserted as unchanged.

Result:

~~~text
VISUAL STRUCTURE = PASS_WITH_VARIANCE
STRICT PIXEL DERIVATION = NOT ESTABLISHED
~~~

## 8. Lineage gate

Generation metadata for the new image does not establish an image-to-image parent relation to the V0.2 baseline.

Therefore:

~~~text
STRICT_BASELINE_DERIVATION = NOT VERIFIED
~~~

This is a governance blocker, not a semantic or legibility failure.

## 9. Promotion decision

V0.3 is accepted as the **preferred legibility candidate**, but V0.2 remains the controlled baseline.

~~~text
PREFERRED_FOR_REVIEW / HUMAN READING = V0.3
CONTROLLED BASELINE                   = V0.2
PROMOTION STATUS                      = BLOCKED
~~~

## 10. Required next controlled action

Create a final baseline candidate that resolves both blockers:

1. use a controlled derivation path from the approved baseline/design;
2. output an exact approved aspect-ratio profile, preferably:
   - 1536 × 1023 (3× of 512 × 341), or
   - 2048 × 1364 (4× master profile);
3. preserve the legibility achieved in V0.3;
4. rerun semantic, visual, legibility and lineage gates;
5. only then execute explicit baseline promotion.

## 11. Final conclusion

> V0.3 solves the readability problem and preserves the architecture, but it should not yet replace V0.2 as the controlled baseline. The remaining work is governance/lineage normalization, not conceptual redesign.
