# Agent Mental Model Visual Assets

This directory contains the controlled raster visual versions of the Agent Mental Model.

## Current verified files

| File | Format | Resolution | Role |
|---|---|---:|---|
| AGENT_MENTAL_MODEL_v0.1.webp | WebP | 512 × 341 | V1 canonical raster baseline / preview |
| AGENT_MENTAL_MODEL_v0.1.png | PNG | 512 × 341 | V1 preview PNG |
| AGENT_MENTAL_MODEL_v0.1_doc_1024x682.png | PNG | 1024 × 682 | V1 documentation rendition |
| AGENT_MENTAL_MODEL_v0.1_master_2048x1364.png | PNG | 2048 × 1364 | V1 recommended master raster rendition |
| AGENT_MENTAL_MODEL_v0.2.webp | WebP | 512 × 341 | V2 strict raster derivative / preview |
| AGENT_MENTAL_MODEL_v0.2.png | PNG | 512 × 341 | V2 preview PNG |
| AGENT_MENTAL_MODEL_v0.2_doc_1024x682.png | PNG | 1024 × 682 | V2 documentation rendition |
| AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png | PNG | 2048 × 1364 | V2 recommended master raster rendition |

All dimensions are verified by the repository GitHub Actions pipeline with ImageMagick `identify`.

## Resolution profiles

```text
PREVIEW        512 × 341   = 1×
DOCUMENTATION 1024 × 682   = 2×
MASTER        2048 × 1364  = 4×
```

The aspect ratio, layout and semantics are locked.

## Rendering method

The documentation and master PNGs are deterministic raster derivatives of the canonical 512 × 341 WebP baseline.

```text
CANONICAL WEBP 512×341
        │
        ├── direct conversion ──► PREVIEW PNG 512×341
        │
        ├── Lanczos 2× ─────────► DOCUMENTATION PNG 1024×682
        │
        └── Lanczos 4× ─────────► MASTER PNG 2048×1364
```

No crop, generative fill, AI reinterpretation, layout change or semantic change is authorized by this transformation.

The larger raster renditions improve compatibility and display size but do not create new source detail. A future true high-resolution master should preferably be rendered from an approved editable/vector source.

## Automation

Pipeline:

`.github/workflows/convert-agent-mental-model-png.yml`

The workflow rebuilds the PNG profiles from the canonical WebP assets and rejects the run if exact target dimensions are not produced.

Normative reference:

`governance/VISUAL_RESOLUTION_STANDARD_v0.1.md`
