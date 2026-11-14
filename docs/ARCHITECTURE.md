# Architecture

## Current state

The repository is a small monorepo with independent components:

- `app/frontend/`: static browser UI served by nginx.
- `app/backend/`: FastAPI HTTP service and future integration boundary.
- `model/`: isolated importable Python package reserved for suitability and
  recommendation logic.
- `data/`: local `raw/`, `processed/`, and `external/` lifecycle directories.
- `scripts/`: cross-platform development utilities.

Docker Compose builds and runs `backend` on port 8000 and `frontend` on port
8080. Nginx proxies `/api/` to the backend over the Compose network, so browser
requests remain same-origin. The frontend depends on the backend health check.

## Target shape (proposed)

The backend should eventually separate request validation, source adapters,
normalization/derived indicators, Arabica suitability rules, climate-risk
warning generation, intervention mapping, and response serialization. The
model package should remain independently testable and CPU-compatible. The
frontend should present location and horizon inputs, the suitability heatmap,
warnings, assumptions, evidence, and interventions without owning domain
calculations.

This is a boundary proposal, not an authorization to add all layers now. Build
only the smallest slice needed by the roadmap.

## Data flow

`farm location + horizon -> source adapters -> provenance-preserving normalized
observations -> derived indicators -> Arabica suitability and risk evaluation
-> warnings/interventions -> explained API response -> frontend map and panels`

Each derived value must retain source, retrieval period, transformation, units,
and quality/uncertainty metadata where available. Raw and processed data remain
outside version control.

## Cross-cutting constraints

Use Docker Compose as the supported lifecycle. Keep configuration in
environment variables, avoid machine-specific paths, support Windows/macOS/Linux,
and prefer CPU defaults. See [docs/DATASETS.md](DATASETS.md) for status before
adding an adapter and [docs/API_CONTRACT.md](API_CONTRACT.md) before changing
interfaces.
