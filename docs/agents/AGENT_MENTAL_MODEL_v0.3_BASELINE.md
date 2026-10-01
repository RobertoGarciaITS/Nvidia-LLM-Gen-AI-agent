# Agent Mental Model v0.3 — Current Visual Baseline

**ID:** NVIDIA-AGENT-MENTAL-MODEL-BASELINE-003  
**Version:** 0.3  
**Status:** ACTIVE / CONTROLLED BASELINE

## Current baseline

```text
docs/agents/assets/AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png
```

Resolution:

```text
1536 × 1023
```

Profile:

```text
512 × 341 × 3
```

## Why v0.3 is the baseline

V0.3 replaces v0.2 as the active visual baseline because it restores practical legibility while preserving the project mental model.

Validation results:

```text
LEGIBILITY            = PASS
SEMANTIC MODEL        = PASS
ARCHITECTURE TOPOLOGY = PASS
COMPONENT COVERAGE    = PASS
ASPECT RATIO          = PASS
NORMALIZATION         = PASS
```

## Lineage

```text
v0.2 controlled baseline
        │
        ├── historical baseline retained
        │
        └── legibility problem identified
                    │
                    ▼
v0.3 legibility candidate 1537×1023
                    │
                    ├── semantic / architecture validation PASS
                    └── deterministic 1px right-edge normalization
                                   │
                                   ▼
v0.3 CONTROLLED BASELINE 1536×1023
```

This is a controlled re-baseline. Strict pixel derivation from v0.2 is not claimed.

## Normalization evidence

```text
source dimensions:                  1537x1023
baseline dimensions:                1536x1023
retained-region absolute pixel error: 0
removed right-edge normalized mean: 0.103386
```

## Governance references

- governance/AGENT_MENTAL_MODEL_BASELINE_PROMOTION_v0.3.md
- governance/AGENT_MENTAL_MODEL_CONTRACT_v0.1.md
- governance/VISUAL_RESOLUTION_STANDARD_v0.1.md
- docs/agents/validation/AGENT_MENTAL_MODEL_V02_V03_BASELINE_COMPARISON_v0.1.md

## Future versions

All future strict visual derivatives SHOULD begin from:

```text
AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png
```

unless another explicit re-baseline decision supersedes it.
