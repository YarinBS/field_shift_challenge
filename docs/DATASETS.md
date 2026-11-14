# Dataset Registry

Status labels are explicit:

- **Available**: publicly documented or otherwise obtained, but not necessarily
  suitable for this application.
- **Investigated**: official documentation and relevant metadata reviewed.
- **Integrated**: code retrieves and records the dataset in the application.
- **Validated**: retrieval, transformations, quality checks, and representative
  outputs have been tested against an agreed protocol.

No candidate is Integrated or Validated at the current repository state.

The complete official challenge resource catalog is maintained in
[OFFICIAL_CHALLENGE.md](OFFICIAL_CHALLENGE.md). It includes NASA resources
listed by the challenge (including ECOSTRESS, Landsat, VIIRS, SRTM, and GEDI)
as well as the agricultural, soil, climate, and validation resources listed on
the Resources tab. Presence in that catalog is not an integration claim.

| Dataset/product | Provider | Status | Coverage/resolution summary | Variables/use | Access/licensing notes | Tested |
|---|---|---|---|---|---|---|
| POWER climate/solar products | NASA POWER | Investigated | Worldwide; product-specific time and spatial grids | Temperature, precipitation, radiation and related climate indicators | Use the product documentation and current terms; exact selected parameters pending | No |
| GPM IMERG | NASA/GPM | Investigated | Global precipitation; IMERG documentation reports coverage from Jan 1998 to present and multiple latency runs | Rainfall totals, timing, intensity, extremes | Product/version and PPS access rules matter; cite GPM policy | No |
| SMAP soil-moisture products | NASA/JPL and NASA DAACs | Investigated | Global products with product-specific grids; documented 3 km, 9 km, 36 km examples and daily/half-orbit products | Surface/root-zone soil moisture and quality flags | Product selection, DAAC access, and scaling/flags pending | No |
| MODIS MOD13Q1 v6.1 | NASA Earthdata/LP DAAC | Investigated | Global; 250 m; generated every 16 days | NDVI, EVI, and quality layers for vegetation context | Product record is public; confirm current Earthdata access, attribution, and quality handling before integration | No |
| SoilGrids | ISRIC | Investigated | Global maps, 250 m, six standard depth intervals | pH, organic carbon, texture, CEC, nitrogen, bulk density and uncertainty | CC BY 4.0; ISRIC currently reports REST API pause and beta caveats | No |
| FAOSTAT crop/agriculture data | FAO | Investigated | 245+ countries/territories; 1961 to most recent year per catalog description; dataset-specific resolution | Agricultural statistics and context, not necessarily field-level suitability | Dataset-specific terms and access route require confirmation | No |

“Available” in this table does not mean “approved,” “suitable,” or “ready for
production.” Add a row only with source, version, license, retrieval date,
schema/units, transformation record, and test evidence.
