# Vector Migration Validation Report — CR-VECTOR-001

**Report ID:** NVIDIA-VECTOR-MIGRATION-VALIDATION-001  
**Version:** 0.1  
**Candidate:** AGENT_MENTAL_MODEL_v0.2_source_candidate_v0.2.svg  
**Baseline:** AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png  
**Render engine:** Inkscape  
**Canvas:** 2048 × 1364

## Scope

This validation covers only the first controlled vector migration: CMP-050 AI Agent core.

All other component groups remain raster anchored.

## Pixel comparison

| Metric | Result |
|---|---:|
| Full image MAE | 1.7137 |
| Full image changed pixels | 7.8323% |
| CMP-050 MAE | 21.2375 |
| CMP-050 changed pixels | 92.5806% |
| Outside CMP-050 MAE | 0.1743 |
| Outside CMP-050 changed pixels | 1.1498% |

Interpretation:

- most visual change is intentionally concentrated inside CMP-050;
- the large CMP-050 pixel delta is expected because raster text and boxes were replaced by native SVG objects;
- outside CMP-050, the candidate remains close to the raster baseline;
- the remaining outside-region delta is attributable mainly to mask-edge/rendering behavior and requires further refinement before canonical promotion.

## Gate status

| Gate | Status | Reason |
|---|---|---|
| Canvas / aspect ratio | PASS | 2048 × 1364 preserved |
| Scope containment | PASS_SCOPE_LIMITED | vector work constrained to CMP-050 |
| Structural semantics | PASS_SCOPE_LIMITED | architecture topology outside CMP-050 unchanged |
| Exact visual regression | REVIEW_REQUIRED | typography, anti-aliasing and panel rendering visibly differ |
| Exact semantic/text regression | REVIEW_REQUIRED | text must be rechecked against the visual baseline before acceptance |
| Editability | PARTIAL_PASS | panel, text and subcards editable; robot icon still raster |

## Promotion decision

~~~text
CANONICAL_EDITABLE_SOURCE = FALSE
CMP-050_STATUS            = MIGRATED_PARTIAL
NEXT_ACTION               = REFINE_AND_REVALIDATE
~~~

The candidate is useful as proof that incremental vector migration works, but it is not yet suitable to replace the raster baseline.
