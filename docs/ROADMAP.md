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

- [ ] Select MVP geography, user scenarios, and supported future horizons.
- [ ] Select and test one climate/precipitation source and one soil/vegetation source.
- [ ] Define Arabica requirements for climate, terrain, soil, water, and extreme events with authoritative references.
- [ ] Define provenance schema, quality checks, units, aggregation windows, and projection assumptions.
- [ ] Implement a small, explainable Arabica patch-suitability baseline.
- [ ] Implement climate-extreme warnings and evidence-linked coffee interventions.
- [ ] Specify and implement versioned location, suitability, warning, and intervention API schemas.
- [ ] Build frontend horizon input, suitability heatmap, explanations, uncertainty, and provenance views.
- [ ] Add representative fixtures, integration tests, and reproducible validation.
- [ ] Conduct domain/expert review and document limitations before demo claims.

## Blocked or unresolved

- [blocked] Production suitability or intervention claims: no validation
  protocol or expert review has been established.
- [blocked] Dataset integration: region, product selection, access terms, and
  validation criteria are not confirmed.
- [blocked] Optimization/ML selection: depends on data quality, labels, and
  baseline evaluation.
