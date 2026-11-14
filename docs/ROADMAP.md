# Roadmap

This checklist is the single source of truth for project progress. Statuses:
`[x]` implemented, `[~]` partial/in progress, `[ ]` planned, `[blocked]`
blocked pending a decision or dependency.

## Implemented

- [x] Docker Compose lifecycle with backend and frontend health checks.
- [x] FastAPI `GET /api/health`.
- [x] Nginx same-origin `/api/` proxy and basic frontend health display.
- [x] Initial repository and documentation structure.

## Partially implemented

- [~] Architecture boundaries exist, but domain/data/model code is not implemented.
- [~] Candidate data-source investigation is documented; no source is integrated.

## Planned

- [ ] Select MVP geography, crops, users, and farmer priorities.
- [ ] Select and test one climate/precipitation source and one soil/vegetation source.
- [ ] Define provenance schema, quality checks, units, and aggregation windows.
- [ ] Define crop requirements and rotation constraints with authoritative references.
- [ ] Implement a small, explainable suitability and rotation baseline.
- [ ] Specify and implement versioned farm, strategy, and recommendation API schemas.
- [ ] Build frontend input, comparison, explanations, uncertainty, and provenance views.
- [ ] Add representative fixtures, integration tests, and reproducible validation.
- [ ] Conduct domain/expert review and document limitations before demo claims.

## Blocked or unresolved

- [blocked] Production recommendation claims: no validation protocol or expert
  review has been established.
- [blocked] Dataset integration: region, product selection, access terms, and
  validation criteria are not confirmed.
- [blocked] Optimization/ML selection: depends on data quality, labels, and
  baseline evaluation.

