# Agent Mental Model v0.3 — Legibility Recovery Candidate

**ID:** NVIDIA-AGENT-MENTAL-MODEL-RASTER-CANDIDATE-003  
**Version:** 0.3  
**Status:** DRAFT  
**Purpose:** Recover diagram legibility after the raster/vector migration experiment reduced practical readability.

## 1. Artifact

```text
docs/agents/assets/AGENT_MENTAL_MODEL_v0.3_candidate_1537x1023.png
```

Verified properties:

```text
Format:     PNG
Resolution: 1537 × 1023
Role:       legibility-recovery raster candidate
```

The repository import pipeline verified the final file as PNG at exactly 1537 × 1023.

## 2. Relationship to the baseline

The currently controlled raster baseline remains the v0.2 family.

This v0.3 file is a **new candidate**, not a silent replacement.

```text
V0.2 CONTROLLED BASELINE
          │
          ├── vector migration experiment
          │       └── v0.3 SVG candidates
          │
          └── legibility recovery
                  └── v0.3 raster candidate 1537×1023
```

## 3. Lineage limitation

The image was generated with the approved baseline and project mental model as design context, but generation metadata does not prove a strict image-to-image derivative relationship.

Therefore:

```text
STRICT_BASELINE_DERIVATION = NOT VERIFIED
CANONICAL_BASELINE         = FALSE
STATUS                     = DRAFT
```

It MUST NOT supersede v0.2 until visual, semantic and legibility validation are completed.

## 4. Legibility objective

The previous vector-validation render was technically useful for editability testing but was judged insufficiently legible for the intended learning artifact.

The v0.3 raster candidate restores a larger native raster canvas:

```text
1537 × 1023
```

This resolution is not one of the established 512/1024/2048 raster profiles because it originates from a new image-generation render. It is preserved at its native generated dimensions to avoid another unnecessary resampling step.

## 5. Repository transport

The generated PNG was transferred to GitHub through a temporary high-quality WebP q95 transport representation.

Transport source verification:

```text
WebP transfer resolution: 1537 × 1023
SHA-256:
c94628402b9d347daaacff982e66843b8994da44ecf4750b60b135428d6834c3
```

GitHub Actions then converted the transport file to PNG, verified the final format and dimensions, committed the PNG, and removed all transport files from the repository.

The final PNG is therefore a high-quality transcoded representation of the generated image, not byte-identical to the original local PNG.

## 6. Required promotion gates

Before v0.3 can become the controlled baseline:

```text
[ ] Visual review against v0.2
[ ] Semantic labels and relationships validated
[ ] Text legibility accepted at normal viewing size
[ ] No required component missing
[ ] Architecture topology validated
[ ] Strict/controlled lineage decision documented
[ ] Explicit baseline promotion decision
```

## 7. Current decision

> Preserve v0.2 as the controlled baseline and retain v0.3 as the legibility-recovery candidate until validation is complete.
