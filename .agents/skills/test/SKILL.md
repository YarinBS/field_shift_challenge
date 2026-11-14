---
name: test
description: Run and report the relevant unit, integration, contract, and Docker validation.
---

# Test

1. Identify changed components and their affected behavior.
2. Read the testing conventions in `docs/DEVELOPMENT.md` and component READMEs.
3. Run focused unit and integration tests first, then relevant end-to-end or API-contract
   checks. Run Docker builds or service health checks when container behavior is affected.
4. Report exact commands, passed and failed tests, skipped coverage, and environment limits.
5. Never hide, ignore, or reinterpret failures as success.

Use the repository's configured test runner and preserve reproducible output. For a failure,
include the test name and concise diagnostic context rather than only a summary.

## Success criteria

Every affected behavior has relevant validation, all executed checks are reported accurately,
and untested behavior or blocked checks is clearly identified.
