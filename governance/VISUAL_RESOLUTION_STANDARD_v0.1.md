# Visual Resolution Standard

**ID:** NVIDIA-VISUAL-RESOLUTION-STANDARD-001  
**Version:** 0.1  
**Status:** ACTIVE  
**Scope:** Versioned raster visual artifacts, including the Agent Mental Model family.

## 1. Purpose

This standard separates the **current verified raster resolution** from the **recommended production resolution** so that previews, documentation renditions and master renditions are not confused.

Resolution changes are presentation changes only. They MUST NOT authorize redesign, semantic changes, cropping, stretching, component movement, typography changes, new connections or generative reinterpretation.

## 2. Verified current state

The GitHub Actions verification for the current Agent Mental Model PNG renditions reports:

| Artifact | Format | Verified resolution | Role today |
|---|---|---:|---|
| AGENT_MENTAL_MODEL_v0.1.webp | WebP | 512 × 341 px | Current raster baseline / preview |
| AGENT_MENTAL_MODEL_v0.1.png | PNG | 512 × 341 px | Current PNG rendition |
| AGENT_MENTAL_MODEL_v0.2.webp | WebP | 512 × 341 px | Current V2 raster derivative / preview |
| AGENT_MENTAL_MODEL_v0.2.png | PNG | 512 × 341 px | Current V2 PNG rendition |

Canonical raster aspect ratio:

```text
512 : 341
≈ 1.501466 : 1
```

The aspect ratio is **LOCKED** for strict derivatives.

## 3. Recommended resolution profile

The project adopts the following target profile:

| Profile | Resolution | Scale from current baseline | Recommended use |
|---|---:|---:|---|
| PREVIEW | 512 × 341 px | 1× | GitHub preview, web preview, lightweight assets |
| DOCUMENTATION | 1024 × 682 px | 2× | Markdown docs, PDF, reports, normal presentations |
| MASTER | 2048 × 1364 px | 4× | Canonical high-resolution raster rendition, zooming, export source |

Concrete recommendation:

```text
MASTER PNG           = 2048 × 1364
DOCUMENTATION PNG    = 1024 × 682
PREVIEW PNG / WEBP   =  512 × 341
```

All three are exact integer multiples of the current raster baseline, preserving geometry and aspect ratio.

## 4. Resolution invariants

For every derived resolution:

```text
ASPECT_RATIO(target) = ASPECT_RATIO(baseline)

CROP                  = FALSE
STRETCH               = FALSE
GENERATIVE_EXPANSION  = FALSE
AI_REINTERPRETATION   = FALSE
LAYOUT_CHANGE         = FALSE
SEMANTIC_CHANGE       = FALSE
```

The permitted transformation is a deterministic raster scale or a native render from an approved editable/vector source.

## 5. Current baseline limitation

The current canonical raster source is only **512 × 341 px**.

A deterministic 2× or 4× upscale can preserve layout and appearance, but it does **not create new source detail**.

Therefore:

- 1024 × 682 and 2048 × 1364 derivatives are valid for compatibility and controlled presentation.
- A future true high-resolution master SHOULD preferably be rendered natively from an editable/vector source such as SVG, Draw.io, Figma or PowerPoint.
- An AI/generative upscale MUST NOT become canonical automatically because it can reinterpret text, icons, borders, arrows and geometry.

## 6. Source-of-truth hierarchy

Until an approved editable/vector source exists:

```text
1. Canonical raster baseline: 512 × 341
2. Resolution standard
3. Deterministic derived renditions
```

After an editable/vector source is approved:

```text
1. Editable/vector source
2. MASTER PNG: 2048 × 1364
3. DOCUMENTATION PNG: 1024 × 682
4. PREVIEW PNG/WEBP: 512 × 341
```

## 7. Naming convention

Recommended naming when multiple resolutions are stored explicitly:

```text
AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png
AGENT_MENTAL_MODEL_v0.2_doc_1024x682.png
AGENT_MENTAL_MODEL_v0.2_preview_512x341.webp
```

The existing filenames remain valid and MUST NOT be renamed merely to adopt this standard.

## 8. Validation gate

Before accepting a derived rendition:

```text
[ ] width and height match the declared profile
[ ] aspect ratio is unchanged
[ ] no crop occurred
[ ] no stretch occurred
[ ] no element moved
[ ] no text changed
[ ] no icon changed
[ ] no arrow or connector changed
[ ] no semantic relationship changed
[ ] transformation is reproducible
```

## 9. Canonical recommendation

> Keep **512 × 341** as the lightweight preview baseline, use **1024 × 682** for documentation, and establish **2048 × 1364** as the recommended PNG master resolution. Prefer a future native/vector render for the true master; do not use generative AI upscaling as the canonical conversion path.

## 10. Implementation status

The recommended raster profiles are now implemented for both V1 and V2.

| Version | Preview | Documentation | Master |
|---|---|---|---|
| v0.1 | 512 × 341 PNG/WebP | 1024 × 682 PNG | 2048 × 1364 PNG |
| v0.2 | 512 × 341 PNG/WebP | 1024 × 682 PNG | 2048 × 1364 PNG |

Generation is automated by:

`.github/workflows/convert-agent-mental-model-png.yml`

The workflow uses explicit deterministic Lanczos scaling for the 2× and 4× raster renditions and validates exact dimensions before committing outputs.

The current master files are **recommended master raster renditions**, not native high-resolution sources. Their lineage remains the 512 × 341 canonical raster baseline until an approved editable/vector source is introduced.

## 11. v0.3 controlled baseline

The active visual baseline is now:

`AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png`

Its resolution is an exact 3× profile:

```text
512 × 341 × 3 = 1536 × 1023
```

This profile is valid alongside the existing preview/documentation/master profiles.

| Profile | Resolution | Role |
|---|---:|---|
| Preview | 512 × 341 | lightweight preview |
| Documentation | 1024 × 682 | docs/PDF/presentations |
| Controlled baseline v0.3 | 1536 × 1023 | active human-readable visual baseline |
| Master raster profile | 2048 × 1364 | 4× raster export profile |

The v0.3 baseline was produced through a controlled re-baseline decision and a deterministic one-pixel right-edge normalization from the validated 1537 × 1023 legibility candidate. The retained region has zero pixel error.

The previous rule prohibiting crop remains the default for strict derivatives. The one-pixel crop used for baseline normalization is an explicitly authorized exception documented in:

`governance/AGENT_MENTAL_MODEL_BASELINE_PROMOTION_v0.3.md`
