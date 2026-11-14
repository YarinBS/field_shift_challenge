# Official Challenge, Resources, and Offers

This document records the official 2026 NASA Space Apps sources used to
ground the project. It separates challenge requirements from the team's
implementation choices. The pages were checked on 2026-11-14; the challenge
page warns that resources may be added before the hackathon begins, so this
catalog must be rechecked before submission.

The two Hebrew challenge slides supplied by the team on 2026-11-14 are also
treated as ground truth for the intended explanation and demonstration. They
are an interpretation and presentation aid, not a replacement for the
official challenge page.

## Official sources

- [Challenge details](https://www.spaceappschallenge.org/2026/challenges/adapting-farms-with-nasa-data/?tab=details)
- [Challenge resources](https://www.spaceappschallenge.org/2026/challenges/adapting-farms-with-nasa-data/?tab=resources)
- [2026 Global Offers](https://www.spaceappschallenge.org/2026/global-offers/)

## Challenge requirements and opportunities

The official challenge asks teams to create a decision-support tool that uses
NASA Earth observations together with local soil information, crop
characteristics, and farmer priorities. The goal is to help farmers explore
rotation strategies that could strengthen soil health and adapt farms to
changing conditions.

The challenge specifically says a tool may:

- analyze temperature, heat stress, rainfall, soil moisture, evaporation,
  frost risk, extreme precipitation, vegetation stress, and long-term water
  trends;
- harmonize datasets with different spatial and temporal resolutions;
- compare at least three rotation strategies, including the existing rotation;
- explain why each strategy was suggested, supporting evidence, possible
  benefits, information gaps, and risks requiring local farmer or expert
  review;
- expose farmer priorities such as water use, forage value, nitrogen-fixing
  potential, erosion reduction, organic-matter improvement, and market
  suitability; and
- optionally provide timelines, dataset overlays, or rainfall/temperature
  scenario sliders.

The intended outcome is supportive exploration, not a replacement for farmer
judgment or local agricultural expertise. The repository therefore must not
claim that a recommendation is validated agronomic advice unless validation
evidence and expert review have been added.

## Team-provided Hebrew slides

The slides add the following requirements and emphasis:

- The problem is agricultural decision-making under climate change: farmers
  must decide what to grow and when while considering rainfall, temperature,
  water availability, soil quality, and the practical conditions of the farm.
- The tool should combine NASA observations with local information, rather
  than present only a climate map. The local context includes soil moisture
  indicators, temperature, precipitation, local soil, and local crops.
- The output should compare alternative crop rotations using water
  consumption, soil health, and climate risk. The official page's stronger
  wording applies: show at least three strategies, including the existing
  rotation.
- The result should be an evidence-based recommendation adapted to the
  farmer's conditions, with understandable advantages and disadvantages.
- The demonstration should change an input such as the preferred crop or
  available water and show that the comparison changes. A low-water scenario
  should make the effect of water availability visible.
- The interface should let a farmer specify the soil type and current crop,
  then present alternatives and explain why the recommendation changes.
- The slides mention earlier projects, Waterwise/GaamaRamma (2024) and
  QUENARIS (2025), as examples of NASA data used for agriculture and water
  management. They are context for presentation, not dependencies or evidence
  that this repository has implemented those systems.

The slide wording “2–3 rotations” is interpreted as an illustrative comparison
range. For this project, the official challenge requirement controls: the
implemented comparison must contain at least three strategies and must include
the existing rotation.

## Official challenge resource catalog

These are the resources listed on the official Resources tab. “Candidate” does
not mean integrated or validated in this repository.

### NASA and Earth-observation resources

- [SMAP](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/smap) -
  surface soil moisture and freeze/thaw measurements.
- [GPM](https://gpm.nasa.gov/data) - precipitation rate and accumulation
  estimates, including IMERG.
- [Landsat](https://earthexplorer.usgs.gov/) - 30 m imagery and reflectance.
- [MODIS products](https://lpdaac.usgs.gov/products/) - vegetation indices and
  related land products.
- [VIIRS search](https://search.earthdata.nasa.gov/search?q=VIIRS) - imagery
  and vegetation observations.
- [NASA POWER](https://power.larc.nasa.gov/) - solar, meteorological, and
  climatology data.
- [SRTM](https://www.earthdata.nasa.gov/data/instruments/srtm) - elevation
  for terrain, runoff, and erosion context.
- [ECOSTRESS](https://ecostress.jpl.nasa.gov/data) - land-surface temperature
  and evapotranspiration-related observations.
- [NASA Earthdata](https://www.earthdata.nasa.gov/) - discovery and access
  portal for NASA data.
- [GEDI](https://gedi.umd.edu/data) - vegetation structure and biomass context.

### Agricultural, soil, climate, and validation resources

- [USDA Ag Data Commons](https://www.nal.usda.gov/services/agdatacommons)
- [USDA NRCS Web Soil Survey](https://websoilsurvey.nrcs.usda.gov/app/)
- [USDA Cropland Data Layer](https://nassgeodata.gmu.edu/CropScape/)
- [PRISM](https://prism.oregonstate.edu)
- [USDA NRCS soils data](https://www.nrcs.usda.gov/resources/data-and-reports/soils),
  including SSURGO and STATSGO2.
- [USDA NAIP](https://naip-usdaonline.hub.arcgis.com/)
- [USGS NLCD](https://www.usgs.gov/centers/eros/science/national-land-cover-database)
- [FAO GAEZ](https://gaez.fao.org)
- [CoCoRaHS](https://www.cocorahs.org/Maps)
- [USGS NWIS](https://waterdata.usgs.gov/nwis)
- [USDA Market News](https://www.ams.usda.gov/market-news)
- [USDA QuickStats](https://quickstats.nass.usda.gov)
- [OpenET](https://openetdata.org)
- [LANDFIRE](https://www.landfire.gov)
- [Sentinel-2 / Copernicus Data Space](https://dataspace.copernicus.eu)
- [ERA5](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=overview)

The official page also describes NLDAS/GLDAS as gridded meteorological
datasets; no separate link was provided there. If either is selected, record
the exact product and provider before integration.

## 2026 Global Offers

The official offers page says offers are optional, may be used in combination,
and are redeemed through **Claim Offer** after signing in. The page currently
requires login to view the offer content. Account, region, new-customer,
verification, usage, and expiration conditions are therefore not confirmed for
this team until each offer is claimed and its provider terms are reviewed.

| Offer | Potential project use | Published condition or redemption note |
|---|---|---|
| Microsoft Azure | Hosting, APIs, and cloud services | Eligible new Azure customers can receive $200 for 30 days; identity verification and a payment card may be required. |
| Microsoft Planetary Computer | Public environmental catalog and STAC API | Catalog access is public; some requests may require a free token and limits may apply. |
| Microsoft Copilot | General brainstorming and content support | Sign in through the provider; availability depends on account, region, and license. |
| GitHub Copilot | Coding, review, and development assistance | Use the provider's supported editor, CLI, or GitHub experience; plan limits apply. |
| Microsoft Teams | Team chat, meetings, and file sharing | Sign up for Teams Free with a Microsoft account. |
| Google Cloud | Hosting, Firebase, Maps, and data services | The page advertises $300 for 90 days; provider eligibility and billing terms apply. |
| Meteomatics Weather API | Weather and climate API data | The page advertises 1,000 queries per day across API features; provider terms apply. |
| Miro Education Plan | Collaboration and planning | Claim through the offer page and follow Miro eligibility rules. |
| Miro Business Plan | Collaboration and planning | Claim through the offer page and follow Miro eligibility rules. |
| Miro Board Templates | Hackathon planning and project coaching | Free hackathon template and project-coach boards are advertised. |
| Free Domain and Website Hosting | Optional public demo hosting | Claim through the offer page and verify the current provider terms before use. |

NASA states that it does not endorse non-U.S. Government entities or their
resources, and that participants must follow each provider's data-use
parameters. No offer is a project dependency; the repository remains runnable
without them.

## Repository alignment

| Official expectation | Repository status |
|---|---|
| NASA Earth observations plus local soil, crop, and farmer-priority context | `[ ]` Planned; no data adapter is integrated |
| At least three strategies, including the existing rotation | `[ ]` Planned; no recommendation endpoint exists |
| Evidence, benefits, gaps, and risks for every strategy | `[ ]` Planned; provenance and explanation schema is not implemented |
| Farmer-friendly interpretation and optional scenario exploration | `[ ]` Planned |
| Local soil/current crop inputs and visible water/crop scenario effect | `[ ]` Planned |
| Water use, soil health, and climate risk comparison | `[ ]` Planned |
| Coffee suitability over a stated X-year horizon | `[ ]` Planned; indicators and horizon semantics are not defined |
| Interim crops and clearly sourced management-aid options | `[ ]` Planned; crop rules and intervention evidence are not implemented |
| Supportive tool that does not replace local expertise | `[x]` Product guardrail documented in [MISSION.md](MISSION.md) |
| Reproducible, source-aware implementation | `[~]` Documentation exists; retrieval and validation are not yet tested |
