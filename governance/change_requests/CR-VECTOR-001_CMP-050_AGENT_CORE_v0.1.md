# CR-VECTOR-001 — CMP-050 AI Agent Core

**ID:** CR-VECTOR-001  
**Version:** 0.1  
**Status:** IMPLEMENTED / REVIEW_REQUIRED  
**Baseline:** AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png  
**Candidate:** AGENT_MENTAL_MODEL_v0.2_source_candidate_v0.2.svg

## Objective

Migrate the first real component of the Agent Mental Model from raster-only representation to independently editable SVG objects while preserving all non-authorized regions.

## Authorized delta

Only CMP-050 AI Agent core is authorized for vector migration.

Authorized region:

~~~yaml
x: 351
y: 492
width: 724
height: 282
corner_radius: 22
~~~

Authorized changes:

- replace the visible CMP-050 panel background and border with SVG rectangles;
- migrate the title, subtitle, description and card labels/bullets to editable SVG text;
- migrate the three internal cards to editable SVG rectangles and text;
- keep the robot icon raster-preserved during this first migration;
- mask the baseline raster only inside the authorized CMP-050 region.

Everything outside CMP-050 is locked.

## Explicitly prohibited

- moving or resizing any non-CMP-050 component;
- changing agent architecture or relationships;
- changing inference, memory, tool, security or observability flows;
- modifying connectors outside the authorized region;
- redesigning the whole infographic;
- promoting the SVG to canonical source without regression review.

## Implementation result

CMP-050 now contains stable editable IDs such as:

~~~text
BOX-050-OUTER
TXT-050-001
BOX-050-PLAN
BOX-050-STATE
BOX-050-TOOLS
~~~

The robot icon remains raster-preserved as ICON-050-ROBOT-RASTER.

## Decision

The change request is technically implemented, but acceptance remains REVIEW_REQUIRED because visual and semantic regression gates have not yet been fully passed.
