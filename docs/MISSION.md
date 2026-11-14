# Mission

## Challenge context

The project is being developed for NASA’s 2026 Space Apps Challenge,
“Adapting Farms with NASA Data.” The challenge topic concerns helping farmers
explore crop-rotation strategies that can improve soil health and adapt to
temperature, rainfall, drought, water availability, extreme weather, soil
conditions, crop requirements, planting seasons, and farmer priorities.

The official challenge requires a decision-support tool using NASA Earth
observations together with local soil information, crop characteristics, and
farmer priorities. It calls for exploration of rotation strategies and
comparison of at least three strategies, including the existing rotation, with
evidence, benefits, information gaps, and risks explained for each. Optional
challenge ideas include timelines, overlays, and rainfall/temperature
scenario sliders. See [OFFICIAL_CHALLENGE.md](OFFICIAL_CHALLENGE.md) for the
source snapshot and complete resource and offer catalog.

These are challenge requirements, not proof that this repository implements
them. The challenge does not prescribe a particular interface, algorithm,
dataset, geographic region, or level of scientific validation.

## Current solution proposal

The current proposal is a coffee-focused, AI-assisted decision-support
system. In English:

> Help farmers assess whether land where coffee is already grown is likely to
> remain suitable for coffee over a user-selected horizon of **X years**.
> Recommend interim crops or cover crops during coffee establishment or
> renovation periods to support soil quality. Use weather and local conditions
> to identify suitable interim crops, and suggest additional management aids
> that may improve crop performance.

The original Hebrew proposal is:

> מערכת מבוססת בינה מלאכותית המאפשרת לחקלאים להבין האם תוואי השטח שבו כבר
> מגדלים קפה יוכל להפיק קפה בטווח בזמן של X שנים קדימה. המערכת תמליץ על גידול
> של ייבולים בתקופות שבין שתילת קפה כדי לשפר את איכות האדמה. המערכת תתחשב
> בתנאי מזג אוויר על מנת להמליץ על גידולי ביניים מתאימים, ותמליץ על דרכים
> לשפר את איכות הגידול בעזרת עזרים נוספים.

“AI-assisted” is currently a product direction, not evidence that a machine
learning model exists. The MVP should use explainable rules and scoring unless
validated labels and a suitable evaluation set justify an ML component.
“X years” must be an explicit user input or documented scenario parameter; it
must not be presented as a validated yield forecast. “Additional aids” must be
named and sourced, such as irrigation, shade, mulch, drainage, erosion
control, or soil amendments, with costs and feasibility left visible.

## Proposed product

We propose a farmer-oriented decision-support application that will:

1. accept farm location, terrain, current coffee status, soil information,
   planning horizon, constraints, and priorities;
2. retrieve and analyze relevant NASA environmental data and local information;
3. assess future coffee-suitability indicators over the selected horizon;
4. evaluate interim crops or cover crops for establishment, renovation, or
   other explicitly selected coffee-management windows;
5. compare at least three strategies, including the existing coffee
   management/rotation;
6. provide understandable explanations of evidence, benefits, gaps, and risks;
   and
7. suggest clearly labeled, sourced management aids without presenting them as
   guaranteed yield improvements.

The MVP may use one geographic region and a limited crop set. The region, crop
set, user research, and validation protocol remain undecided.

The team-provided Hebrew slides further frame the MVP around a farmer entering
the current crop and local soil type, then comparing alternatives by water
consumption, soil health, and climate risk. A demonstration should show that
changing an important condition, especially water availability or preferred
crop, changes the comparison and its explanation. These are product and demo
requirements; they do not imply that the relevant data or recommendation logic
is implemented yet.

### Fit with the official challenge

The proposal answers the challenge directionally: it combines NASA
observations with local soil and crop information, addresses weather and water
stress, and uses interim crops to explore soil-health and resilience benefits.
It is not complete until the implementation:

- compares at least three strategies, including the current coffee practice;
- exposes farmer priorities and constraints;
- explains evidence, benefits, information gaps, and risks for every strategy;
- distinguishes coffee suitability indicators from a prediction of future
  production; and
- labels management aids as options requiring local agronomic review.

The strongest unresolved requirement is the meaning of “produce coffee” over
X years. The MVP should define measurable suitability indicators and report
uncertainty rather than claim a yield or profitability forecast.

## Guardrails

The application is intended to support exploration, not replace agronomists,
local extension services, or farm-specific professional advice. Results must
show data provenance, assumptions, uncertainty, and limitations. Unvalidated
outputs must not be presented as scientifically established agricultural advice.

## Success criteria

The team will define measurable criteria before claiming MVP readiness. At
minimum they should cover reproducibility, data quality, explanation quality,
latency, usability with representative scenarios, and expert or authoritative
review.
