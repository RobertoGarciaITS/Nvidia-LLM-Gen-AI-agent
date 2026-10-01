# Vector Migration Validation Report — CR-VECTOR-001 Refinement

**Report ID:** NVIDIA-VECTOR-MIGRATION-VALIDATION-001  
**Version:** 0.2  
**Candidate:** AGENT_MENTAL_MODEL_v0.2_source_candidate_v0.3.svg  
**Parent candidate:** AGENT_MENTAL_MODEL_v0.2_source_candidate_v0.2.svg  
**Baseline:** AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png  
**Render engine:** Inkscape  
**Canvas:** 2048 × 1364

## 1. Refinement objective

Reduce unauthorized visual delta while retaining editable SVG content inside CMP-050.

The v0.3 strategy preserves the original raster outer frame/glow and robot icon, while vectorizing the interior panel, title, subtitle, description and three internal cards.

## 2. Text correction

The baseline subtitle is preserved as:

> (Orquestador / Memoria / LangChain, Deep Agents)

The v0.2 candidate omitted the parentheses. v0.3 restores them.

## 3. Standardized pixel comparison

Changed-pixel percentage in this report means:

~~~text
max(|Rdelta|, |Gdelta|, |Bdelta|) > 5
~~~

| Metric | v0.2 | v0.3 |
|---|---:|---:|
| Full image MAE | 1.7137 | 1.1099 |
| Full image changed pixels | 5.0526% | 4.3249% |
| CMP-050 MAE | 21.2375 | 15.1854 |
| CMP-050 changed pixels | 59.9541% | 59.1748% |
| Outside CMP-050 MAE | 0.1743 | 0.0000 |
| Outside CMP-050 changed pixels | 0.7236% | 0.0000 |

Improvement:

- full-image MAE reduced by 35.2363%;
- CMP-050 MAE reduced by 28.4972%;
- all measurable delta outside CMP-050 was eliminated.

## 4. Gate result

| Gate | Result | Evidence |
|---|---|---|
| Canvas / aspect ratio | PASS | 2048 × 1364 unchanged |
| Scope containment | PASS | outside-CMP-050 MAE = 0.0000 |
| Semantic / text lock | PASS | labels and subtitle corrected to baseline |
| Visual fidelity | PASS_WITH_RASTER_TEXTURE_VARIANCE | geometry/content preserved; raster texture and vector text anti-aliasing remain different |
| Editability | PARTIAL_PASS | text/cards/fill editable; icon and outer frame/glow remain raster |
| Canonical source promotion | NOT READY | editability gate not fully closed |

## 5. Why pixel equality is not required inside the authorized region

The baseline itself is a 4× deterministic upscale of a 512 × 341 raster source. Native SVG text and flat fills therefore cannot reproduce the exact raster noise, compression texture and anti-aliasing pattern without ceasing to be clean vector objects.

The acceptance criterion for the authorized region is therefore semantic/structural equivalence plus bounded rendering variance, while the locked region must remain unchanged.

## 6. Decision

Candidate v0.3 is a better controlled migration baseline than candidate v0.2.

~~~text
CMP-050 VISUAL / SEMANTIC REFINEMENT = ACCEPTED
CMP-050 FULL EDITABILITY             = NOT YET COMPLETE
CANONICAL EDITABLE SOURCE            = FALSE
~~~

## 7. Next micro-step

Vectorize only:

1. ICON-050 robot icon;
2. outer frame and glow.

Then rerun the same regression gates before migrating CMP-060 or another component.
