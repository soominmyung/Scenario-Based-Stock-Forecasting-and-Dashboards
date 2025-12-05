## 📦 Stock Forecasting Workflow (SARIMA + Momentum + Tableau)

This repository contains anonymised forecasting scripts and dashboard examples used to project stock trajectories and support replenishment planning.
The workflow combines:
- A weekly SARIMA model for structured, seasonality-aware forecasting
- A momentum-based one-step-ahead projection for operational scenario comparison
- A Tableau dashboard for understock risk alerts and visual analysis

All data and identifiers have been anonymised.
 
<br>

## 1. Forecasting Models

Forecasting scripts are provided in pseudocode form to protect company-specific IP while demonstrating modelling methodology.

**SARIMA Forecasting (pseudocode)**
: Seasonal ARIMA workflow used to model medium-term stock or sales patterns.

**Momentum-Based Projection (pseudocode)**
: Lightweight trend-extension method used for one-step-ahead operational scenarios.

File: SARIMA_Momentum_Forecasting.iypnb

<br>

## 2. Tableau Dashboards

An anonymised version of the Tableau dashboards used for forecasting, stock-out detection, and operational planning.

Stock vs Forecast Timeline

Category-level Forecast Comparison

Inventory Risk Indicators (e.g., approaching stock-outs)

**Tableau Public link:**
https://public.tableau.com/app/profile/soomin.myung/viz/Sample_17648599348760/StockForecastingandUnderstockRiskPanel

## 🧠 Summary of Methods
### SARIMA Weekly Stock Forecasting

Used to capture short-term seasonality and provide a statistically structured trajectory of future stock levels.

### Pseudocode
```
ts = load_stock_series()
ts = weekly_resample(ts)

model = SARIMA(order=(p,d,q), seasonal_order=(P,D,Q,s))
fit = model.fit()

forecast = fit.predict(steps=n_weeks)
plot(ts, forecast)
```

The SARIMA model was chosen for:
- Weekly smoothing of operational noise
- Seasonal patterns in imported food stock
- Interpretability for business stakeholders

### Momentum-Based One-Step Projection

A lightweight scenario that extends the recent four-month trend of stock movement.

### Pseudocode
```
recent = ts[-16:]                    # last 4 months (weekly)
slope = compute_linear_gradient(recent)

next_week = ts[-1] + slope
projection = extend_forward(ts[-1], slope, n_weeks)
```

Used as:
- A transparent “trend continuation” scenario
- A counterfactual to SARIMA for operational planning
- A baseline to compare interventions (e.g., purchase orders)

<br>

## Tableau Understock Dashboard

The dashboard presents:
- SARIMA vs Momentum trajectories (dual-scenario comparison)
- Items approaching understock within the import lead time
- Colour-coded risk levels (High / Medium)
- A 4-month horizon alert table

The dashboard can be found here: https://public.tableau.com/app/profile/soomin.myung/viz/Sample_17648599348760/StockForecastingandUnderstockRiskPanel

<br>

## 🔐 Disclaimer

All datasets, screenshots, and identifiers have been anonymised.
No proprietary business information is included.
