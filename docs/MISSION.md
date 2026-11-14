# Mission

## Challenge context

The project is being developed for NASA’s 2026 Space Apps Challenge,
“Adapting Farms with NASA Data.” The challenge topic concerns helping farmers
understand how environmental change affects crop suitability and farm
decisions, using temperature, rainfall, drought, water availability, extreme
weather, soil conditions, and other Earth-observation evidence.

The challenge framing above is the official context available to this project.
It is not a confirmed specification for a particular interface, algorithm,
dataset, geographic region, or level of scientific validation.

## Product focus: Arabica coffee

The MVP focuses on **Coffea arabica (Arabica coffee)**. It is a farmer-oriented
decision-support application that will:

1. accept a farm location and a future planning horizon of `X` years;
2. retrieve and analyze climate, terrain, soil, and vegetation evidence;
3. estimate whether each map patch is suitable for Arabica at a selected
   future point or period;
4. show suitability as an interactive map heatmap with limiting factors;
5. warn about projected climate extremes and recommend when to prepare; and
6. suggest practical interventions for Arabica coffee that is already planted.

The system should answer two central questions:

- Is a location generally suitable for Arabica, and is it likely to remain
  suitable over the selected future horizon?
- How can a farmer improve growing conditions for an existing Arabica
  plantation?

The initial geography, exact horizon choices, intervention catalog, user
research, and validation protocol remain to be defined.

## Guardrails

The application is intended to support exploration, not replace agronomists,
local extension services, or farm-specific professional advice. Results must
show data provenance, assumptions, uncertainty, and limitations. Unvalidated
outputs must not be presented as scientifically established agricultural advice.

## Success criteria

The team will define measurable criteria before claiming MVP readiness. At
minimum they should cover reproducibility, data quality, explanation quality,
map coverage and responsiveness, warning usefulness, usability with
representative coffee scenarios, and expert or authoritative review. The
system must distinguish observed conditions from modeled future projections and
must not imply certainty about long-term suitability.
