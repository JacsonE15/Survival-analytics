# Longitudinal and Survival Analysis of CD4 Progression in AIDS Patients

## Overview
This project investigates longitudinal CD4 dynamics and survival outcomes among AIDS patients receiving different antiretroviral treatments (ddC vs ddI). Using a combination of longitudinal modeling and survival analysis techniques, the study evaluates whether treatment choice significantly affects immunological progression and mortality risk.

The analysis integrates **Generalized Estimating Equations (GEE)**, **Generalized Linear Mixed Models (GLMM)**, and **time-to-event methods**, providing a comprehensive assessment of both population-level trends and individual-level heterogeneity.

---

## Data
The analysis is based on the `aids` and `aids.id` datasets from the **JM** package in R.  
Data were exported to CSV format and analyzed in Python.

- **aids.csv**: Longitudinal CD4 measurements (repeated observations per patient)
- **aids_id.csv**: Survival data (time to death or censoring)

Key variables include:
- `CD4`: CD4 cell count
- `obstime`: Time since baseline (months)
- `drug`: Treatment group (ddC, ddI)
- `prevOI`: Prior AIDS diagnosis
- `AZT`: AZT tolerance
- `Time`, `death`: Survival outcome variables

---

## Methods

### 1. Exploratory Data Analysis
- Baseline CD4 distribution by treatment group
- Individual CD4 trajectories over time (spaghetti plots)

### 2. Longitudinal Analysis
- **GEE (Gaussian family)** with robust standard errors  
  - Correlation structures: Independence, Exchangeable, AR(1)
- **GLMM**
  - Random intercept model
  - Random intercept + random slope model
  - Model comparison via AIC/BIC (ML estimation)

### 3. Survival Analysis
- Kaplan–Meier survival curves by treatment group
- Log-rank test for survival differences
- Cox proportional hazards model
  - Hazard ratios with 95% confidence intervals
  - Model discrimination assessed using concordance index

---

## Key Findings
- CD4 counts declined significantly over time across all patients.
- Baseline CD4 level and prior AIDS status were strong predictors of longitudinal CD4 trajectories.
- Treatment with ddI did **not** significantly alter the rate of CD4 decline compared with ddC.
- Substantial inter-individual heterogeneity was observed, with random slope models providing superior fit.
- Survival analysis showed no statistically significant difference in mortality between treatment groups.
- Higher CD4 levels and absence of prior AIDS were associated with reduced mortality risk.

---

## Project Structure
```text
.
├── data/
│   ├── aids.csv
│   └── aids_id.csv
├── notebooks/
│   └── survival_analysis.ipynb
├── README.md
