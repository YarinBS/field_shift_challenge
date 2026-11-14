# Technical Feasibility Study: Adapting Farms with NASA Data

**Project:** Coffee suitability and interim-crop exploration  
**Prepared:** 2026-11-14  
**Status:** Recommendation for team approval; no implementation is implied

## Executive recommendation

Build a **hybrid, transparent recommendation system** for coffee:

1. A hard-constraint rules layer rejects agronomically or operationally
   infeasible options.
2. A normalized, weighted score ranks the remaining crop/cover/rotation
   strategies.
3. A small exhaustive search (or a constraint solver later) enumerates
   multi-season sequences and exposes trade-offs.
4. Every score is decomposed into climate, water, soil, rotation, risk, and
   farmer-priority components, with source, period, units, quality flags, and
   uncertainty shown to the user.

Treat AI as an explainable assistance layer, not as an unsupported oracle. Do
**not** make machine learning a dependency of the MVP. There is no labeled
farm-level dataset in the repository, and an accurate yield or soil-health
predictor cannot be established within a short hackathon. ML can be a future
research path after collecting outcomes and expert labels.

The scientifically defensible claim is: **the application compares coffee and
interim-crop strategies against explicit, sourced requirements and observed
environmental indicators over a stated horizon**. It can report suitability
signals and limiting factors; it must not claim to predict yield, prove
soil-health improvement, guarantee coffee production X years from now, or
replace local agronomic advice.

## Scope clarification: coffee is perennial

The proposal specifies coffee but does not yet select a species or geography.
This study uses Arabica coffee as a working example because its perennial
growth makes the interim-crop problem concrete; the team must confirm or
replace that assumption before treating the crop requirements as product
scope.

Arabica coffee is a perennial crop. A literal annual crop rotation that removes
coffee every season is generally not an appropriate default representation.
The MVP should therefore model one of these explicitly selected scenarios:

- **Existing coffee stand:** seasonal cover crops, intercrops, mulch/green
  manure, understory management, or renovation windows.
- **New establishment:** a pre-plant sequence followed by coffee establishment.
- **Renovation/replanting:** a longer transition with a fallow, cover, or
  annual-crop phase.

The user interface must label which scenario is being evaluated. The agronomic
rules for these scenarios require validation with a local coffee agronomist or
extension source.

## Proposed decision horizon

The farmer or demo scenario must provide the planning horizon `X` years and its
interpretation:

- **Existing stand:** continued coffee suitability and management risks over
  the horizon.
- **Establishment or renovation:** interim-crop windows before or between
  coffee planting phases.

The result should show the indicators used, the observation period, scenario
assumptions, uncertainty, and missing information. A horizon is not a
forecasting validation set.

## 1. Variables needed for meaningful recommendations

### Farm and management context

- Location, elevation, farm boundary or representative point.
- Existing crop, stand age, shade system, slope, aspect, drainage, and
  conservation practices.
- Soil test values and sampling depth: pH, organic carbon/matter, texture,
  CEC, bulk density, nitrogen, phosphorus, potassium, salinity, and drainage.
- Irrigation source, reliability, application capacity, water rights, and
  irrigation schedule.
- Planting/harvest windows, labor and equipment constraints, input budget,
  market access, and risk tolerance.
- Past crops, cover crops, residue removal, fertilizer/manure, tillage, pest
  and disease history, yields, and observed failures.

### Environmental exposure

- Temperature: seasonal mean, minimum/maximum, heat days, cold/frost
  exposure, and trends.
- Precipitation: seasonal total, dry-spell length, intensity, onset/cessation,
  and extreme rainfall.
- Water availability: soil moisture, water balance, and irrigation deficit.
- Radiation/energy and, where useful, humidity or vapor-pressure-related
  stress indicators.
- Topography, land cover, and cloud-free vegetation condition.
- Hazard exposure: drought, flood/runoff, heat, cold, erosion, and disease
  risk proxies. A proxy must be labeled as a proxy, not a diagnosis.

### Crop and rotation requirements

For each candidate crop, cover, or management practice:

- Temperature and water response range, season length, and planting calendar.
- Soil pH, texture, drainage, salinity, nutrient, and rooting requirements.
- Drought, heat, waterlogging, shade, and frost tolerance.
- Nitrogen fixation or nutrient-demand behavior where scientifically
  documented.
- Residue, rooting, erosion, pest, disease, allelopathy, and replant-disease
  interactions.
- Labor, seed, equipment, termination, and market constraints.

The requirements must be versioned and sourced. Where a requirement is only a
team assumption, the UI and report must say so.

## 2. NASA data versus external data

### NASA data that can support the MVP

| NASA product | Useful variables | Appropriate use | Important limitation |
|---|---|---|---|
| [NASA POWER](https://power.larc.nasa.gov/docs/) | Temperature, precipitation, radiation, and related climate/solar parameters | Long climate baseline and farm-location indicators | Product, grid, interpolation, units, and service resolution are parameter-specific; verify the selected request |
| [GPM IMERG](https://gpm.nasa.gov/data/imerg) | Satellite precipitation estimates and quality/latency variants | Rainfall timing, totals, intensity proxies, and dry-spell indicators | Estimates are not local gauges; early/late/final runs differ and require product/version selection |
| [SMAP](https://smap.jpl.nasa.gov/data/) | Surface/root-zone soil-moisture products and quality flags | Water-stress context and drought/water-availability proxy | Coarse pixels, retrieval uncertainty, masking, and vegetation/topography effects limit field-level inference |
| [MODIS MOD13Q1 v6.1](https://www.earthdata.nasa.gov/data/catalog/lpcloud-mod13q1-061) | NDVI/EVI and quality layers | 250 m, 16-day vegetation seasonality and anomaly context | Cloud/aerosol quality and mixed pixels; vegetation indices do not identify crop or soil health by themselves |
| [NASA Earthdata catalog](https://www.earthdata.nasa.gov/learn/find-data) | Product metadata, versions, extents, distribution links | Provenance and reproducible product selection | A catalog record is not proof of local suitability or validation |

NASA data are strongest for **environmental exposure and temporal context**.
They do not supply a complete farm management record, a soil test, local crop
requirements, or a labeled target such as yield or soil-health change.

### External or farmer-provided data required

| Need | Preferred source | Why NASA alone is insufficient |
|---|---|---|
| Soil properties and uncertainty | Field laboratory test; local soil survey; [ISRIC SoilGrids](https://isric.org/explore/soilgrids) as a coarse prior | Satellite retrievals do not replace farm sampling; SoilGrids is a prediction, not a field measurement |
| Crop requirements/calendars | Local extension, national agriculture ministry, coffee research institute, peer-reviewed agronomy | Requirements are crop- and region-specific and cannot be inferred safely from generic climate data |
| Coffee-specific management | Local agronomist, producer records, Coffee Research and Extension sources | Arabica phenology, shade, disease, renovation, and intercrop compatibility are not represented by generic Earth observation |
| Irrigation and water rights | Farmer input, irrigation controller, local authority | Remote sensing cannot establish legal availability or pump capacity |
| Rotation interactions | Agronomic literature and expert review | Soil-health effects depend on species, residue, tillage, duration, and local practice |
| Yield/economic outcomes | Farm records, trial data, or validated regional statistics such as [FAOSTAT](https://www.fao.org/faostat/en/#data) | Without labels, ML cannot be validated; regional statistics are not field-level response data |

SoilGrids is a useful fallback or prior: the official documentation describes
global 250 m maps, six standard depth intervals, fourteen soil properties, and
per-pixel uncertainty, under CC BY 4.0. Its official page currently warns that
the REST API is paused and beta, so the MVP should not depend on live API
availability.

## 3. Resolution and aggregation

### Spatial resolution

The desired decision unit is the **management zone**, not an individual
satellite pixel. For a hackathon:

- Accept a point or polygon and report the input geometry.
- Use a representative NASA POWER point or documented grid cell.
- Aggregate gridded products over the farm/zone when the product supports it.
- Present SMAP and MODIS as contextual evidence where their pixels are larger
  than the farm; do not imply field-scale precision.
- Use local soil samples or a soil map for within-farm differences when
  available.
- Do not downscale coarse observations into false 10 m precision.

MODIS MOD13Q1 provides a documented 250 m, 16-day vegetation product. SoilGrids
provides documented 250 m soil predictions. NASA product resolutions are
product-specific; record the exact product/version rather than generalizing
from the mission name.

### Temporal resolution

Use multiple windows, because a single annual average hides agronomic risk:

- **Baseline:** 10-20 years of monthly/seasonal climate summaries where
  available; use the exact available period and avoid claiming climate trends
  from a short record.
- **Recent context:** the latest 1-3 years or complete seasons, with quality
  flags and missing-data handling.
- **Operational season:** daily or weekly rainfall/soil-moisture aggregates;
  monthly temperature and water-balance features.
- **Planning horizon:** 3-5 seasons for an MVP, with a longer horizon only for
  perennial establishment or renovation.

The system should compare a candidate's requirements with distributions and
stress events, not only means. Example derived indicators include growing
season temperature, rainfall total, longest dry spell, number of heat/cold
events, soil-moisture percentile, and vegetation-index anomaly. Each indicator
needs a documented formula and quality threshold.

## 4. Translating conditions into crop suitability

Represent each crop or management option as a versioned requirement profile:

```text
requirement = {
  variable,
  unit,
  preferred_range,
  tolerable_range,
  season/window,
  penalty_or_constraint,
  source,
  confidence
}
```

For an observed feature `x`:

1. Apply a hard constraint for values outside a defensible tolerable range.
2. Within the feasible region, calculate a transparent membership score:
   1.0 in the preferred range, declining toward 0 at the tolerable boundary.
3. Aggregate by category (climate, water, soil, phenology, operations) rather
   than allowing many correlated variables to dominate.
4. Preserve limiting factors and missingness; do not treat missing data as a
   favorable value.
5. Show the observed value, requirement, source, and contribution to the
   result.

A triangular or trapezoidal membership function is adequate for an MVP. It is
not a biological response curve; call it a screening suitability score. If
requirements are uncertain, use intervals or sensitivity analysis and show
which ranking changes when the threshold changes.

## 5. Evaluating rotation over multiple seasons

Define a strategy as a sequence of management actions:

```text
strategy = [season_1_action, season_2_action, ..., season_n_action]
```

For every transition, evaluate:

- Seasonal climate and water feasibility.
- Planting/termination windows and crop duration.
- Soil-health proxy change: organic-carbon direction, ground cover, erosion
  protection, nitrogen demand/fixation, residue return, and compaction risk.
- Water use and risk accumulation.
- Rotation compatibility: same-family repetition, pest/disease break,
  replanting interval, and coffee-specific management rules.
- Labor, equipment, input, and economic feasibility.

The simplest defensible algorithm is **enumeration plus scoring**: generate
all sequences from a deliberately small candidate set, remove sequences that
violate hard constraints, score each remaining sequence, and return the
top alternatives plus a trade-off view. A 3-5-season horizon and a small set
of options keeps this computationally trivial and inspectable.

Do not call a soil proxy “soil health.” Report separate proxy dimensions and
the direction of change. Soil health is multi-dimensional, dynamic, and
site-specific; field sampling and longer trials are needed for validation.

## 6. Representing soil health

Use a dashboard of observable or modeled proxies:

- **Carbon:** soil organic carbon or organic matter level/trend, with depth and
  uncertainty.
- **Nutrients:** nitrogen balance and available nutrient measurements where
  available; avoid inferring lab nutrients from NDVI alone.
- **Structure:** bulk density, texture, infiltration/drainage observations,
  compaction and aggregate-stability evidence where available.
- **Cover/erosion:** proportion of season with ground cover, bare-soil exposure,
  slope/runoff risk, and residue retention.
- **Biological function:** only include microbial or biodiversity indicators
  if measured or supported by a documented model; otherwise mark as unknown.

For a demo score, normalize each proxy against a baseline and combine only
after labeling it as a **soil-health proxy index**. Keep the unaggregated
components visible. The index must not be presented as a validated soil-health
measurement.

## 7. Farmer priorities

Collect priorities explicitly instead of hiding them in weights:

- Soil improvement
- Drought resilience
- Water conservation
- Climate-risk reduction
- Income/market fit
- Low labor or low input
- Erosion control
- Short-term versus long-term horizon

Use sliders or ranked priorities to initialize weights, then normalize them and
show the resulting contribution. Keep non-negotiable constraints separate from
preferences. Include a sensitivity view: if small weight changes reorder the
top strategies, say so. Allow the farmer to exclude crops, set unavailable
irrigation, specify a planting window, or lock the existing coffee stand.

## 8. Approach evaluation

| Approach | Required data | Implementation | Advantages | Limitations and scientific validity | Complexity | Hackathon fit |
|---|---|---|---|---|---|---|
| **A. Rule-based engine** | Sourced crop thresholds, climate/soil indicators, calendars, hard constraints | Explicit requirement profiles, guards, and explanation objects | Highly transparent; easy to audit; works without labels | Thresholds can be brittle and region-specific; does not learn interactions; valid only as a screening model supported by sources | Low | **High**, especially for feasibility gates |
| **B. Weighted scoring** | Rule outputs plus farmer priorities and proxy definitions | Normalize features, category weights, sensitivity analysis, ranked explanations | Compares trade-offs; supports preferences; no labels required | Weights and normalization are normative; correlated variables can double-count; score is not yield | Low-medium | **High**, best ranking baseline |
| **C. Multi-objective optimization** | Reliable constraints, seasonal transitions, objective functions, horizon, costs/resources | Enumerate sequences first; optionally use linear/integer programming or Pareto search | Makes trade-offs explicit; returns Pareto alternatives; handles multi-season planning | Results are only as credible as objective functions and constraints; local interactions may be missing | Medium | **Medium**; use bounded enumeration for MVP |
| **D. Machine learning prediction** | Representative labeled yield/soil-health/outcome data, covariates, validation sites, monitoring | Feature pipeline, train/test design, calibration, uncertainty, drift monitoring | Can learn nonlinear relationships if data support them | No labeled dataset currently; transfer across regions is unsafe; opaque or spurious patterns; cannot establish causality | High | **Low**; do not use for the MVP |
| **E. Hybrid** | Rules/scoring data plus explicit optimization; ML only later as an optional calibrated component | Constraint layer -> indicators -> scoring/search -> explanations; future ML challenger | Preserves safety and interpretability while supporting sequences and preferences | More components and maintenance; requires disciplined provenance and versioning | Medium | **Highest** when limited to rules + scoring + enumeration |

### Recommended algorithm stack

1. **Quality and provenance checks:** units, ranges, timestamps, product
   version, missingness, and NASA quality flags.
2. **Feature derivation:** season windows, rolling dry spells, heat/cold
   events, water-balance proxy, soil-moisture percentile, vegetation anomaly.
3. **Requirement matching:** trapezoidal membership functions plus hard
   feasibility constraints.
4. **Rotation search:** bounded exhaustive enumeration for 3-5 seasons.
5. **Ranking:** weighted sum of category scores, with farmer-configurable
   weights and a Pareto/trade-off table.
6. **Uncertainty:** low/medium/high confidence from source quality,
   spatial mismatch, missingness, and requirement confidence; optionally run
   low/central/high threshold scenarios.

## 9. Recommended architecture

```text
farmer + farm geometry
        |
        v
request validation / scenario selection
        |
        v
source adapters (POWER, IMERG, SMAP or MODIS, soil source)
        |
        v
normalized observations + provenance + quality flags
        |
        v
derived seasonal indicators
        |
        +--> crop/management requirement profiles
        |
        v
hard constraints --> sequence enumeration --> weighted scoring
        |                                      |
        +-------------- explanations ----------+
                                               v
                         alternatives, trade-offs, uncertainty, citations
```

Keep the existing frontend/backend/model boundaries:

- **Backend:** request validation, source adapters, orchestration, and
  versioned response.
- **Model package:** pure, CPU-compatible indicator, suitability, sequence,
  and scoring functions with unit-tested fixtures.
- **Frontend:** input, scenario selection, comparison, explanations,
  assumptions, uncertainty, and provenance; no domain calculations.
- **Data layer:** raw and processed data outside Git, with retrieval metadata
  and transformation records.

The API response should include the strategy, season-by-season scores,
limiting factors, farmer-priority contributions, confidence, assumptions,
source citations, and a clear “decision support, not agronomic advice”
notice.

## 10. Required datasets for the MVP

### Minimum viable, demonstrable set

1. **NASA POWER** daily/monthly climate parameters for one selected region.
2. **One precipitation cross-check**, preferably GPM IMERG for rainfall
   timing/extremes, with product/version and quality treatment documented.
3. **One soil source:** a representative field soil test is preferred; SoilGrids
   can provide a clearly labeled coarse prior if live access/download is
   available.
4. **One vegetation context source:** MOD13Q1 only if the selected geography
   is large enough for its 250 m pixels to be meaningful; otherwise make it
   optional.
5. **Authoritative crop/management profiles:** Arabica plus a small, locally
   plausible set of cover/rotation options, reviewed by an agronomist or
   extension source.
6. **Farmer scenario input:** irrigation, soil observations, priorities,
   existing coffee scenario, and operational constraints.

SMAP should be treated as an optional drought/water-context layer, not a
required farm-scale soil-moisture measurement.

## 11. Concrete implementation plan (after approval)

### Phase 0: decisions and validation

1. Choose one geography, representative farm, and user scenario.
2. Decide whether the demo is existing coffee, establishment, or renovation.
3. Obtain authoritative local Arabica and candidate-cover requirements.
4. Define the soil-health proxy vocabulary and expert review checklist.

### Phase 1: data contract and fixtures

1. Define normalized observation schemas with units, timestamps, geometry,
   source/version, retrieval time, quality, and uncertainty.
2. Record fixed, small representative fixtures; do not commit large datasets.
3. Define formulas and tests for each derived indicator.

### Phase 2: explainable baseline

1. Implement requirement profiles and hard constraints.
2. Implement membership scoring and category aggregation.
3. Implement farmer-priority weights and sensitivity analysis.
4. Implement bounded sequence enumeration and transition rules.

### Phase 3: evidence-oriented product slice

1. Add one real source adapter at a time, beginning with POWER.
2. Add the precipitation cross-check and soil input.
3. Return provenance and limiting-factor explanations in the API.
4. Build a comparison UI for three or more strategies.

### Phase 4: validation and demo

1. Test units, missingness, quality flags, geometry mismatch, and reproducible
   ranking on fixtures.
2. Run scenario tests: drought, wet season, poor soil, no irrigation, and
   changed priorities.
3. Have a domain reviewer inspect requirements, constraints, and explanations.
4. Report what is measured, modeled, assumed, and unknown in the demo.

## 12. Assumptions requiring validation

1. The selected geography has appropriate Arabica production and a reachable
   extension or agronomy reviewer.
2. The intended intervention is a valid coffee-compatible rotation, cover,
   intercrop, establishment, or renovation scenario.
3. Candidate crop/management requirements can be sourced for that geography.
4. NASA POWER parameters and access terms meet the chosen spatial/temporal
   needs.
5. GPM IMERG adds useful information beyond POWER precipitation for the chosen
   farm and season.
6. SMAP/MODIS pixel sizes are not being misrepresented as farm-scale evidence.
7. SoilGrids availability, version, depth interval, uncertainty, and license
   are acceptable; a paused API must not be a runtime dependency.
8. A field soil test or credible local soil source can be supplied for the
   demonstration.
9. Three to five seasons are sufficient for the selected management scenario.
10. Soil-health proxies and transition rules are acceptable to an agronomist.
11. Farmer priorities can be represented as explicit weights and constraints.
12. The ranking remains stable enough under plausible threshold and weight
   changes to be useful; otherwise the application must emphasize trade-offs.
13. The demo has no hidden labels or synthetic results presented as observed
   farm outcomes.
14. Expert review and a documented validation protocol can be completed before
   making any agricultural performance claim.

## 13. Research traceability and limitations

The following official product documentation was checked on 2026-11-14:

- NASA POWER documentation: <https://power.larc.nasa.gov/docs/>
- NASA GPM IMERG overview: <https://gpm.nasa.gov/data/imerg>
- NASA SMAP data products: <https://smap.jpl.nasa.gov/data/>
- NASA Earthdata MOD13Q1 v6.1 record: <https://www.earthdata.nasa.gov/data/catalog/lpcloud-mod13q1-061>
- NASA Earthdata discovery guidance: <https://www.earthdata.nasa.gov/learn/find-data>
- ISRIC SoilGrids documentation: <https://isric.org/explore/soilgrids>
- FAOSTAT catalog: <https://www.fao.org/faostat/en/#data>

The documentation confirms product scope and published metadata; it does not
validate a particular farm, crop requirement, rotation effect, or
recommendation. Product versions, access routes, terms, units, and quality
flags must be recorded again when adapters are implemented. The repository's
existing [dataset registry](DATASETS.md) and [source registry](DATA_SOURCES.md)
remain the operational status records.

## Approval requested

Approve or revise these decisions before implementation:

1. The hybrid rules + weighted scoring + bounded sequence enumeration approach.
2. One geography and one Arabica management scenario.
3. The minimum data set and optional SMAP/MODIS layers.
4. The 3-5-season planning horizon and soil-health proxy representation.
5. The requirement for agronomic review before any performance claim.
