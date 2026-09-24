# 🏠 Predictive Model for Real Estate Valuation

## Project Overview

This project develops a multiple linear regression model for explaining and
predicting house price per unit area in **Sindian District, New Taipei City,
Taiwan**.

The analysis investigates the relationship between property values and
characteristics including house age, proximity to MRT stations, nearby
convenience stores, transaction date, and geographic location.

The complete statistical analysis was conducted using **R**.

## Objectives

The primary objectives of the project are to:

- Develop a regression model for house price per unit area.
- Identify statistically significant factors associated with property values.
- Select a parsimonious model with strong explanatory performance.
- Evaluate whether the selected model satisfies key regression assumptions.

## Data Source

The **Real Estate Valuation Data Set** was obtained from the
**UCI Machine Learning Repository**.

The original dataset was contributed by **I-Cheng Yeh, Tamkang University,
Taiwan**, and contains real estate transaction data from Sindian District,
New Taipei City.

**Source:**  
[UCI Machine Learning Repository – Real Estate Valuation Data Set](https://archive.ics.uci.edu/ml/datasets/Real+estate+valuation+data+set)

The original dataset contains **414 observations** and has no missing values.

[View Dataset](data/real_estate_valuation.csv)

## Variables

The response variable is:

- **Y:** House price per unit area

Candidate predictors are:

- **X1:** Transaction date
- **X2:** House age
- **X3:** Distance to the nearest MRT station
- **X4:** Number of convenience stores
- **X5:** Latitude
- **X6:** Longitude

## Analysis Workflow

The project includes:

- Exploratory data analysis
- Correlation analysis
- Distribution analysis
- Outlier investigation
- Cook's distance for influential observations
- Multicollinearity assessment using VIF
- Multiple linear regression
- Best subsets regression
- AIC and information-criterion-based model selection
- Residual diagnostics
- Breusch-Pagan test for heteroskedasticity
- Shapiro-Wilk normality test
- Model interpretation

## Model Selection

Best subsets regression was used to compare candidate models.

Model selection considered:

- Adjusted R²
- Predicted R²
- Mallows' Cp
- AIC
- SBIC/SBC
- Model complexity

The selected model retained five predictors:

`X1 + X2 + X3 + X4 + X5`

Longitude (X6) was excluded from the final model.

## Final Model

The selected regression model is:

`Y = -13216.810 + 3.829X1 - 0.324X2 - 0.004X3 + 1.222X4 + 222.326X5`

### Model Performance

- **R²:** 0.726
- **Adjusted R²:** 0.722
- **Predicted R²:** 0.717
- **RMSE:** 6.425
- **MAE:** 5.090
- **Overall model p-value:** < 0.001

The selected model explains approximately **72.6% of the observed variation**
in house price per unit area.

## Key Findings

The final model indicates that:

- **Transaction date** has a positive association with house price.
- **House age** has a negative association with house price.
- **Distance to the nearest MRT station** has a negative association with
  house price.
- **Number of convenience stores** has a positive association with house price.
- **Latitude** has a positive association with house price.
- **Longitude** was not retained in the selected model.

All five predictors retained in the final model were statistically significant.

## Model Diagnostics

Regression assumptions were evaluated using graphical and statistical
diagnostics.

The final model produced:

- **Breusch-Pagan test:** p = 0.277
- **Shapiro-Wilk test:** p = 0.163

At the 5% significance level, these tests did not provide evidence against
the constant-variance and normality assumptions, respectively.

Residual plots, Q-Q plots, multicollinearity analysis, and influential
observation diagnostics were also examined.

## Tools & Techniques

- R
- Multiple Linear Regression
- Exploratory Data Analysis
- Correlation Analysis
- Best Subsets Regression
- AIC / Model Selection
- Variance Inflation Factor (VIF)
- Cook's Distance
- Breusch-Pagan Test
- Shapiro-Wilk Test
- Regression Diagnostics

## Source Code

The R code used for data exploration, regression modeling, model selection,
and diagnostic analysis is available here:

[View R Analysis Code](analysis.R)

## Full Project Report

The complete report contains the methodology, exploratory analysis,
statistical output, model-selection process, diagnostic plots,
interpretations, limitations, and conclusions.

📄 [View Full Project Report](report/real_estate_valuation_report.pdf)
