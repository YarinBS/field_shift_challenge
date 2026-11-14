---
name: implement-feature
description: Implement a new feature with repository-aware planning, tests, and documentation.
---

# Implement a feature

1. Understand the requested behavior and acceptance criteria.
2. Read relevant architecture, API, decision, roadmap, and component documentation.
3. Inspect existing code and identify affected frontend, backend, model, data, and test surfaces.
4. Propose a concise implementation plan, dependencies, risks, and API-contract impact.
5. Implement incrementally using existing patterns and minimal scope.
6. Add or update focused tests and keep real, mock, and synthetic data clearly distinguished.
7. Run the smallest relevant tests, lint, type checks, and Docker validation where applicable.
8. Update directly related documentation and `docs/ROADMAP.md`.

Do not silently change established API contracts, add GPU-only dependencies, or perform
unrelated refactors. Surface failures explicitly and stop for approval before a major
architectural or destructive decision.

## Success criteria

The feature is implemented end-to-end across every affected surface, tests cover new behavior,
validation passes or failures are reported, and documentation matches the actual behavior.
