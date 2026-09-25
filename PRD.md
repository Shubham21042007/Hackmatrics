# PRD.md

# Urban Air Quality Digital Twin

**Project Type:** Hackathon / Urban Environmental Intelligence Platform\
**Primary Domain:** Air Quality, GIS, Machine Learning, Digital Twin,
What-if Simulation\
**Pilot Geography:** Defined urban area, with Pune / Pimpri-Chinchwad as
the recommended pilot boundary\
**Primary Pollutant for MVP:** PM2.5\
**Core Product Flow:** **OBSERVE → PREDICT → EXPLAIN → SIMULATE →
COMPARE → VALIDATE**

------------------------------------------------------------------------

## 1. Executive Summary

Urban air-quality systems commonly show pollution levels after they have
already occurred. They may provide AQI or pollutant readings, but they
often do not provide a unified way to understand:

-   where pollution is concentrated,
-   how weather, traffic, and industrial activity are associated with
    pollution,
-   where pollution is likely to move next,
-   which factors have the strongest modeled influence,
-   what could happen if an intervention is applied,
-   whether a proposed intervention reduces pollution under the model
    assumptions,
-   and whether the forecasting system actually works on historical
    periods.

This project builds a **map-based Urban Air Quality Digital Twin**.

The system represents a defined urban area as a continuously updated
digital model using observed air-quality, weather, traffic-related,
industrial-activity-related, temporal, and geospatial information.

The platform will:

1.  ingest and harmonize multi-source urban data,
2.  display observed air-quality conditions on an interactive map,
3.  forecast PM2.5 levels,
4.  predict potential pollution hotspots,
5.  explain model-attributed influence from at least three source/factor
    categories,
6.  simulate interventions such as traffic reduction and industrial
    controls,
7.  compare baseline and intervention scenarios,
8.  validate predictions against historical test periods,
9.  clearly distinguish observed data, forecasts, and modeled scenarios.

The system is not intended to claim direct causal source apportionment
unless direct emissions measurements support such a claim. Source
influence will be presented as **model-attributed influence under stated
assumptions**.

------------------------------------------------------------------------

# 2. Problem Statement

City-level air-quality tracking often shows where pollution is high
without explaining which interventions would actually help.

The proposed system connects air-quality observations with:

-   weather,
-   traffic indicators,
-   industrial activity indicators,
-   spatial information,
-   temporal patterns,
-   and historical observations

to forecast pollution, estimate modeled influence across source/factor
categories, and compare possible interventions.

### Required outcomes

The final system must:

1.  Forecast at least one air-quality indicator for a defined urban
    area.
2.  Attribute modeled influence across at least three source/factor
    categories with explicit assumptions.
3.  Compare at least three possible actions to reduce pollution.
4.  Display pollution hotspots on a map.
5.  Validate forecasts against historical test periods.
6.  Clearly label **Observed**, **Forecast**, and **Modeled Scenario**
    results throughout the demo.

------------------------------------------------------------------------

# 3. Product Vision

## Vision

> Build an interactive digital representation of an urban area that can
> observe pollution, predict future conditions, explain modeled
> influences, and simulate potential interventions before they are
> implemented.

## Product tagline

**Urban Air Quality Digital Twin**\
**Observe. Predict. Explain. Simulate.**

## One-line description

A data-driven urban model that does not only show pollution hotspots,
but forecasts where pollution may increase, explains the modeled
influence of major factors, and lets users test intervention scenarios
before acting.

------------------------------------------------------------------------

# 4. Goals

## 4.1 Primary Goals

-   Create a functional map-based urban digital twin.
-   Forecast PM2.5 for the selected urban area.
-   Produce spatial pollution/hotspot visualization.
-   Integrate air quality and weather data.
-   Include traffic-related and industrial-activity-related indicators.
-   Provide explainable ML results.
-   Support at least three intervention scenarios.
-   Re-run the prediction model for what-if scenarios.
-   Compare baseline and intervention outcomes.
-   Validate predictions using historical time periods.
-   Maintain complete separation between observed and modeled
    information.

## 4.2 Secondary Goals

-   Historical replay of pollution conditions.
-   Prediction confidence / uncertainty visualization.
-   Pollution cause explanation.
-   Emerging hotspot detection.
-   Scenario impact heatmaps.
-   Real-time or near-real-time updates when data availability permits.
-   Multi-pollutant support after PM2.5 MVP is stable.

## 4.3 Stretch Goals

-   Satellite data integration.
-   IoT sensor integration.
-   Automated intervention optimization.
-   Multi-city support.
-   Natural-language querying.
-   Automated scenario generation.
-   Advanced spatial ML.
-   Public reporting interface.

------------------------------------------------------------------------

# 5. Non-Goals

The following are explicitly outside the mandatory MVP:

-   Building a full 3D city engine.
-   Claiming exact physical emissions from every vehicle or factory.
-   Claiming scientifically validated causal source apportionment
    without appropriate emissions data.
-   Replacing official government air-quality monitoring.
-   Making policy decisions automatically.
-   Deploying highly complex deep-learning architectures before a
    reliable baseline exists.
-   Supporting every pollutant and every city in the first version.

The project should prioritize **working prediction + explainability +
simulation + GIS visualization** over unnecessary technical complexity.

------------------------------------------------------------------------

# 6. Core Product Concept: Digital Twin

A dashboard only displays information.

A digital twin should represent the real system and connect that
representation to data, prediction, and simulation.

For this project:

``` text
REAL URBAN ENVIRONMENT
        │
        ├── Air Quality
        ├── Weather
        ├── Traffic Indicators
        ├── Industrial Indicators
        ├── Roads / Land Use
        └── Historical Patterns
        │
        ▼
DIGITAL CITY MODEL
        │
        ├── Current State
        ├── Forecast
        ├── Influence Analysis
        └── What-if Simulation
        │
        ▼
DECISION SUPPORT
        │
        ├── Baseline
        ├── Scenario A
        ├── Scenario B
        ├── Scenario C
        └── Comparison
```

The digital twin does not need to be 3D.

A **2D GIS-based spatial digital twin** is sufficient and preferred for
the project because it directly supports pollution hotspots, roads,
monitoring locations, industrial areas, and intervention visualization.

------------------------------------------------------------------------

# 7. Product Architecture

## High-Level Architecture

``` text
                    DATA SOURCES
                         │
       ┌─────────────────┼─────────────────┐
       │                 │                 │
   Air Quality       Weather          Urban Data
       │                 │          ┌──────┴──────┐
       │                 │       Traffic      Industry
       └─────────────────┼──────────┬─────────────┘
                         │
                         ▼
                DATA INGESTION LAYER
                         │
                         ▼
              DATA CLEANING / ALIGNMENT
                         │
                         ▼
              SPATIOTEMPORAL DATA LAYER
                         │
              ┌──────────┴──────────┐
              │                     │
              ▼                     ▼
       FEATURE ENGINEERING      GIS PROCESSING
              │                     │
              └──────────┬──────────┘
                         │
                         ▼
                  ML MODEL LAYER
             ┌───────────┼───────────┐
             │           │           │
             ▼           ▼           ▼
         Forecast     Hotspots    Explanation
             │           │           │
             └───────────┼───────────┘
                         │
                         ▼
                  DIGITAL TWIN
                         │
             ┌───────────┼───────────┐
             │           │           │
             ▼           ▼           ▼
          Observe     Simulate    Compare
                         │
                         ▼
                SCENARIO ENGINE
                         │
                         ▼
                  WEB DASHBOARD
```

------------------------------------------------------------------------

# 8. Core User Journey

The complete product experience follows:

## Step 1: OBSERVE

User opens the digital twin and sees:

-   current PM2.5,
-   PM10 / other available pollutants,
-   monitoring locations,
-   pollution hotspots,
-   weather,
-   roads,
-   traffic indicators,
-   industrial areas,
-   historical conditions.

Every measured value is marked **OBSERVED**.

------------------------------------------------------------------------

## Step 2: PREDICT

User selects a forecast horizon.

Example:

-   Next 1 hour
-   Next 3 hours
-   Next 6 hours
-   Next 12 hours
-   Next 24 hours

The system predicts PM2.5.

The map changes from:

**Observed Pollution**

to:

**Forecast Pollution**

Forecast values are never presented as observations.

------------------------------------------------------------------------

## Step 3: EXPLAIN

The user selects a location or hotspot.

The system shows model-attributed influence from at least:

1.  Traffic-related factors
2.  Industrial-activity-related factors
3.  Weather / meteorological factors

Additional categories:

-   historical pollution,
-   time of day,
-   day of week,
-   spatial characteristics,
-   seasonal effects.

The UI must explain:

> These values represent model-attributed influence under the defined
> assumptions. They are not direct measurements of emissions or
> definitive causal source apportionment.

------------------------------------------------------------------------

## Step 4: SIMULATE

The user changes intervention parameters.

Examples:

-   Traffic reduction: 10%, 20%, 30%, 50%
-   Industrial activity reduction: 10%, 20%, 30%
-   Combined traffic + industrial control
-   Optional temporary restriction around selected zones

The system modifies relevant model inputs and runs the prediction again.

It must not simply hard-code a pollution reduction percentage.

------------------------------------------------------------------------

## Step 5: COMPARE

The system compares:

``` text
BASELINE
vs
SCENARIO A
vs
SCENARIO B
vs
SCENARIO C
```

Comparison can include:

-   predicted average PM2.5,
-   peak PM2.5,
-   number/area of hotspots,
-   predicted reduction,
-   spatial impact,
-   affected regions,
-   intervention parameters.

------------------------------------------------------------------------

## Step 6: VALIDATE

User can open historical periods.

The system compares:

``` text
ACTUAL OBSERVED
vs
MODEL PREDICTION
```

Metrics:

-   MAE
-   RMSE
-   R²
-   optionally MAPE where appropriate

The test period must be chronologically separated from training data.

------------------------------------------------------------------------

# 9. Complete Feature Set

## 9.1 Data Ingestion

### Feature: Multi-source data ingestion

Support configurable ingestion from:

-   Air-quality APIs/datasets
-   Government air-quality datasets
-   Weather APIs/datasets
-   Municipal traffic datasets where available
-   OpenStreetMap / geospatial data
-   Industrial-area / land-use data
-   Historical datasets
-   Optional IoT sensors

### Requirements

-   CSV import
-   API ingestion
-   Scheduled data refresh
-   Timestamp normalization
-   Coordinate normalization
-   Missing-value handling
-   Duplicate detection
-   Data validation
-   Source metadata

------------------------------------------------------------------------

# 10. Air Quality Monitoring

## Pollutants

Primary:

-   PM2.5

Secondary:

-   PM10
-   NO2
-   SO2
-   CO
-   O3
-   AQI where available

## Features

-   Current readings
-   Historical readings
-   Monitoring-station locations
-   Time-series charts
-   Pollutant selection
-   Station comparison
-   Map visualization
-   Data quality indicators

------------------------------------------------------------------------

# 11. Weather Integration

Weather features:

-   Temperature
-   Relative humidity
-   Wind speed
-   Wind direction
-   Rainfall
-   Surface pressure
-   Atmospheric / boundary-layer information when available
-   Weather condition

Weather is important because pollution concentration and movement are
strongly influenced by atmospheric conditions.

------------------------------------------------------------------------

# 12. Traffic Intelligence

Traffic data may not always be available at the required spatial and
historical resolution.

Therefore the system supports two levels:

### Level A: Observed traffic data

When actual traffic data is available:

-   vehicle count,
-   traffic speed,
-   congestion index,
-   road occupancy,
-   traffic volume.

### Level B: Traffic indicators / proxies

When direct traffic measurements are unavailable:

-   road density,
-   road class,
-   major-road proximity,
-   road network density,
-   time-of-day traffic patterns,
-   weekday/weekend pattern,
-   defined traffic index.

Every proxy must be clearly documented as a proxy.

The system must not present a traffic proxy as measured traffic.

------------------------------------------------------------------------

# 13. Industrial Activity Intelligence

Industrial information may be represented through:

-   industrial zone locations,
-   industrial land-use density,
-   distance to industrial areas,
-   industrial facility density,
-   industrial activity index,
-   available emissions/activity datasets.

The model can create an:

**Industrial Activity Index**

based on available data.

Assumptions must be visible in the project documentation and, where
relevant, in the UI.

The index is not equivalent to direct factory emissions.

------------------------------------------------------------------------

# 14. Interactive GIS Map

The map is the central interface of the digital twin.

## Layers

### Air Quality

-   PM2.5
-   PM10
-   AQI
-   NO2
-   Other supported pollutants

### Infrastructure

-   Roads
-   Major roads
-   Monitoring stations
-   Administrative boundaries

### Urban Activity

-   Traffic indicators
-   Industrial zones
-   Industrial activity indicators

### Weather

-   Wind direction
-   Wind speed
-   Temperature
-   Rainfall

### Prediction

-   Forecast pollution
-   Predicted hotspots
-   Forecast confidence

### Scenario

-   Baseline
-   Scenario A
-   Scenario B
-   Scenario C
-   Scenario impact

------------------------------------------------------------------------

# 15. Pollution Hotspot Detection

The system identifies areas with elevated pollution.

Possible approaches:

-   threshold-based hotspot detection,
-   spatial interpolation,
-   grid-based prediction,
-   clustering,
-   local spatial statistics,
-   ML-based spatial prediction.

MVP approach:

1.  divide the urban area into spatial cells,
2.  aggregate available observations,
3.  estimate pollution for cells,
4.  identify high-value cells,
5.  display them as hotspots.

The system should distinguish:

**Observed Hotspot**

from

**Forecast Hotspot**

from

**Scenario Hotspot**.

------------------------------------------------------------------------

# 16. PM2.5 Forecasting

## Primary prediction target

**PM2.5**

## Initial prediction horizons

-   1 hour
-   3 hours
-   6 hours

Optional:

-   12 hours
-   24 hours

## Features

### Temporal

-   current PM2.5
-   lagged PM2.5
-   rolling mean
-   rolling maximum
-   hour
-   day of week
-   month
-   season

### Weather

-   temperature
-   humidity
-   wind speed
-   wind direction
-   rainfall
-   pressure
-   boundary-layer-related variables if available

### Urban

-   traffic index
-   road density
-   industrial index
-   distance to major roads
-   distance to industrial zones

### Spatial

-   latitude
-   longitude
-   grid ID
-   neighboring pollution values
-   station proximity

------------------------------------------------------------------------

# 17. ML Model Strategy

## Baseline

Start with simple models.

Recommended order:

1.  Persistence / last-value baseline
2.  Linear Regression
3.  Random Forest
4.  XGBoost or LightGBM

The final MVP model can be selected using historical validation.

The project should not introduce deep learning unless it demonstrably
improves the result.

## Why tree-based models

Tree-based models handle:

-   nonlinear relationships,
-   mixed feature types,
-   interactions,
-   missing values after preprocessing,
-   relatively small/medium datasets,

and are easy to explain using SHAP.

------------------------------------------------------------------------

# 18. Time-Series Validation

Random train-test splitting must not be the primary validation strategy.

Use chronological splits.

Example:

``` text
Historical Data
│
├── Training Period
│
├── Validation Period
│
└── Final Test Period
```

Example:

``` text
Jan ─────── Jun     Jul ─── Aug     Sep
TRAINING           VALIDATION     TEST
```

The exact dates depend on the final dataset.

The test period must not be used for model training.

------------------------------------------------------------------------

# 19. Forecast Validation

Required metrics:

### MAE

Average absolute prediction error.

### RMSE

Penalizes larger errors more heavily.

### R²

Measures explained variance.

Optional:

-   MAPE
-   Median Absolute Error
-   Prediction interval coverage

The dashboard should display:

``` text
Model Performance
MAE: ...
RMSE: ...
R²: ...
Test Period: ...
```

------------------------------------------------------------------------

# 20. Explainable AI

## SHAP

Use SHAP to explain individual predictions and global model behavior.

Example:

``` text
Why is PM2.5 high here?

Traffic-related features       + influence
Previous PM2.5                 + influence
Low wind speed                 + influence
High humidity                  + influence
Industrial activity indicator  + influence
```

The UI should avoid claiming:

> Traffic caused 42% of pollution.

Instead:

> Traffic-related features contributed strongly to this model prediction
> under the selected assumptions.

------------------------------------------------------------------------

# 21. Source / Factor Attribution

The system must support at least three categories:

1.  Traffic
2.  Industrial activity
3.  Meteorology / weather

Additional categories can be:

4.  Previous pollution
5.  Time patterns
6.  Spatial factors

## Attribution design

Raw features are grouped into categories.

Example:

``` text
Traffic Category
├── traffic_index
├── road_density
└── major_road_distance

Industrial Category
├── industrial_index
├── industrial_density
└── industrial_distance

Weather Category
├── wind_speed
├── wind_direction
├── humidity
├── temperature
└── rainfall
```

SHAP values can then be aggregated by category.

Output:

``` text
Traffic-related influence      31%
Weather-related influence      28%
Industrial-related influence   17%
Historical pollution           16%
Other                           8%
```

These values are **model-attributed influence**, not direct emissions
percentages.

The UI must include an assumptions / methodology note.

------------------------------------------------------------------------

# 22. "Why Is Pollution High?" Feature

User selects a location.

The system generates an explanation.

Example:

``` text
Pollution Level: HIGH

Main modeled influences:
1. High recent PM2.5
2. Low wind speed
3. High traffic indicator
4. Elevated industrial activity indicator
5. High humidity

Interpretation:
The model associates the current conditions with these factors.
This is model-based attribution, not direct causal measurement.
```

------------------------------------------------------------------------

# 23. What-if Scenario Engine

This is one of the most important differentiating features.

The user can change urban conditions and observe model output.

## Scenario 1: Traffic Reduction

Input:

``` text
Traffic reduction = 20%
```

The system modifies traffic-related model inputs.

Then:

``` text
Baseline Prediction
        ↓
Scenario Feature Modification
        ↓
ML Model
        ↓
Scenario Prediction
```

------------------------------------------------------------------------

## Scenario 2: Industrial Control

Input:

``` text
Industrial activity reduction = 20%
```

The system modifies the industrial activity indicator according to the
defined model assumption.

------------------------------------------------------------------------

## Scenario 3: Combined Intervention

Example:

``` text
Traffic reduction = 20%
Industrial activity reduction = 15%
```

The model produces a new prediction.

------------------------------------------------------------------------

# 24. Minimum Three Intervention Scenarios

The final product must compare at least:

### Scenario A

Traffic restriction.

### Scenario B

Industrial activity control.

### Scenario C

Combined traffic + industrial intervention.

Optional additional scenarios:

-   traffic restriction around hotspot,
-   temporary industrial reduction,
-   low-emission zone,
-   public transport shift proxy,
-   restricted heavy-vehicle movement.

------------------------------------------------------------------------

# 25. Scenario Comparison

Example UI:

  Metric              Baseline   Traffic Control   Industrial Control   Combined
  ----------------- ---------- ----------------- -------------------- ----------
  Avg PM2.5                  X                 X                    X          X
  Peak PM2.5                 X                 X                    X          X
  Hotspot Area               X                 X                    X          X
  High-Risk Cells            X                 X                    X          X

The system should also show a map:

``` text
Baseline Map
        ↓
Scenario Map
        ↓
Difference / Impact Map
```

------------------------------------------------------------------------

# 26. Intervention Impact Heatmap

For each scenario:

``` text
Scenario Prediction
        -
Baseline Prediction
        =
Spatial Impact
```

Display:

-   areas improved,
-   areas unchanged,
-   areas potentially worsened,
-   magnitude of change.

This helps show that interventions may have spatially different effects.

------------------------------------------------------------------------

# 27. Historical Replay

A timeline allows the user to select a historical date/time.

Example:

``` text
08:00 → 10:00 → 12:00 → 14:00 → 16:00
```

The map updates with historical pollution conditions.

The user can inspect:

-   observed pollution,
-   weather,
-   traffic indicators,
-   industrial indicators,
-   forecast,
-   actual values.

This turns the dashboard into a temporal digital twin instead of a
static map.

------------------------------------------------------------------------

# 28. Forecast vs Actual Replay

For historical periods:

``` text
Actual
██████████

Predicted
████████
```

The user can inspect where the model performed well or poorly.

------------------------------------------------------------------------

# 29. Uncertainty / Confidence

Where technically feasible, predictions should include uncertainty.

Example:

``` text
Predicted PM2.5
48 µg/m³

Prediction interval
42–55 µg/m³
```

Map visualization can also show confidence.

Low-confidence predictions should not appear equally certain as
high-confidence predictions.

MVP implementation can use:

-   model ensembles,
-   quantile regression,
-   conformal prediction,
-   or another practical prediction-interval method.

This is optional if time is limited, but highly valuable.

------------------------------------------------------------------------

# 30. Emerging Hotspot Prediction

Instead of only identifying current hotspots, the system can identify:

**Potential future hotspots**

Example:

``` text
Current hotspot:
Zone A

Predicted hotspot in 3 hours:
Zone B
```

This can be derived from spatial forecasting.

------------------------------------------------------------------------

# 31. Pollution Movement Visualization

Where data supports it, show:

-   wind direction,
-   pollution concentration,
-   hotspot movement,
-   predicted movement.

This helps communicate the relationship between meteorology and spatial
pollution patterns.

It should remain clearly modeled where appropriate.

------------------------------------------------------------------------

# 32. Real-Time Monitoring

If live APIs are available:

-   refresh observations,
-   update map,
-   refresh weather,
-   update forecast,
-   show latest timestamp.

UI must display:

``` text
Last updated: YYYY-MM-DD HH:MM
Data source: ...
```

If live data is unavailable, use historical or preloaded data without
pretending it is live.

------------------------------------------------------------------------

# 33. Alerts

Optional feature.

Possible alerts:

-   PM2.5 threshold exceeded,
-   forecast hotspot,
-   sudden pollution increase,
-   low-confidence forecast,
-   scenario exceeds defined threshold.

Example:

``` text
Potential PM2.5 hotspot predicted in Zone B
Forecast horizon: 3 hours
```

------------------------------------------------------------------------

# 34. Correlation Explorer

Users can select variables:

``` text
PM2.5 vs Wind Speed
PM2.5 vs Traffic Index
PM2.5 vs Humidity
PM2.5 vs Industrial Index
```

Display:

-   scatter plot,
-   correlation,
-   time relationship,
-   selected period.

Correlation must not be described as causation.

------------------------------------------------------------------------

# 35. Dashboard Design

## Main Layout

``` text
┌─────────────────────────────────────────────────────┐
│ Urban Air Quality Digital Twin                     │
│ Observe | Predict | Explain | Simulate | Validate  │
├─────────────────────────────────────────────────────┤
│                                                     │
│                  GIS MAP                            │
│                                                     │
│        Pollution / Hotspots / Roads / Industry     │
│                                                     │
├───────────────┬───────────────┬─────────────────────┤
│ PM2.5         │ Forecast      │ Hotspots             │
│ 42 µg/m³      │ 48 µg/m³      │ 7 zones             │
├───────────────┴───────────────┴─────────────────────┤
│                                                   │
│ Scenario Builder                                  │
│ Traffic:       [----20%----]                      │
│ Industry:      [----15%----]                      │
│ [Run Scenario]                                    │
│                                                   │
├─────────────────────────────────────────────────────┤
│ Scenario Comparison / Explanation / Validation     │
└─────────────────────────────────────────────────────┘
```

------------------------------------------------------------------------

# 36. UI Modes

## Mode 1: Observe

Show real / observed data.

## Mode 2: Predict

Show forecast.

## Mode 3: Explain

Show model-attributed influences.

## Mode 4: Simulate

Allow scenario controls.

## Mode 5: Compare

Compare baseline and interventions.

## Mode 6: Validate

Show historical model performance.

------------------------------------------------------------------------

# 37. Mandatory Data Labels

Every visualization must distinguish:

### OBSERVED

Directly measured or retrieved data.

### FORECAST

Output from the prediction model.

### MODELED SCENARIO

Output generated after changing model inputs.

Example UI labels:

``` text
● OBSERVED
● FORECAST
● MODELED SCENARIO
```

These labels should appear in:

-   map legends,
-   charts,
-   cards,
-   scenario outputs,
-   tooltips,
-   downloadable reports.

------------------------------------------------------------------------

# 38. Data Sources Strategy

The system should use a configurable data-source layer.

Potential sources:

## Air Quality

-   OpenAQ
-   CPCB
-   data.gov.in
-   available municipal / government datasets

## Weather

-   Open-Meteo
-   other compatible weather datasets

## Geospatial

-   OpenStreetMap
-   administrative boundary datasets
-   municipal GIS datasets

## Traffic

-   municipal open-data sources where available,
-   government traffic datasets,
-   defined traffic proxies where direct historical data is unavailable.

## Industrial

-   industrial zones,
-   land-use datasets,
-   facility locations,
-   available government datasets,
-   derived industrial activity indicators.

## Important Rule

Do not make the product dependent on one source.

Implement adapters so the source can be replaced without changing the ML
pipeline.

------------------------------------------------------------------------

# 39. Data Processing Pipeline

``` text
RAW DATA
   ↓
INGEST
   ↓
VALIDATE
   ↓
CLEAN
   ↓
NORMALIZE
   ↓
ALIGN TIMESTAMPS
   ↓
ALIGN SPATIAL COORDINATES
   ↓
JOIN DATASETS
   ↓
FEATURE ENGINEERING
   ↓
MODEL DATASET
```

------------------------------------------------------------------------

# 40. Data Quality Rules

Handle:

-   missing values,
-   duplicate timestamps,
-   invalid coordinates,
-   impossible pollutant values,
-   sensor gaps,
-   different sampling intervals,
-   timezone mismatch,
-   unit mismatch,
-   API failures.

Every dataset should have:

``` text
source
timestamp
location
unit
quality_status
```

------------------------------------------------------------------------

# 41. Spatiotemporal Data Model

Recommended base record:

``` text
timestamp
location_id
grid_id
latitude
longitude

pm25
pm10
no2
so2
co
o3

temperature
humidity
wind_speed
wind_direction
rainfall
pressure

traffic_index
road_density
major_road_distance

industrial_index
industrial_density
industrial_distance
```

Derived fields:

``` text
pm25_lag_1
pm25_lag_3
pm25_lag_6
pm25_rolling_mean
pm25_rolling_max

hour
day_of_week
month
season

traffic_category_features
industrial_category_features
weather_category_features
```

------------------------------------------------------------------------

# 42. Spatial Grid

The city can be divided into grid cells.

Example:

``` text
┌───┬───┬───┬───┐
│ A │ B │ C │ D │
├───┼───┼───┼───┤
│ E │ F │ G │ H │
├───┼───┼───┼───┤
│ I │ J │ K │ L │
└───┴───┴───┴───┘
```

Each cell stores:

-   observations,
-   engineered features,
-   predictions,
-   scenario outputs,
-   confidence,
-   hotspot status.

Grid size should be selected based on data density rather than
arbitrarily choosing extremely fine resolution.

------------------------------------------------------------------------

# 43. Spatial Modeling Strategy

Start simple.

## MVP

Use:

-   station observations,
-   spatial interpolation or nearest-station features,
-   grid aggregation,
-   spatial features.

## Advanced

Possible approaches:

-   XGBoost with spatial features,
-   Random Forest spatial prediction,
-   Gaussian Process,
-   spatial interpolation,
-   graph-based models,
-   GNN.

Do not use a GNN unless the available data justifies it.

------------------------------------------------------------------------

# 44. Scenario Engine Design

The scenario engine must be deterministic and reproducible.

Input:

``` json
{
  "traffic_reduction": 0.20,
  "industrial_reduction": 0.15,
  "target_area": "all"
}
```

Processing:

``` text
BASELINE FEATURES
       ↓
APPLY SCENARIO TRANSFORMATION
       ↓
SCENARIO FEATURES
       ↓
TRAINED MODEL
       ↓
SCENARIO PREDICTION
```

Output:

``` json
{
  "baseline_pm25": 52,
  "scenario_pm25": 44,
  "change": -8,
  "change_percent": -15.38
}
```

The scenario output must be marked:

**MODELED SCENARIO**

------------------------------------------------------------------------

# 45. Scenario Assumption System

Every intervention should have an assumption definition.

Example:

``` text
Traffic reduction: 20%

Assumption:
The traffic indicator used by the model is reduced by 20%
in the selected area and forecast period.

Interpretation:
This represents a modeled intervention scenario.
It does not directly measure a real-world 20% reduction
in emissions.
```

This transparency is mandatory.

------------------------------------------------------------------------

# 46. Explainability Architecture

``` text
Prediction
    ↓
SHAP
    ↓
Feature Contributions
    ↓
Feature Grouping
    ↓
Category Contributions
    ↓
User Explanation
```

Categories:

``` text
Traffic
Industry
Weather
Historical Pollution
Temporal
Spatial
Other
```

------------------------------------------------------------------------

# 47. Model Registry

Store model metadata:

``` text
model_id
model_name
version
training_period
validation_period
test_period
features
target
metrics
created_at
```

Example:

``` text
PM25-XGB-v1

Target: PM2.5
Training: Jan-Jun
Validation: Jul-Aug
Test: Sep
MAE: ...
RMSE: ...
R²: ...
```

------------------------------------------------------------------------

# 48. Backend API

Recommended endpoints:

## Data

``` text
GET /api/air-quality/current
GET /api/air-quality/history
GET /api/weather/current
GET /api/weather/history
GET /api/traffic
GET /api/industrial
```

## Map

``` text
GET /api/map/layers
GET /api/map/hotspots
GET /api/map/grid
```

## Forecast

``` text
POST /api/forecast
GET /api/forecast/{id}
```

## Explain

``` text
POST /api/explain
GET /api/explain/{predictionId}
```

## Scenario

``` text
POST /api/scenarios
GET /api/scenarios/{id}
POST /api/scenarios/compare
```

## Validation

``` text
GET /api/validation/metrics
GET /api/validation/history
```

## System

``` text
GET /api/health
GET /api/data-status
```

------------------------------------------------------------------------

# 49. Suggested Technology Stack

## Frontend

Recommended:

-   React
-   TypeScript
-   Tailwind CSS
-   MapLibre GL JS or Leaflet
-   Recharts / Plotly / ECharts

## Backend

Recommended:

-   Python
-   FastAPI

Reason:

-   ML integration,
-   data processing,
-   geospatial processing,
-   API development.

## ML

-   Pandas
-   NumPy
-   Scikit-learn
-   XGBoost / LightGBM
-   SHAP

## Geospatial

-   GeoPandas
-   Shapely
-   Rasterio if required
-   PostGIS where needed
-   OpenStreetMap

## Database

Recommended:

-   PostgreSQL
-   PostGIS

Optional:

-   Redis for caching/background tasks.

## Deployment

Potential:

-   Docker
-   Docker Compose
-   cloud deployment

The final stack can be simplified if time is limited.

------------------------------------------------------------------------

# 50. Recommended Repository Structure

``` text
urban-air-quality-digital-twin/
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── maps/
│   │   ├── charts/
│   │   ├── scenarios/
│   │   ├── validation/
│   │   └── services/
│   └── package.json
│
├── backend/
│   ├── app/
│   │   ├── api/
│   │   ├── models/
│   │   ├── services/
│   │   ├── schemas/
│   │   ├── data/
│   │   ├── ml/
│   │   ├── geospatial/
│   │   └── main.py
│   └── requirements.txt
│
├── ml/
│   ├── notebooks/
│   ├── preprocessing/
│   ├── features/
│   ├── training/
│   ├── evaluation/
│   ├── explainability/
│   └── models/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── sample/
│
├── docs/
│   ├── architecture/
│   ├── assumptions/
│   └── methodology/
│
├── tests/
│
├── docker-compose.yml
├── README.md
└── PRD.md
```

------------------------------------------------------------------------

# 51. Development Phases

## Phase 0: Project Setup

Deliverables:

-   repository,
-   frontend,
-   backend,
-   ML workspace,
-   environment configuration,
-   Docker setup if required.

------------------------------------------------------------------------

## Phase 1: Data Pipeline

Build:

-   air-quality ingestion,
-   weather ingestion,
-   geospatial ingestion,
-   traffic indicator generation,
-   industrial indicator generation.

Deliverable:

A clean unified dataset.

------------------------------------------------------------------------

## Phase 2: Data Cleaning and EDA

Implement:

-   missing-value analysis,
-   outlier checks,
-   temporal patterns,
-   spatial patterns,
-   correlation analysis,
-   feature distributions.

Deliverables:

-   cleaned dataset,
-   EDA notebook,
-   initial insights.

------------------------------------------------------------------------

## Phase 3: Baseline ML

Build:

-   persistence baseline,
-   linear regression,
-   Random Forest,
-   XGBoost / LightGBM.

Compare using chronological validation.

Select the model based on validation performance and practical
reliability.

------------------------------------------------------------------------

## Phase 4: Explainability

Implement:

-   SHAP global importance,
-   SHAP local explanations,
-   grouped source/factor influence,
-   explanation API.

------------------------------------------------------------------------

## Phase 5: Spatial Prediction

Implement:

-   city grid,
-   spatial features,
-   grid-level prediction,
-   hotspot detection.

------------------------------------------------------------------------

## Phase 6: Digital Twin Map

Implement:

-   base map,
-   air-quality layer,
-   monitoring stations,
-   weather layer,
-   road layer,
-   industrial layer,
-   observed/forecast labels.

------------------------------------------------------------------------

## Phase 7: Forecast Dashboard

Implement:

-   forecast cards,
-   time-series chart,
-   forecast map,
-   forecast horizon selection,
-   confidence if available.

------------------------------------------------------------------------

## Phase 8: Scenario Engine

Implement:

-   traffic scenario,
-   industrial scenario,
-   combined scenario,
-   scenario execution,
-   baseline comparison.

------------------------------------------------------------------------

## Phase 9: Scenario Visualization

Implement:

-   comparison table,
-   scenario charts,
-   impact heatmap,
-   hotspot changes,
-   scenario assumptions.

------------------------------------------------------------------------

## Phase 10: Historical Validation

Implement:

-   historical replay,
-   actual vs predicted chart,
-   MAE,
-   RMSE,
-   R²,
-   test-period selector.

------------------------------------------------------------------------

## Phase 11: Product Integration

Connect:

``` text
Data → ML → API → Map → Explanation → Scenario → Validation
```

Remove disconnected prototype screens.

------------------------------------------------------------------------

## Phase 12: UX and Transparency

Verify:

-   observed labels,
-   forecast labels,
-   scenario labels,
-   source information,
-   assumptions,
-   timestamps,
-   model version,
-   confidence.

------------------------------------------------------------------------

## Phase 13: Demo Optimization

Create a fixed demonstration flow:

``` text
1. Open city map
2. Show observed pollution
3. Select hotspot
4. Show forecast
5. Explain why pollution is high
6. Run traffic intervention
7. Run industrial intervention
8. Run combined intervention
9. Compare scenarios
10. Show historical validation
```

------------------------------------------------------------------------

# 52. MVP Definition

The MVP is complete when all of the following work:

### Data

-   Air-quality data loaded.
-   Weather data loaded.
-   Traffic indicator available.
-   Industrial indicator available.
-   Historical data available.

### ML

-   PM2.5 prediction works.
-   Time-based validation works.
-   Metrics are calculated.
-   SHAP explanation works.

### GIS

-   Map works.
-   Pollution is visualized spatially.
-   Hotspots are shown.

### Digital Twin

-   Observed state shown.
-   Forecast state shown.
-   Modeled scenario shown.

### Simulation

-   Traffic intervention works.
-   Industrial intervention works.
-   Combined intervention works.

### Comparison

-   Baseline vs three scenarios works.

### Validation

-   Historical actual vs prediction comparison works.

### Transparency

-   Observed/forecast/scenario labels are visible.

------------------------------------------------------------------------

# 53. Advanced Feature Priority

## Priority P0: Mandatory

-   Data ingestion
-   PM2.5 forecasting
-   GIS map
-   Hotspots
-   Weather
-   Traffic indicator
-   Industrial indicator
-   SHAP
-   Three source categories
-   Three interventions
-   Scenario comparison
-   Historical validation
-   Observed vs modeled labels

## Priority P1: Strongly Recommended

-   Spatial forecast
-   Historical replay
-   Confidence / uncertainty
-   Impact heatmap
-   Why pollution is high
-   Emerging hotspots
-   Correlation explorer

## Priority P2: Stretch

-   Satellite
-   IoT
-   Optimization
-   Natural-language interface
-   Multi-city
-   Multiple pollutant forecasting
-   Automated scenarios

------------------------------------------------------------------------

# 54. Differentiation

The project should not position itself as merely:

> "An AI model that predicts air quality."

The stronger product proposition is:

> "An explainable urban air-quality digital twin that connects observed
> city conditions with prediction and intervention simulation."

Differentiating capabilities:

1.  Spatial digital twin.
2.  Forecasting.
3.  Model-attributed factor influence.
4.  What-if intervention engine.
5.  Spatial scenario comparison.
6.  Historical replay.
7.  Historical validation.
8.  Uncertainty.
9.  Explicit observed vs modeled transparency.

------------------------------------------------------------------------

# 55. Innovation Narrative

The innovation is in the integration of capabilities into one
decision-support workflow.

Existing systems may separately provide:

-   air-quality monitoring,
-   weather information,
-   traffic information,
-   forecasts,
-   maps.

This project connects these components into:

``` text
OBSERVE
   ↓
PREDICT
   ↓
EXPLAIN
   ↓
SIMULATE
   ↓
COMPARE
   ↓
VALIDATE
```

The system therefore moves from:

**"What is happening?"**

to:

**"What may happen?"**

to:

**"What factors does the model associate with it?"**

to:

**"What could happen under different modeled interventions?"**

------------------------------------------------------------------------

# 56. Important Scientific / Product Boundaries

## Boundary 1: SHAP is not causal attribution

SHAP explains model behavior.

It does not prove that a source physically caused a specific percentage
of pollution.

Use:

**model-attributed influence**

not:

**exact causal contribution**

unless scientifically justified.

------------------------------------------------------------------------

## Boundary 2: Proxy data must remain proxies

If direct traffic measurements are unavailable:

Do not say:

> Actual traffic emissions.

Say:

> Traffic-related indicator / proxy.

If direct industrial emissions are unavailable:

Do not say:

> Factory emissions.

Say:

> Industrial activity indicator.

------------------------------------------------------------------------

## Boundary 3: Forecast is not observation

A forecast must never be presented as a measured value.

------------------------------------------------------------------------

## Boundary 4: Scenario is not real-world measurement

Scenario output represents:

> What the model predicts if the defined assumptions are applied.

It does not prove the real-world outcome.

------------------------------------------------------------------------

# 57. Demo Scenario

Use a realistic urban situation.

Example:

``` text
Current observed PM2.5:
58 µg/m³

Forecast in 3 hours:
67 µg/m³

Predicted hotspot:
Zone B
```

User selects Zone B.

System explains:

``` text
High modeled influence:
- recent PM2.5
- low wind speed
- traffic-related features
- industrial activity indicator
```

User opens simulation:

``` text
Traffic reduction: 20%
Industrial reduction: 15%
```

System calculates:

``` text
Baseline:
67 µg/m³

Traffic scenario:
61 µg/m³

Industrial scenario:
63 µg/m³

Combined:
55 µg/m³
```

These values are illustrative for the interface only. The actual demo
must use model-generated outputs.

------------------------------------------------------------------------

# 58. First-Round PPT Plan

The PRD itself is the source of truth for the first-round presentation.

## Slide 1: Title

**Urban Air Quality Digital Twin**

Subtitle:

**Observe. Predict. Explain. Simulate.**

Team name and members.

------------------------------------------------------------------------

## Slide 2: Problem

Show:

-   current systems show pollution levels,
-   limited explanation of contributing factors,
-   limited ability to test interventions,
-   decision makers need spatial and predictive insight.

------------------------------------------------------------------------

## Slide 3: Proposed Solution

Show the digital twin:

``` text
Air Quality
Weather
Traffic
Industry
   ↓
Urban Digital Twin
   ↓
Prediction + Explanation
   ↓
What-if Simulation
   ↓
Intervention Comparison
```

------------------------------------------------------------------------

## Slide 4: Product Workflow

``` text
OBSERVE
   ↓
PREDICT
   ↓
EXPLAIN
   ↓
SIMULATE
   ↓
COMPARE
   ↓
VALIDATE
```

------------------------------------------------------------------------

## Slide 5: Key Features

Group features:

### Observe

-   live/historical air quality
-   weather
-   traffic
-   industry
-   GIS map

### Predict

-   PM2.5 forecast
-   hotspot forecast
-   uncertainty

### Explain

-   SHAP
-   factor influence
-   why pollution is high

### Simulate

-   traffic control
-   industrial control
-   combined interventions

### Validate

-   historical replay
-   actual vs predicted
-   MAE/RMSE/R²

------------------------------------------------------------------------

## Slide 6: AI / ML

Show:

``` text
Historical Data
      ↓
Feature Engineering
      ↓
XGBoost / Tree Model
      ↓
PM2.5 Forecast
      ↓
SHAP Explanation
```

------------------------------------------------------------------------

## Slide 7: Digital Twin Interface

Show conceptual UI:

-   map,
-   hotspots,
-   forecast,
-   scenario controls,
-   explanation,
-   comparison.

------------------------------------------------------------------------

## Slide 8: What-if Scenario

Example:

``` text
Baseline
Traffic -20%
Industry -20%
Combined
```

Show before/after map and metrics.

------------------------------------------------------------------------

## Slide 9: Validation

Show:

``` text
Historical Test Period

Actual PM2.5
vs
Predicted PM2.5

MAE
RMSE
R²
```

------------------------------------------------------------------------

## Slide 10: Impact

Explain:

-   proactive pollution management,
-   evidence-based intervention testing,
-   spatial hotspot awareness,
-   transparent AI,
-   historical validation,
-   reusable urban intelligence architecture.

------------------------------------------------------------------------

# 59. PPT Design Rules

The presentation should communicate the product, not overload judges
with implementation details.

Use:

-   clean GIS visual,
-   one architecture diagram,
-   one ML pipeline,
-   one scenario comparison,
-   one validation graph.

Avoid excessive:

-   buzzwords,
-   paragraphs,
-   generic AI terminology,
-   unexplained model names,
-   claims without data.

The main story must remain:

**Observe → Predict → Explain → Simulate → Compare → Validate**

------------------------------------------------------------------------

# 60. Implementation Order

Do not build all features simultaneously.

Follow this dependency order:

``` text
1. Data
   ↓
2. Cleaning
   ↓
3. Feature Engineering
   ↓
4. Baseline Model
   ↓
5. Validation
   ↓
6. SHAP
   ↓
7. Spatial Prediction
   ↓
8. Map
   ↓
9. Forecast API
   ↓
10. Scenario Engine
   ↓
11. Scenario Comparison
   ↓
12. Historical Replay
   ↓
13. Dashboard Integration
   ↓
14. UX / Transparency
   ↓
15. Demo
```

------------------------------------------------------------------------

# 61. Engineering Principles

## Principle 1: Build a working baseline first

Do not start with advanced ML.

## Principle 2: Every prediction must be reproducible

Store model version and feature configuration.

## Principle 3: Every modeled output must be labeled

Observed, forecast, or modeled scenario.

## Principle 4: Never hide assumptions

Traffic and industrial proxies must be documented.

## Principle 5: Spatial visualization is central

The map is not an accessory.

## Principle 6: Scenario simulation must use the model

Do not fake scenario results with hard-coded percentages.

## Principle 7: Historical validation is mandatory

A live dashboard alone is not sufficient.

## Principle 8: Prefer explainable models

A slightly simpler but explainable model is preferable to an
unnecessarily complex black box.

------------------------------------------------------------------------

# 62. Performance Requirements

Target:

-   dashboard initial load: reasonable for demo environment,
-   API response: typically under 2 seconds for cached/read operations,
-   scenario execution: preferably under 5 seconds,
-   map interaction: smooth enough for live demonstration,
-   model inference: fast enough for interactive what-if simulation.

Heavy training should happen offline.

The dashboard should perform inference using a saved model.

------------------------------------------------------------------------

# 63. Reliability Requirements

The system must:

-   handle unavailable external APIs,
-   display last successful update,
-   avoid crashing because one source is missing,
-   show data-quality warnings,
-   preserve historical data,
-   support demo data fallback.

Fallback data is acceptable for demonstration, but it must be clearly
labeled as historical/preloaded data rather than live data.

------------------------------------------------------------------------

# 64. Security Requirements

Basic requirements:

-   environment variables for API keys,
-   no secrets committed to Git,
-   backend input validation,
-   rate limiting where public APIs are exposed,
-   CORS configuration,
-   safe file upload handling if uploads are supported.

No personally identifiable data is required for the core product.

------------------------------------------------------------------------

# 65. Testing Strategy

## Unit Tests

-   feature engineering,
-   scenario transformations,
-   API validation,
-   metric calculation.

## ML Tests

-   train/test separation,
-   feature consistency,
-   model loading,
-   prediction shape,
-   scenario reproducibility.

## GIS Tests

-   coordinate validity,
-   grid assignment,
-   spatial joins.

## Integration Tests

``` text
Data → Model → API → Frontend
```

## Demo Tests

Run the complete fixed demo from beginning to end.

------------------------------------------------------------------------

# 66. Success Criteria

The project is considered successful if a judge can complete this
journey without developer intervention:

1.  Open the city map.
2.  Identify an observed pollution hotspot.
3.  Inspect historical conditions.
4.  View PM2.5 forecast.
5.  See predicted hotspot.
6.  Ask why pollution is high.
7.  See influence from at least three categories.
8.  Open scenario simulation.
9.  Run traffic intervention.
10. Run industrial intervention.
11. Run combined intervention.
12. Compare outcomes.
13. Inspect historical validation.
14. Understand which results are observed and which are modeled.

------------------------------------------------------------------------

# 67. Final Feature Matrix

  Feature                             Priority   Required
  ----------------------------------- ---------- -------------
  Air-quality ingestion               P0         Yes
  Weather ingestion                   P0         Yes
  Traffic indicator                   P0         Yes
  Industrial indicator                P0         Yes
  GIS map                             P0         Yes
  Pollution hotspots                  P0         Yes
  PM2.5 forecast                      P0         Yes
  Spatial forecast                    P0         Yes
  SHAP explanation                    P0         Yes
  Traffic influence                   P0         Yes
  Industrial influence                P0         Yes
  Weather influence                   P0         Yes
  Traffic intervention                P0         Yes
  Industrial intervention             P0         Yes
  Combined intervention               P0         Yes
  Scenario comparison                 P0         Yes
  Historical validation               P0         Yes
  Observed/Forecast/Scenario labels   P0         Yes
  Historical replay                   P1         Recommended
  Uncertainty                         P1         Recommended
  Emerging hotspots                   P1         Recommended
  Impact heatmap                      P1         Recommended
  Why pollution is high               P1         Recommended
  Correlation explorer                P1         Recommended
  Alerts                              P1         Recommended
  Multiple pollutants                 P2         Stretch
  Satellite data                      P2         Stretch
  IoT sensors                         P2         Stretch
  Intervention optimization           P2         Stretch
  Natural-language query              P2         Stretch
  Multi-city                          P2         Stretch

------------------------------------------------------------------------

# 68. Final Product Definition

The final system is:

> **A map-based Urban Air Quality Digital Twin that combines observed
> air-quality, weather, traffic-related, industrial-activity-related,
> temporal, and spatial data to forecast PM2.5, identify pollution
> hotspots, explain model-attributed influences, simulate intervention
> scenarios, compare their modeled outcomes, and validate predictions
> against historical periods.**

The project should demonstrate the complete loop:

``` text
REAL CITY
   ↓
OBSERVED DATA
   ↓
DIGITAL TWIN
   ↓
PREDICTION
   ↓
EXPLANATION
   ↓
WHAT-IF SIMULATION
   ↓
SCENARIO COMPARISON
   ↓
VALIDATION
   ↓
DECISION SUPPORT
```

------------------------------------------------------------------------

# 69. Final Scope Lock

This PRD is the authoritative project scope.

The implementation should prioritize the following sequence:

### MUST BUILD

-   Multi-source data pipeline
-   PM2.5 prediction
-   GIS pollution map
-   Hotspot detection
-   Weather integration
-   Traffic indicator
-   Industrial indicator
-   SHAP-based explanation
-   Three source/factor categories
-   Three intervention scenarios
-   Model-based scenario simulation
-   Baseline vs scenario comparison
-   Historical validation
-   Observed / Forecast / Modeled Scenario labels

### SHOULD BUILD

-   Spatial forecasting
-   Historical replay
-   Uncertainty
-   Impact heatmap
-   Emerging hotspots
-   Correlation explorer
-   Alerts

### MAY BUILD IF TIME REMAINS

-   Satellite
-   IoT
-   Optimization
-   Natural language interface
-   Multi-city
-   Multiple pollutant forecasting

The team should not expand the scope beyond this PRD before the
mandatory system is functional.

------------------------------------------------------------------------

# 70. Final Presentation Story

The entire project should be explainable in one sentence:

> **We are building an Urban Air Quality Digital Twin that not only
> shows where pollution is, but predicts where it will be, explains the
> factors influencing the model, and lets users test interventions
> before implementing them.**

And the complete story is:

**Observe → Predict → Explain → Simulate → Compare → Validate**

This is the final product direction for both the first-round PPT and
implementation.
