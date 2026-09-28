# AGENTS.md

## Purpose
Operational contract for any LLM or coding agent working in this repository.

## Context acquisition order
1. Read `README.md`.
2. Read `inventory/ARTIFACT_INVENTORY.md`.
3. Read `governance/REPOSITORY_RULES.md`.
4. Read `governance/DOCUMENTATION_LIFECYCLE.md`.
5. Identify the active learning module in `docs/LEARNING_ROADMAP.md`.
6. Review dependencies of the artifact to be changed.
7. Run a preflight before significant changes.
8. Preserve reproducible evidence.

## Agent rules
- Never invent content from an unread source.
- Distinguish SOURCE, INTERPRETATION, LAB and RESULT.
- Do not overwrite stable artifacts without version review.
- Labs declare objective, preconditions, steps, expected result and evidence.
- Prefer the simplest code that explains the concept.
- Register every new artifact in the inventory.
- Significant architectural decisions require an ADR.
- Never commit secrets, tokens or keys.
- Preserve failures as evidence.

## Workflow
```
READ → ANALYZE → PLAN → PREFLIGHT → IMPLEMENT → TEST → EVIDENCE → REVIEW → INVENTORY UPDATE
```
