# Approaches

## Environmental data processing

Proposed pipeline: retrieve observations for a farm location or region,
validate units and quality flags, aggregate meaningful windows (season,
month, rolling drought period), and derive rainfall patterns, temperature
trends, drought exposure, and soil-moisture indicators. Preserve provenance for
every derived value. Window definitions and drought metric remain to be chosen.

## Crop suitability

Represent coffee and each interim crop with explicit requirements and
constraints: temperature range, water demand, season/calendar, soil properties,
and tolerance or risk signals. Compare normalized farm indicators with those
requirements over a user-selected horizon and return both fit and limiting
factors. This is a suitability assessment, not a yield forecast. Requirements
must be sourced or clearly labeled as assumptions; they are not yet selected.

## Crop rotation

Evaluate existing coffee management plus at least two alternatives, including
interim crops or cover crops during explicitly labeled establishment or
renovation windows. Compare multi-season or multi-year sequences for crop
compatibility, soil-health proxies, water requirements, climate risk, seasonal
feasibility, management aids, and farmer priorities. Return evidence,
benefits, gaps, risks, and trade-offs, not only a single score. Agronomic
interaction rules and the planning horizon remain under investigation.

## Recommendation engine options

1. **Transparent rules**: easiest to explain; can be brittle and requires
   defensible thresholds.
2. **Weighted scoring**: compares constraints and priorities; weights require
   elicitation and sensitivity analysis.
3. **Optimization**: useful for explicit multi-season constraints; requires
   reliable objective functions and feasible constraint data.
4. **Machine learning**: may identify patterns but needs representative labels,
   validation, monitoring, and explainability.

**Proposed default:** begin with rules plus transparent scoring, then add
optimization only when the data and constraints justify it. AI may help
explain or organize evidence, but ML is not selected and must not be
introduced merely to use AI. No recommendation method is yet scientifically
validated.
