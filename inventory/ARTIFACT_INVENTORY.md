# Artifact Inventory

**Registry ID:** NVIDIA-ARTIFACT-REGISTRY-001  
**Version:** 0.9  
**Status:** ACTIVE

## Status vocabulary
`PLANNED` · `DRAFT` · `ACTIVE` · `VALIDATED` · `SUPERSEDED` · `ARCHIVED` · `TO_CONSOLIDATE`

## Initial inventory

| ID | Artifact / topic | Type | Status | Target |
|---|---|---|---|---|
| INV-001 | Repository bootstrap | governance | ACTIVE | root + governance/ |
| INV-002 | NemoClaw course learning framework | learning | TO_CONSOLIDATE | docs/nemoclaw/ |
| INV-003 | NemoClaw 01a Agent Loop | lesson | TO_CONSOLIDATE | docs/nemoclaw/ |
| INV-004 | Agent workflow anatomy | guide | TO_CONSOLIDATE | docs/agents/ |
| INV-005 | NemoClaw / OpenClaw definitions | reference | TO_CONSOLIDATE | docs/nemoclaw/ |
| INV-006 | NVIDIA vs Gemini ADK equivalents | comparison | TO_CONSOLIDATE | docs/comparisons/ |
| INV-007 | Google Colab capability boundary | guide | TO_CONSOLIDATE | docs/labs/ |
| INV-008 | Master NemoClaw lesson prompt template | prompt-contract | TO_CONSOLIDATE | governance/templates/ |
| INV-009 | RAG topic map for NVIDIA/NeMoClaw | learning | TO_CONSOLIDATE | docs/rag/ |
| INV-010 | Certification learning roadmap | certification | ACTIVE | docs/LEARNING_ROADMAP.md |
| INV-011 | Agent configuration lab framework | lab | ACTIVE | labs/README.md |
| INV-012 | Source registry | governance | ACTIVE | references/SOURCE_REGISTRY.md |
| INV-013 | Agent context contract | governance | ACTIVE | AGENTS.md |
| INV-014 | Repository rules | governance | ACTIVE | governance/REPOSITORY_RULES.md |
| INV-015 | Documentation lifecycle | governance | ACTIVE | governance/DOCUMENTATION_LIFECYCLE.md |
| INV-016 | NemoClaw course setup preflight | governance | ACTIVE | governance/NEMOCLAW_COURSE_SETUP_PREFLIGHT_v0.1.md |
| INV-017 | Agent mental model contract | governance-contract | ACTIVE | governance/AGENT_MENTAL_MODEL_CONTRACT_v0.1.md |
| INV-018 | Agent mental model visual + explanation | learning-artifact | DRAFT | docs/agents/AGENT_MENTAL_MODEL_v0.1.md + assets/AGENT_MENTAL_MODEL_v0.1.webp + assets/AGENT_MENTAL_MODEL_v0.1.png + assets/AGENT_MENTAL_MODEL_v0.1_doc_1024x682.png + assets/AGENT_MENTAL_MODEL_v0.1_master_2048x1364.png |
| INV-019 | Strict baseline image V2 execution contract | governance-contract | ACTIVE | governance/STRICT_BASELINE_IMAGE_V2_EXECUTION_CONTRACT_v0.1.md |
| INV-020 | Agent mental model visual v0.2 — strict derivative of v0.1 | visual-artifact | DRAFT | docs/agents/assets/AGENT_MENTAL_MODEL_v0.2.webp + docs/agents/assets/AGENT_MENTAL_MODEL_v0.2.png + docs/agents/assets/AGENT_MENTAL_MODEL_v0.2_doc_1024x682.png + docs/agents/assets/AGENT_MENTAL_MODEL_v0.2_master_2048x1364.png |
| INV-021 | Visual resolution standard | governance-standard | ACTIVE | governance/VISUAL_RESOLUTION_STANDARD_v0.1.md + docs/agents/assets/README.md |
| INV-022 | Agent mental model raster rendition pipeline | ci-pipeline | ACTIVE | .github/workflows/convert-agent-mental-model-png.yml |
| INV-023 | Vector source migration contract | governance-contract | ACTIVE | governance/VECTOR_SOURCE_MIGRATION_CONTRACT_v0.1.md |
| INV-024 | Agent mental model SVG source candidate + manifest | visual-source-candidate | DRAFT | docs/agents/assets/AGENT_MENTAL_MODEL_v0.2_source_candidate.svg + docs/agents/assets/AGENT_MENTAL_MODEL_VECTOR_SOURCE_MANIFEST_v0.1.yaml + docs/agents/assets/AGENT_MENTAL_MODEL_v0.2_source_candidate_v0.2.svg + docs/agents/assets/AGENT_MENTAL_MODEL_VECTOR_SOURCE_MANIFEST_v0.2.yaml |
| INV-025 | CR-VECTOR-001 CMP-050 AI Agent core migration | change-request | REVIEW_REQUIRED | governance/change_requests/CR-VECTOR-001_CMP-050_AGENT_CORE_v0.1.md |
| INV-026 | CR-VECTOR-001 vector migration validation report | validation-report | REVIEW_REQUIRED | docs/agents/validation/VECTOR_MIGRATION_CR-VECTOR-001_REPORT_v0.1.md |

## Historical knowledge migration queue
Prior project conversations contain work on NemoClaw/OpenClaw, 01a loop, agent workflow anatomy, lesson prompt templates, NVIDIA/ADK comparisons, Colab constraints, first-agent research and RAG. These items must be migrated by reviewing their original source and conversation evidence rather than reconstructed from memory.

## Rule
Every added artifact, status promotion, supersession or archival action updates this registry.
