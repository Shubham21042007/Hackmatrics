# 🌍 Urban Environmental Digital Twin

> **ENR01 — Urban Environmental Digital Twin**

A map-based digital twin for monitoring, predicting, explaining, and simulating urban air pollution in **Pune / Pimpri-Chinchwad**.

## 🔄 Core Workflow

**OBSERVE → PREDICT → EXPLAIN → SIMULATE → COMPARE → VALIDATE**

## ✨ Key Features

- 📍 GIS-based pollution and hotspot visualization
- 📈 PM2.5 forecasting using Machine Learning
- 🔍 SHAP-based explainability
- 🚦 Traffic intervention simulation
- 🏭 Industrial intervention simulation
- 🔄 What-if scenario comparison
- 📊 Historical model validation

## 🛠️ Tech Stack

**Frontend:** React, TypeScript, Tailwind CSS, MapLibre  
**Backend:** Python, FastAPI  
**ML:** Pandas, NumPy, Scikit-learn, XGBoost, SHAP  
**GIS:** GeoPandas, Shapely, OpenStreetMap  
**Database:** PostgreSQL, PostGIS / Supabase

## 📊 Data Sources

- OpenAQ
- CPCB / data.gov.in
- Open-Meteo
- OpenStreetMap
- MIDC / Industrial GIS data
- Traffic datasets or defined traffic proxies

## 🚧 Current Status

**Data Collection & Verification**

The project is currently focused on verifying and collecting the required historical air-quality, weather, traffic, industrial, and geospatial data before prototype development.

## 🎯 Goal

Build a transparent urban environmental intelligence system that shows **where pollution is, what factors influence the model's predictions, how pollution may change, and how modeled interventions could affect it**.

**Problem Statement:** ENR01  
**Pilot Area:** Pune / Pimpri-Chinchwad  
**Primary Indicator:** PM2.5
