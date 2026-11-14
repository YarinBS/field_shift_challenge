---
name: code-review
description: Review changes for correctness, maintainability, security, performance, and data provenance.
---

# Code review

Inspect the diff and relevant surrounding code for correctness, architecture, readability,
maintainability, security, performance, error handling, testing, API consistency, and data
provenance. Verify claims against tests and documentation. Prioritize concrete findings by
severity and include file paths, line locations, impact, confidence, and a suggested fix.

Check that real, mock, and synthetic data are labeled correctly and that API contracts remain
synchronized. Do not automatically modify code unless explicitly requested. If there are no
findings, say what was checked and note meaningful testing gaps.

## Success criteria

The review is evidence-based, actionable, prioritized, and complete for the requested diff;
it does not report speculative style preferences as defects.
