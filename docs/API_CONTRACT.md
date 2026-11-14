# API Contract

The contract currently contains only the implemented health endpoint. Future
endpoints must be specified here before frontend/backend integration.

## Implemented

`GET /api/health`

Response `200`:

```json
{"status": "ok", "service": "backend"}
```

The frontend calls this path through nginx at the same origin. FastAPI also
publishes interactive documentation at `/docs` while running.

## Proposed future shape

Potential resources include farm profile, environmental observations,
candidate crops, rotation strategies, and recommendation explanations. Names,
schemas, units, error formats, authentication, rate limits, and versioning are
not decided. Do not implement them as if this section were a specification.

Any future response should expose assumptions, source/product/version,
observation period, units, quality/uncertainty, transformation summary, and
whether values are observed, modeled, simulated, or unavailable.

## Change rule

Update this document, backend tests, and frontend consumers together. Prefer
backward-compatible additive changes; document intentional breaking changes in
[docs/DECISIONS.md](DECISIONS.md).

