# Decisions

This log records confirmed choices. Proposals and open questions belong in the
other documents until the team confirms them.

## Confirmed

| Date | Decision | Rationale |
|---|---|---|
| 2026-11-14 | Use a frontend/backend/model monorepo with Docker Compose as the supported lifecycle. | Matches the existing repository and gives a repeatable cross-platform runtime. |
| 2026-11-14 | Keep the current health endpoint as the only implemented API contract. | The repository is infrastructure-only; inventing domain endpoints would create unsupported commitments. |
| 2026-11-14 | Treat candidate datasets as unintegrated until retrieval and validation evidence exists. | Documentation alone does not establish suitability, access, or correctness. |
| 2026-11-14 | Prefer transparent rules/scoring before ML. | Explanations and defensibility are central, while labeled data and validation are not yet available. |

## Open decisions

The team must decide the MVP geography and crops; target users and farmer
priorities; authoritative crop requirement sources; data products and update
cadence; drought and soil-health definitions; recommendation evaluation and
expert-review protocol; API schemas/versioning; privacy and deployment model;
and whether optimization is justified after the baseline.

