# 🏠 Real Estate Valuation: Predictive Modeling in R

> Predicting property prices in New Taipei City and identifying the location,
> accessibility, and property characteristics that drive real-estate value.

![R](https://img.shields.io/badge/R-Statistical%20Analysis-276DC3?logo=r)
![Regression](https://img.shields.io/badge/Model-Multiple%20Linear%20Regression-20B2AA)
![R²](https://img.shields.io/badge/R²-72.6%25-success)
![Status](https://img.shields.io/badge/Status-Complete-success)

## Project Snapshot

Real-estate valuation is influenced by property characteristics, transportation
access, amenities, and location.

In this project, I analyzed real-estate transactions from **Sindian District,
New Taipei City, Taiwan** and developed a multiple linear regression model to
predict **house price per unit area**.

### Results at a Glance

| Metric | Result |
|---|---:|
| R² | **72.6%** |
| Adjusted R² | **72.2%** |
| Predicted R² | **71.7%** |
| RMSE | **6.425** |
| MAE | **5.090** |

The final model retained **5 of the 6 candidate predictors**, with distance to
the nearest MRT station emerging as one of the strongest predictors of property
value.

---

## Business Question

**Can property characteristics and location data be used to explain and predict
real-estate prices in Sindian District?**

I approached the problem through four stages:

1. Exploratory data analysis
2. Regression modeling
3. Feature/model selection
4. Statistical diagnostics and validation

---

## Dataset

**Source:** UCI Machine Learning Repository  
**Observations:** 414 property transactions  
**Location:** Sindian District, New Taipei City  
**Period:** 2012–2013

### Features

| Feature | Description |
|---|---|
| Transaction Date | Date of property transaction |
| House Age | Age of the property |
| MRT Distance | Distance to nearest MRT station |
| Convenience Stores | Number of nearby convenience stores |
| Latitude | Geographic latitude |
| Longitude | Geographic longitude |
| House Price | Price per unit area — target variable |

---

## Exploratory Analysis

### What drives property prices?

![Correlation Matrix](images/correlation.png)

The exploratory analysis revealed several important relationships:

- **MRT distance** has a strong negative relationship with property price.
- **Convenience-store availability** is positively associated with price.
- **House age** has a negative relationship with price.
- **Geographic location** is an important component of valuation.
- Transaction date has a smaller positive association with price.

These findings suggested that both **accessibility and location** should play
important roles in the predictive model.

---

## Outliers & Influential Observations

![Cook's Distance](images/cooks-distance.png)

I used boxplots and **Cook's Distance** to investigate potentially influential
observations.

Observations **149, 271 and 313** showed comparatively large Cook's Distance
values and were investigated before the final model was fitted.

This step was important because highly influential transactions can
disproportionately affect ordinary least-squares regression estimates.

---

## Multicollinearity

Variance Inflation Factors were calculated before model selection.

| Variable | VIF |
|---|---:|
| Transaction Date | 1.009 |
| House Age | 1.012 |
| MRT Distance | 4.580 |
| Convenience Stores | 1.626 |
| Latitude | 1.854 |
| Longitude | 2.880 |

All VIF values were below **5**, providing no indication of severe
multicollinearity.

---

## Model Selection

![Model Selection](images/model-selection.png)

I used **Best Subsets Regression** to compare candidate models using:

- Adjusted R²
- Predicted R²
- Mallows' Cp
- AIC
- BIC/SBIC

The five-predictor model provided the best balance between explanatory power
and model complexity.

**Selected predictors**

`Transaction Date + House Age + MRT Distance + Convenience Stores + Latitude`

Longitude was excluded from the final specification.

---

## Final Model

The selected regression model is:

```text
Price =
-13216.810
+ 3.829(Transaction Date)
- 0.324(House Age)
- 0.004(MRT Distance)
+ 1.222(Convenience Stores)
+ 222.326(Latitude)
