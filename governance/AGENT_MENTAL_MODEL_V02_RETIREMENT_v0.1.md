# Agent Mental Model V0.2 Retirement Record

**ID:** NVIDIA-AGENT-MENTAL-MODEL-V02-RETIREMENT-001  
**Version:** 0.1  
**Status:** ACTIVE  
**Decision:** RETIRE V0.2 VISUAL ASSETS FROM ACTIVE TREE

## 1. Reason

The V0.2 raster and SVG artifacts are not sufficiently legible for normal project use and have been superseded by the validated V0.3 controlled baseline.

## 2. Decision

V0.2 visual assets are removed from the active repository tree.

They are **not erased from Git history**.

This preserves auditability without allowing obsolete visuals to appear as current or reusable assets.

## 3. Retired active-tree files

~~~text
docs/agents/assets/AGENT_MENTAL_MODEL_v0.2.webp
docs/agents/assets/AGENT_MENTAL_MODEL_v0.2.png
docs/agents/assets/AGENT_MENTAL_MODEL_v0.2_doc_1024x682.png
docs/agents/assets/AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png
docs/agents/assets/AGENT_MENTAL_MODEL_v0.2_source_candidate.svg
docs/agents/assets/AGENT_MENTAL_MODEL_v0.2_source_candidate_v0.2.svg
docs/agents/assets/AGENT_MENTAL_MODEL_v0.2_source_candidate_v0.3.svg
docs/agents/assets/AGENT_MENTAL_MODEL_VECTOR_SOURCE_MANIFEST_v0.1.yaml
docs/agents/assets/AGENT_MENTAL_MODEL_VECTOR_SOURCE_MANIFEST_v0.2.yaml
docs/agents/assets/AGENT_MENTAL_MODEL_VECTOR_SOURCE_MANIFEST_v0.3.yaml
docs/agents/validation/images/AGENT_MENTAL_MODEL_v0.2_source_candidate_v0.3_render.png
.github/workflows/render-vector-candidate-validation.yml
~~~

## 4. Historical recovery point

Immediately before retirement, the repository baseline state was represented by commit:

~~~text
76b4ff6361bd8e3e6c5f24aad6fab092facddca6
~~~

V0.2 assets remain recoverable from Git history and from earlier commits.

## 5. Current visual source

~~~text
CURRENT_VISUAL_BASELINE
= docs/agents/assets/AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png

STATUS
= ACTIVE
~~~

## 6. Governance status

~~~text
V0.2 raster visuals         = ARCHIVED
V0.2 SVG migration assets  = ARCHIVED
V0.2 render pipeline       = ARCHIVED / REMOVED
V0.2 strict execution rule = ARCHIVED
V0.3 controlled baseline   = ACTIVE
~~~

## 7. Rule

> Historical visual evidence belongs in Git history and validation documentation; only usable current visuals belong in the active assets directory.
