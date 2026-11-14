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
| 2026-11-14 | Focus the MVP on Arabica coffee suitability, future climate-risk warnings, and interventions for existing coffee plantations. | This gives the challenge a concrete crop and user-facing decision while keeping the model explainable and evidence-driven. |

## Open decisions

The team must decide the MVP geography; supported future horizons and target
user scenarios; authoritative Arabica requirement and intervention sources; data
products and update cadence; drought, terrain, and extreme-event definitions;
suitability evaluation and expert-review protocol; API schemas/versioning;
privacy and deployment model; and whether optimization is justified after the
baseline.
