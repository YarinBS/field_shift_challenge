---
name: debug
description: Reproduce, diagnose, and fix technical problems across the application stack.
---

# Debug

1. Capture the exact symptom, input, environment, command, and error output.
2. Reproduce the issue when possible and inspect relevant tests, logs, Docker configuration,
   frontend, backend, model, and data boundaries.
3. Trace the behavior to a root cause before editing; distinguish facts from hypotheses.
4. Implement the smallest reasonable fix at the producer of the incorrect behavior.
5. Add a regression test when appropriate.
6. Run focused validation and verify adjacent behavior.

Do not randomly modify code, hide failures, replace real data with synthetic data, or delete
volumes/files to remove symptoms. Report the root cause, changed files, validation results,
and any remaining uncertainty.

## Success criteria

The failure is reproducible or the limitation is documented, the root cause is supported by
evidence, the fix is minimal, and the original failure no longer occurs under focused tests.
