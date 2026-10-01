# Agent Mental Model Visual Assets

This directory contains the current usable visual assets for the Agent Mental Model.

## Current controlled baseline

| File | Format | Resolution | Status |
|---|---|---:|---|
| AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png | PNG | 1536 × 1023 | ACTIVE / CONTROLLED BASELINE |
| AGENT_MENTAL_MODEL_v0.3_candidate_1537x1023.png | PNG | 1537 × 1023 | SUPERSEDED / provenance |
| AGENT_MENTAL_MODEL_BASELINE.yaml | YAML | — | ACTIVE pointer |

The active baseline is:

~~~text
AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png
~~~

## Legacy V0.1 assets

V0.1 remains as an earlier learning artifact and is not the active baseline.

| File | Resolution |
|---|---:|
| AGENT_MENTAL_MODEL_v0.1.webp | 512 × 341 |
| AGENT_MENTAL_MODEL_v0.1.png | 512 × 341 |
| AGENT_MENTAL_MODEL_v0.1_doc_1024x682.png | 1024 × 682 |
| AGENT_MENTAL_MODEL_v0.1_master_2048x1364.png | 2048 × 1364 |

## V0.2 retirement

V0.2 visual assets were retired from the active tree because they were not sufficiently legible and were superseded by V0.3.

They remain available through Git history and historical validation/governance records.

Retirement record:

`governance/AGENT_MENTAL_MODEL_V02_RETIREMENT_v0.1.md`

## Current derivation rule

Future strict visual changes use:

~~~text
V(n) = AGENT_MENTAL_MODEL_v0.3_baseline_1536x1023.png
V(n+1) = V(n) + AUTHORIZED_DELTA
~~~

Do not use V0.2 assets as a source for new visual derivatives.
