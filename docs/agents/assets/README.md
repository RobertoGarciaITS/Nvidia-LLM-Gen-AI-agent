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

## Vector source migration

A controlled SVG migration has started:

AGENT_MENTAL_MODEL_v0.2_source_candidate.svg

Current state:

~~~text
V2 MASTER PNG 2048×1364
        │
        ▼
RASTER-ANCHORED SVG CANDIDATE
        │
        ▼
incremental component migration
        │
        ▼
visual + semantic + editability gates
        │
        ▼
future canonical editable SVG
~~~

The candidate currently preserves the master PNG as the visible 1:1 anchor and contains stable planned component groups. It is not yet a fully vectorized or canonical editable source.

See:

- governance/VECTOR_SOURCE_MIGRATION_CONTRACT_v0.1.md
- AGENT_MENTAL_MODEL_VECTOR_SOURCE_MANIFEST_v0.1.yaml

### CR-VECTOR-001 — first real editable component

Candidate v0.2 migrates CMP-050 AI Agent core as a hybrid raster/vector SVG:

- outer panel is editable SVG;
- title, subtitle, description and internal cards are editable SVG;
- robot icon remains raster-preserved;
- all other components remain locked to the raster baseline.

Status: REVIEW_REQUIRED. The candidate is not canonical.

Files:

- AGENT_MENTAL_MODEL_v0.2_source_candidate_v0.2.svg
- AGENT_MENTAL_MODEL_VECTOR_SOURCE_MANIFEST_v0.2.yaml
- governance/change_requests/CR-VECTOR-001_CMP-050_AGENT_CORE_v0.1.md
- docs/agents/validation/VECTOR_MIGRATION_CR-VECTOR-001_REPORT_v0.1.md
