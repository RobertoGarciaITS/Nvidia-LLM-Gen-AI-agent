# Agent Mental Model Baseline Promotion — v0.3

**ID:** NVIDIA-AGENT-MENTAL-MODEL-BASELINE-PROMOTION-003  
**Version:** 0.1  
**Status:** ACTIVE  
**Decision:** PROMOTE V0.3 AS CURRENT CONTROLLED VISUAL BASELINE

## 1. Decision

The project promotes:

```text
docs/agents/assets/AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png
```

as the current controlled visual baseline for the Agent Mental Model.

The previous v0.2 baseline is retained as historical evidence and lineage context in Git history and validation documentation, but is no longer present in the active visual-assets tree.

## 2. Promotion type

This is a **CONTROLLED RE-BASELINE**, not a claim of strict pixel lineage from v0.2.

Reason:

- v0.2 became insufficiently legible for normal human review;
- v0.3 restored practical readability;
- semantic and architectural validation against the canonical mental-model contract passed;
- exact image-to-image lineage from v0.2 could not be proven for the newly generated legible candidate;
- governance therefore records an explicit baseline reset rather than inventing a false strict derivation claim.

## 3. Final normalized artifact

Source candidate:

```text
AGENT_MENTAL_MODEL_v0.3_candidate_1537x1023.png
1537 × 1023
```

Promoted baseline:

```text
AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png
1536 × 1023
```

Normalization:

```text
AUTHORIZED_DELTA = remove exactly 1 pixel from far-right outer margin
retained region  = x=0..1535, y=0..1022
pixel error       = 0
```

The retained 1536 × 1023 region is pixel-identical to the source candidate.

## 4. Resolution profile

The promoted baseline uses an exact 3× multiple of the original locked profile:

```text
512 × 341
× 3
──────────
1536 × 1023
```

Therefore:

```text
ASPECT_RATIO(v0.3 baseline) = ASPECT_RATIO(512×341)
```

The geometry gate is closed.

## 5. Validation gates

| Gate | Result |
|---|---|
| Legibility | PASS |
| Semantic model | PASS |
| Architecture topology | PASS |
| Component coverage | PASS |
| Visual structure | PASS_WITH_VARIANCE |
| Exact baseline aspect ratio | PASS |
| Controlled normalization | PASS |
| Retained-region pixel identity | PASS |
| Strict v0.2 pixel lineage | NOT CLAIMED |
| Re-baseline governance decision | PASS |
| Baseline promotion | PASS |

## 6. Canonical status

```text
CURRENT_VISUAL_BASELINE = v0.3
BASELINE_FILE           = AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png
BASELINE_RESOLUTION     = 1536 × 1023
PROMOTION_TYPE          = CONTROLLED_REBASELINE
PREVIOUS_BASELINE       = v0.2
```

## 7. Historical preservation

V0.2 visual files and SVG experiments have been retired from the active tree because they are obsolete and insufficiently legible.

Auditability is preserved through Git history, validation reports, comparison records and:

`governance/AGENT_MENTAL_MODEL_V02_RETIREMENT_v0.1.md`

The active assets directory MUST NOT present V0.2 as a usable current visual source.

## 8. Future derivation rule

Any future v0.4+ visual that claims strict derivation MUST use the promoted v0.3 baseline as its visual source unless a new controlled re-baseline decision is explicitly approved.

```text
V(n+1) = V(n) + AUTHORIZED_DELTA
```

For strict v0.4 derivation:

```text
V(n) = AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png
```

## 9. Absolute rule

> V0.3 becomes the new visual baseline because its semantic model is validated and its legibility is materially better; the project records this honestly as a controlled re-baseline rather than misrepresenting it as a strict pixel derivative of V0.2.
