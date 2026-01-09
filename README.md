# Factors Associated with Airbnb Prices in Budapest

## Project Overview

This project investigates **factors associated with Airbnb listing prices in Budapest**, focusing on how **room characteristics, quality indicators, temporal effects, and location-based features** relate to pricing patterns.

The primary objective of this study is **statistical inference**, not causal estimation or prediction. We aim to understand which features are most strongly associated with Airbnb prices and how well a linear regression framework can explain observed price variation.

The complete analysis, modeling, diagnostics, and interpretation are documented in the final HTML report.

---

## Research Question

**Which room characteristics and location features are most strongly associated with Airbnb listing prices in Budapest, and how well can these relationships be modeled using linear regression?**

---

## Dataset

* **Source:**
  Kaggle – *Airbnb Prices in European Cities* (thedevastator)
  Original data: Gyódi & Nawaro (2021), Zenodo
* **License:** Creative Commons Attribution 4.0
* **Data type:** Observational
* **City analyzed:** Budapest

### Sample Size

* **Total observations:** 4,022

---

## Variables

### Response Variable

* `realSum` — Total Airbnb listing price

### Key Explanatory Variables

* `room_type` (entire home / private room / shared room)
* `person_capacity`
* `bedrooms`
* `cleanliness_rating`
* `guest_satisfaction_overall`
* `host_is_superhost`
* `attr_index_norm` (normalized attraction index)
* `rest_index_norm` (normalized restaurant index)
* `metro_dist` (distance to nearest metro station)
* `period` (Weekday vs Weekend)

Irrelevant or redundant variables (e.g., identifiers, geographic coordinates, unnormalized indices) were removed to reduce multicollinearity and simplify inference.

---

## Methods

### Data Processing

* Combined weekday and weekend datasets
* Removed outliers using the IQR method
* Converted categorical and boolean variables to factors
* Added a `period` indicator for weekday vs weekend listings

### Exploratory Data Analysis

* Log-transformed price to address skewness
* Visualized price distributions by room type and time period
* Explored relationships between price, capacity, metro distance, and room type
* Identified heteroskedasticity and right-skewness in prices

### Modeling Approach

* Used **multiple linear regression (MLR)** with log-transformed price:

  [
  \log(\text{realSum}) = \beta_0 + \beta_1 X_1 + \cdots + \varepsilon
  ]

* Checked multicollinearity using **GVIF**

* Performed **bidirectional stepwise selection using AIC**

* Split data into **training (80%)** and **testing (20%)** sets

* Conducted inference using coefficient estimates and hypothesis testing

### Model Diagnostics

* Residuals vs fitted plots
* Q–Q plots for normality
* Actual vs predicted price comparison
* Variance Inflation Factor (VIF) checks

---

## Key Findings

* **Room type** is one of the strongest predictors:

  * Private rooms are ~30% cheaper than entire homes
  * Shared rooms are ~25% cheaper than entire homes
* **Capacity and size matter:**

  * Each additional guest increases price by ~6%
  * Each additional bedroom increases price by ~5–6%
* **Weekend listings** are priced ~6% higher than weekday listings
* **Cleanliness rating** and **attraction density** show positive but modest associations
* The final model explains **moderate variation** in prices (Adjusted R² ≈ 0.33)
* High-priced listings are consistently **underpredicted**, indicating nonlinear effects or missing qualitative features

---

## Authors

* Winnie Chen
* Yifan Hao
* Roxanna Ng
* Jennifer Tjen

---

## Notes

* Results are **associational**, not causal
* The analysis highlights the limitations of linear models for capturing luxury price premiums

