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

- [ ] Select MVP coffee geography, Arabica/coffee scope, users, and farmer
      priorities.
- [ ] Define the user-selected planning horizon `X` years and measurable
      coffee-suitability indicators; do not treat it as a validated yield
      forecast.
- [ ] Select and test one climate/precipitation source and one soil/vegetation source.
- [ ] Implement comparison of at least three strategies, including the existing
      rotation, with evidence, benefits, information gaps, and risks per strategy.
- [ ] Add farmer inputs for current crop, local soil type, and water
      availability; demonstrate how changing these inputs changes the
      water-use, soil-health, and climate-risk comparison.
- [ ] Define and source interim-crop and management-aid requirements for
      coffee establishment or renovation windows.
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
