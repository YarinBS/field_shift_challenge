# Model

This directory is reserved for the recommendation model and its tests. The package is intentionally infrastructure-only at this stage. Backend containers add `model/src` to `PYTHONPATH`, making the eventual model package importable without coupling backend dependency installation to model dependencies.

CPU inference is the baseline requirement. Optional GPU dependencies should be introduced separately when a concrete model is selected.
