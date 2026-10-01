# STRICT BASELINE IMAGE V2 EXECUTION CONTRACT

**ID:** NVIDIA-VISUAL-V2-EXECUTION-CONTRACT-001\
**Version:** 0.1\
**Status:** ACTIVE\
**Trigger command:** `EJECUTA LA IMAGEN V2 CON EL BASELINE`

---

# 1. Purpose

Este contrato define exactamente cómo debe actuar el agente cuando el usuario indique:

```text
EJECUTA LA IMAGEN V2 CON EL BASELINE
```

La instrucción significa:

> Crear una nueva versión derivada de la imagen baseline canónica mediante edición controlada de la imagen existente, preservando estrictamente diseño, estructura, geometría, contenido, conexiones y lenguaje visual.

No significa:

```text
crear una imagen similar
reinterpretar el esquema
rediseñar la composición
generar nuevamente desde texto
modernizar el diseño
```

---

# 2. Trigger

Cuando el usuario escriba:

```text
EJECUTA LA IMAGEN V2 CON EL BASELINE
```

se activa automáticamente:

```text
MODE:
STRICT_BASELINE_DERIVATION
```

con:

```text
TARGET_VERSION = V2
```

y:

```text
DERIVATION_TYPE =
STRUCTURAL_REPLICA_WITH_CONTROLLED_DELTA
```

---

# 3. Baseline Resolution

El agente deberá localizar primero el baseline visual canónico.

Para el modelo mental actual:

```text
BASELINE_ID:
AGENT_MENTAL_MODEL

BASELINE_VERSION:
v0.1

BASELINE_FILE:
docs/agents/assets/AGENT_MENTAL_MODEL_v0.1.webp
```

Fuentes asociadas:

```text
CONTRACT:
governance/AGENT_MENTAL_MODEL_CONTRACT_v0.1.md

DOCUMENTATION:
docs/agents/AGENT_MENTAL_MODEL_v0.1.md
```

La jerarquía de autoridad será:

```text
1. Baseline image
2. Mental-model contract
3. Documentation artifact
4. Explicit user delta
```

---

# 4. Mandatory Editing Mode

La nueva versión debe derivarse de la imagen existente.

Obligatorio:

```text
BASELINE IMAGE
      ↓
IMAGE-TO-IMAGE EDIT
      ↓
V2
```

Prohibido:

```text
TEXT DESCRIPTION
      ↓
TEXT-TO-IMAGE
      ↓
NEW INTERPRETATION
```

La imagen baseline debe ser la entrada visual efectiva de la operación.

---

# 5. Fundamental Equation

La operación se define como:

```text
V2 = V1 + AUTHORIZED_DELTA
```

Formalmente:

```text
∀ property ∉ AUTHORIZED_DELTA:

property(V2) = property(V1)
```

Esto significa:

> Todo lo no autorizado explícitamente debe permanecer igual.

---

# 6. Default Delta

Si el usuario ejecuta:

```text
EJECUTA LA IMAGEN V2 CON EL BASELINE
```

sin proporcionar cambios adicionales, el delta por defecto será:

```yaml
AUTHORIZED_DELTA:

  - id: DELTA-001
    element: version_identity
    operation: derive_new_version
    from: v0.1
    to: v0.2

  - id: DELTA-002
    element: rendering
    operation: preserve_or_improve_quality
    constraint: no_visual_redesign
```

No se autoriza ningún cambio conceptual.

---

# 7. Baseline Lock

Todos los siguientes elementos quedan:

```text
LOCKED
```

## Geometry

```text
canvas
aspect ratio
layout
component coordinates
relative positions
relative sizes
section dimensions
margins
spacing
alignment
```

## Style

```text
color palette
background
borders
corner radius
icon style
icon placement
line style
arrow style
visual density
typography hierarchy
font-size relationships
```

## Structure

```text
section order
component grouping
component hierarchy
architecture topology
```

## Connections

```text
arrows
connectors
directions
dependencies
relationships
control paths
data paths
inference paths
memory paths
security paths
observability paths
```

## Content

```text
titles
labels
terminology
component names
descriptions
existing text
```

---

# 8. Semantic Lock

The following mental-model distinctions MUST remain unchanged:

```text
Agent ≠ Model

NemoClaw ≠ Agent

OpenShell ≠ Model

NeMo Agent Toolkit ≠ NemoClaw

Tool ≠ Inference

Memory ≠ Model Context

Observability ≠ Execution Authority

Container ≠ Complete Security Boundary
```

---

# 9. Architecture Lock

Preserve the conceptual architecture:

```text
USER
 │
 ▼
NemoClaw
 │
 ▼
OpenShell
 │
 ▼
AI AGENT
 │
 ├──── Tools
 │
 ├──── Memory
 │
 └──── Inference
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

Preserve parallel observability:

```text
Agent / Tools / LLM
        │
        ▼
NeMo Agent Toolkit
        │
        ▼
Telemetry / Tracing
        │
 ┌──────┼───────┐
 ▼      ▼       ▼
LangSmith Phoenix OTel / other configured observer
```

---

# 10. Three-Loop Lock

The following three loops are canonical and immutable unless explicitly changed:

## Agent Loop

```text
OBSERVE
   ↓
STATE
   ↓
REASON
   ↓
DECIDE
   ↓
ACT
   ↓
OBSERVE
```

## Security Loop

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

## Observability Loop

```text
EXECUTION
   ↓
TRACE
   ↓
MEASURE
   ↓
EVALUATE
   ↓
ANALYZE
   ↓
IMPROVE
```

---

# 11. Text Preservation Rule

All baseline text is immutable by default.

```text
IF TEXT_ELEMENT ∉ AUTHORIZED_DELTA
THEN:
    preserve exactly
```

Forbidden without authorization:

```text
rewrite
summarize
translate
correct
abbreviate
rename
paraphrase
```

---

# 12. Connection Preservation Rule

Every baseline relationship remains immutable.

```text
IF CONNECTION ∉ AUTHORIZED_DELTA
THEN:
    preserve source
    preserve target
    preserve direction
    preserve position
    preserve visual representation
```

No new architectural relationship may be inferred.

---

# 13. Forbidden Operations

The agent MUST NOT:

```text
redesign
reinterpret
restyle
modernize
simplify
expand
summarize
reorganize
move components
resize components
recolor components
replace icons
change arrows
change connections
change terminology
change architecture
change hierarchy
change section order
change conceptual relationships
```

The following are NOT valid reasons for changing the baseline:

```text
better design
cleaner composition
more professional
more modern
better UX
better visualization
improved hierarchy
more readable arrangement
```

---

# 14. Localized Edit Principle

Changes must affect the smallest possible visual region.

```text
LOCATE TARGET
      ↓
EDIT TARGET ONLY
      ↓
PRESERVE SURROUNDING REGION
      ↓
PRESERVE ENTIRE REMAINDER
```

Do not redraw unaffected portions unless technically unavoidable.

---

# 15. Preflight

Before invoking image generation/editing, verify:

```text
[ ] baseline image exists
[ ] baseline image is available as an image input
[ ] contract is known
[ ] documentation is known
[ ] target is V2
[ ] authorized delta is known
[ ] no creative redesign is required
```

If the actual baseline image is unavailable:

```text
STOP
```

Do NOT reconstruct the baseline from memory.

Do NOT generate a visually similar image.

Request or recover the actual baseline.

---

# 16. Image Edit Instruction

When the baseline has been resolved, execute an image edit with the following semantic instruction:

```text
Create Version 2 as a strict controlled derivative
of the supplied baseline image.

Use the supplied image as the canonical visual source.

Do not redesign, reinterpret, redraw, restyle,
reorganize, simplify, expand, or modernize it.

Preserve the complete composition exactly:
canvas, aspect ratio, geometry, layout, component
positions, component sizes, spacing, hierarchy,
colors, backgrounds, borders, typography hierarchy,
icons, arrows, connectors, labels, text, section
ordering, architecture topology, relationships and
flow directions.

Preserve all architecture and mental-model meaning
defined by the associated contract.

This is an image-to-image controlled revision.

V2 = V1 + AUTHORIZED_DELTA.

Anything not explicitly included in AUTHORIZED_DELTA
must remain unchanged.

AUTHORIZED_DELTA:
derive the new artifact as Version 2 while preserving
the design and semantic baseline.

Rendering quality may be preserved or improved only
when this produces no design, geometry, content,
typography, color, topology or relationship changes.

The result must appear to be the exact same controlled
artifact family, not a newly generated interpretation.
```

---

# 17. Visual Regression Gate

After generation, verify:

```text
[ ] same aspect ratio
[ ] same canvas structure
[ ] same layout
[ ] same number of sections
[ ] same components
[ ] same component positions
[ ] same relative dimensions
[ ] same spacing
[ ] same colors
[ ] same typography hierarchy
[ ] same icons
[ ] same arrows
[ ] same connectors
[ ] same flow directions
[ ] same section ordering
[ ] same terminology
[ ] same architecture
[ ] same conceptual relationships
[ ] no unauthorized additions
[ ] no unauthorized deletions
```

---

# 18. Semantic Regression Gate

Verify:

```text
[ ] User role unchanged
[ ] NemoClaw role unchanged
[ ] OpenShell role unchanged
[ ] Agent role unchanged
[ ] Tool role unchanged
[ ] Memory model unchanged
[ ] Inference path unchanged
[ ] Provider role unchanged
[ ] NeMo Agent Toolkit role unchanged
[ ] Observability role unchanged
[ ] Agent Loop unchanged
[ ] Security Loop unchanged
[ ] Observability Loop unchanged
```

---

# 19. Acceptance Rule

Accept V2 only if:

```text
V2 ≈ V1 + authorized delta
```

Reject the result if:

```text
V2 = reinterpretation(V1)
```

or:

```text
unauthorized_delta != 0
```

---

# 20. Output Naming

Default target:

```text
docs/agents/assets/AGENT_MENTAL_MODEL_v0.2.webp
```

Metadata:

```yaml
artifact:
  id: NVIDIA-AGENT-MENTAL-MODEL
  version: v0.2
  derived_from: v0.1

  derivation:
    type: STRUCTURAL_REPLICA_WITH_CONTROLLED_DELTA

  baseline:
    file: AGENT_MENTAL_MODEL_v0.1.webp

  contract:
    id: NVIDIA-VISUAL-V2-EXECUTION-CONTRACT-001

  semantic_contract:
    id: NVIDIA-AGENT-MENTAL-MODEL-CONTRACT-001
```

---

# 21. Trigger Behavior Summary

When the user states:

```text
EJECUTA LA IMAGEN V2 CON EL BASELINE
```

interpret it as:

```text
1. Retrieve canonical V1 baseline.
2. Retrieve associated contract/documentation.
3. Lock baseline.
4. Set V2 as target.
5. Apply only authorized delta.
6. Use image-to-image editing.
7. Do not redesign.
8. Preserve architecture and text.
9. Perform visual regression review.
10. Perform semantic regression review.
11. Produce V2.
```

---

# 22. Absolute Execution Rule

```text
BASELINE
    =
VISUAL SOURCE OF TRUTH

MENTAL MODEL CONTRACT
    =
SEMANTIC SOURCE OF TRUTH

AUTHORIZED DELTA
    =
ONLY PERMITTED CHANGE

V2
    =
V1 + AUTHORIZED_DELTA
```

Anything else is:

```text
OUT OF SCOPE
```

---

# 23. Canonical Invocation

User command:

```text
EJECUTA LA IMAGEN V2 CON EL BASELINE
```

Agent interpretation:

```text
EXECUTE:
NVIDIA-VISUAL-V2-EXECUTION-CONTRACT-001

BASELINE:
AGENT_MENTAL_MODEL_v0.1.webp

TARGET:
AGENT_MENTAL_MODEL_v0.2.webp

MODE:
STRICT BASELINE DERIVATION

REDESIGN:
FALSE

REINTERPRETATION:
FALSE

IMAGE-TO-IMAGE:
REQUIRED

SEMANTIC CHANGES:
NONE unless explicitly supplied

UNAUTHORIZED DELTA:
ZERO
```

## Final Principle

> **V2 must be derived from V1, not recreated from the idea represented by V1.**