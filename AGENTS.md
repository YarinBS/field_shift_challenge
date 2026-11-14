# Project Instructions

## Mission and scope

This repository is a decision-support application for the NASA 2026 Space Apps
Challenge, “Adapting Farms with NASA Data.” The product goal is to help farmers
compare crop-rotation strategies using environmental evidence, constraints, and
transparent trade-offs. The challenge framing and the team’s proposed product
scope are not interchangeable; see [docs/MISSION.md](docs/MISSION.md).

The current repository is infrastructure-only. Do not describe planned
integrations, recommendations, or scientific claims as implemented or validated.

## Required reading

Before making architectural changes, read [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md),
[docs/API_CONTRACT.md](docs/API_CONTRACT.md), [docs/DECISIONS.md](docs/DECISIONS.md),
and [docs/ROADMAP.md](docs/ROADMAP.md). For data work, also read
[docs/DATA_SOURCES.md](docs/DATA_SOURCES.md) and [docs/DATASETS.md](docs/DATASETS.md).
For development commands and testing conventions, read
[docs/DEVELOPMENT.md](docs/DEVELOPMENT.md). Update the relevant documentation
when behavior or decisions change.

## Engineering rules

- Respect the existing frontend/backend/model/data structure.
- Prefer simple, modular, readable, testable code over premature abstraction.
- Use type hints and meaningful names; keep frontend, backend, and model responsibilities separate.
- Add or update tests for new behavior and never claim an integration works without testing it.
- Keep the API contract synchronized across frontend, backend, and documentation.
- Use Docker Compose for application lifecycle management and preserve Windows, macOS, and Linux compatibility.
- Prefer CPU-compatible defaults. Do not add GPU-only dependencies without an explicit decision.
- Never hardcode secrets, credentials, or machine-specific paths.
- Do not commit large datasets, generated data, or model weights.
- Document external sources, transformations, provenance, licenses, and retrieval/validation status.
- Never silently replace real data with synthetic or mock data. Clearly label all mock data and simulated results.
- Ask before making a major architectural decision or destructive change.

## Source of truth

- [docs/ROADMAP.md](docs/ROADMAP.md) is the progress checklist.
- [docs/DECISIONS.md](docs/DECISIONS.md) records important decisions and rationale.
- [docs/DATASETS.md](docs/DATASETS.md) is the status registry for datasets.
- [docs/API_CONTRACT.md](docs/API_CONTRACT.md) is the shared HTTP contract.

