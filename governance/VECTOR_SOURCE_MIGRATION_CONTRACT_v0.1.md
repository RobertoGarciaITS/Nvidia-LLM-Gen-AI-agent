> **ARCHIVAL NOTICE:** This contract documents the retired V0.2 vector-migration experiment. Its V0.2 source files are no longer in the active tree. Use the current V0.3 baseline for future visual work.

# Vector Source Migration Contract

**ID:** NVIDIA-VECTOR-SOURCE-MIGRATION-CONTRACT-001  
**Version:** 0.1  
**Status:** ARCHIVED  
**Scope:** Agent Mental Model visual family

## 1. Purpose

This contract governs migration from the current raster baseline to a genuinely editable/vector visual source without silently redesigning or semantically changing the Agent Mental Model.

The migration target is an SVG source whose boxes, text, connectors, arrows and semantic groups can be edited independently.

## 2. Baseline

Current visual baseline:

~~~text
AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png
2048 × 1364
~~~

Initial migration candidate:

~~~text
AGENT_MENTAL_MODEL_v0.2_source_candidate.svg
~~~

The initial SVG candidate is intentionally raster anchored. It references the verified master PNG at a 1:1 canvas size and is therefore a transitional source candidate, not yet a fully vectorized source.

## 3. Promotion rule

The SVG MUST NOT be called the canonical editable source until all required components have been migrated and validated.

~~~text
DRAFT CANDIDATE
      ↓
COMPONENT INVENTORY
      ↓
CONTROLLED VECTOR RECONSTRUCTION
      ↓
VISUAL REGRESSION
      ↓
SEMANTIC REGRESSION
      ↓
EDITABILITY TEST
      ↓
APPROVAL
      ↓
CANONICAL EDITABLE SOURCE
~~~

## 4. Source-of-truth hierarchy during migration

~~~text
1. V2 master PNG — visual baseline
2. Agent mental model contract — semantic baseline
3. Strict baseline derivation contract — change-control baseline
4. Vector source migration contract — migration process
5. SVG candidate — implementation under validation
~~~

Until promotion, disagreement is resolved in favor of items 1–4, not the SVG candidate.

## 5. Stable component IDs

The migration SHALL use stable IDs:

| ID | Component group |
|---|---|
| CMP-010 | Header |
| CMP-020 | Observability |
| CMP-030 | NemoClaw boundary |
| CMP-040 | OpenShell boundary |
| CMP-050 | AI Agent core |
| CMP-060 | Tools |
| CMP-070 | Memory |
| CMP-080 | Inference routing |
| CMP-090 | Provider / models |
| CMP-100 | Execution flow |
| CMP-110 | Responsibilities |
| CMP-120 | Benefits |

Future individual text, connector and shape IDs SHOULD use:

~~~text
TXT-xxx
BOX-xxx
ICON-xxx
ARROW-xxx
CONN-xxx
~~~

IDs MUST remain stable across compatible visual versions unless explicitly superseded.

## 6. Migration unit

Only one controlled component group or one tightly coupled set of elements SHOULD be migrated per change request.

Example:

~~~text
CR-VECTOR-001
CMP-050 AI Agent core
Raster anchor remains visible for all other components.
~~~

A large one-shot redraw is prohibited for strict migration.

## 7. Visual invariants

Unless explicitly authorized:

~~~text
CANVAS               = LOCKED
ASPECT_RATIO         = LOCKED
COMPONENT_POSITIONS  = LOCKED
COMPONENT_SIZES      = LOCKED
MARGINS              = LOCKED
SPACING              = LOCKED
COLORS               = LOCKED
BORDERS              = LOCKED
CORNER_RADII         = LOCKED
TYPOGRAPHY_HIERARCHY = LOCKED
ARROWS                = LOCKED
CONNECTORS            = LOCKED
FLOW_DIRECTIONS       = LOCKED
SECTION_ORDER         = LOCKED
~~~

## 8. Semantic invariants

The vector migration does not authorize any change to component responsibilities, architecture topology, Agent / Model separation, NemoClaw / OpenShell distinction, tools, memory or inference roles, security relationships, observability relationships, the three canonical loops, or existing labels and terminology.

## 9. Text migration rule

Text MUST be migrated as editable SVG text whenever practical.

~~~text
text_content(new) = text_content(baseline)
position(new)     = position(baseline)
role(new)         = role(baseline)
~~~

No paraphrasing, correction, translation or abbreviation is authorized by migration. If exact font metrics cannot be reproduced, the variance MUST be documented before promotion.

## 10. Connection migration rule

Every connector receives a stable ID and retains SOURCE, TARGET, DIRECTION, ROUTING INTENT and VISUAL ROLE. No inferred or decorative connector may be added without a change request.

## 11. Regression gates

### 11.1 Structural gate

~~~text
[ ] same canvas
[ ] same aspect ratio
[ ] same section count
[ ] same component count
[ ] same component hierarchy
[ ] same source/target relationships
[ ] same text content
[ ] same flow directions
~~~

### 11.2 Visual gate

A rendered SVG candidate MUST be compared with the master PNG at 2048 × 1364.

Zero visual delta is preferred. Raster-vs-vector anti-aliasing may produce non-zero pixel differences even when geometry is equivalent; any accepted non-zero difference MUST be limited to rendering/anti-aliasing edges and MUST NOT represent a geometry, color, content or topology change.

### 11.3 Semantic gate

~~~text
[ ] no component meaning changed
[ ] no relationship changed
[ ] no label changed
[ ] no security boundary changed
[ ] no inference path changed
[ ] no observability path changed
~~~

### 11.4 Editability gate

~~~text
[ ] major boxes are independent SVG objects
[ ] text is independently editable
[ ] arrows/connectors are independently editable
[ ] logical groups use stable IDs
[ ] no single flattened raster is required for the complete visible design
~~~

## 12. Raster anchor retirement

The raster anchor L-000-baseline-raster may be removed only when all visible components have passed migration and regression gates. Before that point it remains the visual truth layer.

## 13. Version lineage

~~~yaml
vector_source:
  id: NVIDIA-AGENT-MENTAL-MODEL-VECTOR-SOURCE
  candidate_version: v0.1
  baseline_visual: AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png
  baseline_model_version: v0.2
  migration_mode: incremental
  canonical: false
  promotion_requires:
    - structural_regression_pass
    - visual_regression_pass
    - semantic_regression_pass
    - editability_gate_pass
~~~

## 14. Definition of Done

The migration is complete only when the SVG is independently editable, preserves the approved design and semantics, passes regression review, has documented lineage, and is explicitly promoted.

## 15. Absolute rule

> The raster baseline is replaced component by component, never reinterpreted as a new design.
