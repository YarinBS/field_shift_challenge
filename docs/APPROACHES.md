# Approaches

## Environmental data processing

Proposed pipeline: retrieve observations for a farm location or region,
validate units and quality flags, aggregate meaningful windows (season,
month, rolling drought period), and derive rainfall patterns, temperature
trends, drought exposure, soil-moisture indicators, elevation, and terrain
constraints. Preserve provenance for every derived value. Window definitions,
future projection method, and drought metric remain to be chosen.

## Arabica suitability

Represent Arabica coffee with explicit requirements and constraints, including
temperature range, rainfall and dry-season pattern, elevation/terrain,
soil properties, water stress, and exposure to extreme heat, cold, drought, and
heavy rainfall. Compare normalized patch indicators with those requirements
and return a suitability category or score plus limiting factors. Requirements
must be sourced or clearly labeled as assumptions; they are not yet selected.

## Future suitability and interventions

Evaluate suitability for a selected future point or period over a planning
horizon of `X` years. The output should compare current baseline conditions
with projected conditions and expose the assumptions, uncertainty, and
climate factors driving any change.

For already planted coffee, return evidence-linked interventions such as shade
management, irrigation or water conservation, soil cover, erosion control, and
heat or frost preparation only when the relevant risk is present. These are
decision-support suggestions, not prescriptive agronomic advice.

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
optimization only when the data and constraints justify it. ML is not selected
and must not be introduced merely to use ML. No recommendation method is yet
scientifically validated.
