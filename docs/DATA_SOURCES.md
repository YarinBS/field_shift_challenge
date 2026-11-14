# Data Sources

This is a candidate-source investigation, not a claim that every source will
be used. Official documentation is the primary reference. Access, licensing,
version, and product-level caveats must be rechecked before integration.

The official challenge's complete Resources-tab catalog is maintained in
[OFFICIAL_CHALLENGE.md](OFFICIAL_CHALLENGE.md). The records below are the
smaller set investigated in more detail by this repository; they are not a
replacement for that official catalog.

## Candidate records

The fields below deliberately say “confirm” where the official source is
product-specific or where this repository has not tested an access path.

### NASA POWER

- **Documentation:** [POWER Docs](https://power.larc.nasa.gov/docs/); [API tutorial](https://power.larc.nasa.gov/docs/tutorials/api-getting-started/)
- **Coverage/resolution:** Worldwide point and gridded services; temporal and spatial resolution are parameter/product-specific and must be recorded for the selected request.
- **Variables:** Candidate temperature, precipitation, radiation, and related climate/solar parameters.
- **Access/authentication:** Documented web services; authentication requirement for the selected service is not established.
- **License/restrictions:** Confirm current POWER terms and citation requirements before redistribution.
- **Formats:** Service response format is request-specific; confirm selected JSON/CSV or other format.
- **Potential use:** Climate baselines, rainfall patterns, temperature trends, and solar context.
- **Limitations:** Product lineage, interpolation, units, missing values, and parameter availability must be checked.
- **Status:** Documentation inspected; API not tested.

### NASA GPM IMERG

- **Documentation:** [Precipitation Data Directory](https://gpm.nasa.gov/data/directory); [data policy](https://gpm.nasa.gov/data/policy)
- **Coverage/resolution:** Global precipitation; the directory reports Jan 1998 to present for IMERG and multiple latency runs. Product-specific temporal/spatial resolution must be recorded.
- **Variables:** Precipitation estimates, with product/version and quality information to be confirmed.
- **Access/authentication:** HTTPS/FTPS product access; some PPS access requires registration.
- **License/restrictions:** Follow the GPM data policy and product citation instructions.
- **Formats:** Product/download format is product-specific and must be confirmed.
- **Potential use:** Rainfall totals, timing, intensity, extremes, and drought indicators.
- **Limitations:** Early, late, and final runs differ in latency and quality; estimates are not local gauges.
- **Status:** Documentation inspected; API/download not tested.

### NASA SMAP

- **Documentation:** [SMAP data](https://smap.jpl.nasa.gov/data/); [NSIDC SMAP data](https://nsidc.org/data/smap)
- **Coverage/resolution:** Global products with product-specific coverage; documented examples include 3 km, 9 km, and 36 km grids and half-orbit/daily products.
- **Variables:** Surface and root-zone soil moisture, freeze/thaw, and quality flags depending on product.
- **Access/authentication:** NASA DAAC distribution; exact product and credentials depend on the selected DAAC/service.
- **License/restrictions:** Confirm product-specific NASA/DAAC data-use and citation terms.
- **Formats:** Product-specific scientific formats; confirm before implementation.
- **Potential use:** Soil-moisture context and drought/water-availability indicators.
- **Limitations:** Coarse spatial resolution, retrieval uncertainty, masking, and product scaling/flags require validation.
- **Status:** Documentation inspected; access not tested.

### NASA MODIS

- **Documentation:** [Earthdata Search](https://search.earthdata.nasa.gov/); [MODIS data](https://modis.gsfc.nasa.gov/data/)
- **Coverage/resolution:** Global products with product-specific temporal cadence and pixel size; no product has been selected.
- **Variables:** Candidate vegetation indices, land-surface, and reflectance observations.
- **Access/authentication:** Earthdata/DAAC services; product and credential requirements vary.
- **License/restrictions:** Confirm product-specific NASA Earthdata terms and attribution.
- **Formats:** Product-specific scientific formats; confirm selected product format.
- **Potential use:** Vegetation/land-surface context and seasonal signals.
- **Limitations:** Cloud contamination, revisit/cadence, land-cover interpretation, and product quality flags matter.
- **Status:** Candidate only; product selection and access not tested.

### NASA MODIS MOD13Q1 v6.1 (selected candidate)

- **Documentation:** [Earthdata product record](https://www.earthdata.nasa.gov/data/catalog/lpcloud-mod13q1-061)
- **Coverage/resolution:** Global product generated every 16 days at 250 m; confirm the selected granule and coverage for the MVP geography.
- **Variables:** NDVI, EVI, and associated quality layers.
- **Access/authentication:** NASA Earthdata/LP DAAC distribution; account and distribution route must be confirmed before integration.
- **License/restrictions:** Follow current Earthdata/LP DAAC terms and attribution requirements.
- **Formats:** Product distribution format is product-specific and must be confirmed.
- **Potential use:** Seasonal vegetation context and anomaly features, never a standalone crop or soil-health measurement.
- **Limitations:** Clouds, aerosols, quality flags, mixed pixels, and phenology confounding require masking and cautious interpretation.
- **Status:** Product documentation inspected 2026-11-14; access and representative retrieval not tested.

### NASA Earthdata discovery services

- **Documentation:** [Find data](https://www.earthdata.nasa.gov/learn/find-data); [Earthdata Search/API resources](https://www.earthdata.nasa.gov/learn/find-data/earthdata-search)
- **Coverage/resolution:** Discovery metadata spans many NASA missions; these values belong to the selected dataset, not Earthdata itself.
- **Variables:** Metadata, spatial/temporal extents, variables, versions, and distribution links.
- **Access/authentication:** Account/token requirements vary by service and product.
- **License/restrictions:** Inherited from each dataset/product; discovery does not grant redistribution rights.
- **Formats:** Metadata and distribution formats vary.
- **Potential use:** Dataset discovery, version tracking, and provenance.
- **Limitations:** A catalog record is not proof of suitability, availability, or validation.
- **Status:** Discovery resources inspected; no dataset integrated.

### SoilGrids / ISRIC

- **Documentation:** [SoilGrids](https://isric.org/explore/soilgrids); [FAQ](https://docs.isric.org/globaldata/soilgrids/SoilGrids_faqs.html)
- **Coverage/resolution:** Global maps at 250 m for six standard depth intervals.
- **Variables:** pH, organic carbon, bulk density, coarse fragments, sand, silt, clay, CEC, total nitrogen, organic-carbon density/stock, and prediction uncertainty.
- **Access/authentication:** Public maps and documented services; the official page currently reports that the REST API is paused and is beta software.
- **License/restrictions:** CC BY 4.0; preserve attribution and check current terms.
- **Formats:** Service/download format is route-specific and must be confirmed.
- **Potential use:** Soil constraints, crop requirements, and soil-health context.
- **Limitations:** Predictions and uncertainty are not field measurements; depth aggregation and API availability require care.
- **Status:** Documentation inspected; REST access not tested.

### FAOSTAT

- **Documentation:** [FAOSTAT data](https://www.fao.org/faostat/en/#data)
- **Coverage/resolution:** Catalog describes 245+ countries/territories and 1961 to the most recent year; dataset-specific geographic/temporal resolution varies.
- **Variables:** Agricultural statistics and contextual crop information; selected variables remain open.
- **Access/authentication:** Public web data access; dataset-specific API and authentication details require confirmation.
- **License/restrictions:** Confirm FAO dataset-specific terms and citation requirements.
- **Formats:** Download/API format is dataset-specific and must be confirmed.
- **Potential use:** Regional crop context and plausibility checks, not automatically field-level suitability.
- **Limitations:** Statistics may not represent a particular farm or provide agronomic requirements.
- **Status:** Catalog inspected; no data retrieved.

### Regional or government agriculture data

- **Provider/documentation:** To be selected for the MVP region.
- **Coverage/resolution:** Expected to be locally relevant; temporal/spatial resolution is unknown until a source is selected.
- **Variables:** Candidate crop calendars, advisories, water restrictions, soil surveys, and crop requirements.
- **Access/authentication:** To be determined by provider.
- **License/restrictions:** Must be confirmed before use or redistribution.
- **Formats:** To be determined.
- **Potential use:** Local calibration and farmer-relevant constraints.
- **Limitations:** Region, authority, update cadence, and data quality are unknown.
- **Status:** Not selected or tested.

## Source-selection rules

Prefer authoritative, documented products with known units, temporal/spatial
resolution, stable access, and terms compatible with the project. Compare
overlapping sources rather than silently merging them. Record product/version,
retrieval date, query parameters, transformations, quality flags, and license
at ingestion time.

## Research gaps

The team still must choose the MVP region and products, verify current
endpoints, confirm authentication and redistribution terms, establish a
validation protocol, and decide how to reconcile satellite, modeled, and local
observations.
