# Dataset Registry

Status labels are explicit:

- **Available**: publicly documented or otherwise obtained, but not necessarily
  suitable for this application.
- **Investigated**: official documentation and relevant metadata reviewed.
- **Integrated**: code retrieves and records the dataset in the application.
- **Validated**: retrieval, transformations, quality checks, and representative
  outputs have been tested against an agreed protocol.

No candidate is Integrated or Validated at the current repository state.

| Dataset/product | Provider | Status | Coverage/resolution summary | Variables/use | Access/licensing notes | Tested |
|---|---|---|---|---|---|---|
| POWER climate/solar products | NASA POWER | Investigated | Worldwide; product-specific time and spatial grids | Temperature, precipitation, radiation and related climate indicators for Arabica suitability and warnings | Use the product documentation and current terms; exact selected parameters pending | No |
| GPM IMERG | NASA/GPM | Investigated | Global precipitation; IMERG documentation reports coverage from Jan 1998 to present and multiple latency runs | Rainfall totals, timing, intensity, extremes | Product/version and PPS access rules matter; cite GPM policy | No |
| SMAP soil-moisture products | NASA/JPL and NASA DAACs | Investigated | Global products with product-specific grids; documented 3 km, 9 km, 36 km examples and daily/half-orbit products | Surface/root-zone soil moisture and quality flags | Product selection, DAAC access, and scaling/flags pending | No |
| MODIS land/vegetation product | NASA Earthdata | Available | Product-specific global coverage, temporal cadence, and pixel size | Vegetation/land-surface context for existing coffee plantations | A concrete MODIS product and terms have not been selected | No |
| SoilGrids | ISRIC | Investigated | Global maps, 250 m, six standard depth intervals | pH, organic carbon, texture, CEC, nitrogen, bulk density and uncertainty for Arabica constraints | CC BY 4.0; ISRIC currently reports REST API pause and beta caveats | No |
| FAOSTAT crop/agriculture data | FAO | Investigated | 245+ countries/territories; 1961 to most recent year per catalog description; dataset-specific resolution | Regional coffee context and plausibility checks, not field-level suitability | Dataset-specific terms and access route require confirmation | No |
| Arabica agronomy requirements | Authoritative agronomy or extension sources | Not selected | Source and geography dependent | Temperature, rainfall seasonality, elevation, soil, water, and extreme-event tolerances; intervention evidence | Source, license, and applicability must be confirmed before use | No |

“Available” in this table does not mean “approved,” “suitable,” or “ready for
production.” Add a row only with source, version, license, retrieval date,
schema/units, transformation record, and test evidence.
