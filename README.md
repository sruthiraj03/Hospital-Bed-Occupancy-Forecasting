# Hospital Bed Occupancy Forecasting
**Achieved <2% forecast error across Texas, California, and Florida using time series models on real-world CDC hospital data.**

Forecasting short-term hospital bed demand across three U.S. states to support healthcare staffing and resource planning.

## 📌 Overview

Weekly hospital bed demand is hard to predict until you model it.

Using **CDC National Healthcare Safety Network (NHSN)** data (Aug 2020 – May 2024), this project forecasts inpatient bed occupancy across California, Florida, and Texas - the three highest average bed utilization states in the U.S.

By capturing COVID-19 surges, seasonal respiratory cycles, and post-pandemic stabilization, the models achieve <2% MAPE on 13-week forecasts, supporting healthcare staffing and resource planning.

## 📊 Key Results

| State | Best Model | RMSE | MAPE |
|-------|-----------|------|------|
| Texas (TX) | ETS | 531.08 | 0.99% |
| California (CA) | SARIMAX (2,0,0)(1,0,0,52) | 877.99 | 1.15% |
| Florida (FL) | Seasonal ETS | 1,004.26 | 1.91% |

## 🧠 Key Skills Demonstrated

- Time Series Forecasting (ARIMA, SARIMA, SARIMAX, ETS)
- Data Cleaning & Preprocessing on real-world healthcare data (missing values, anomalies, structural breaks)
- Exploratory Data Analysis (trend, seasonality, and demand drivers)
- Model Selection, Evaluation, and Validation using AIC, BIC, RMSE, MAPE, and residual diagnostics
- Translating forecasts into actionable insights for healthcare staffing and capacity planning

## 💡 Business Impact
- **Texas:** Stable forecasts reduce the need for reactive surge planning and support efficient capacity management  
- **California:** COVID-19 and influenza admissions act as leading indicators, enabling early staffing adjustments before peak demand  
- **Florida:** Strong seasonal patterns enable proactive staffing and resource allocation ahead of predictable winter surges

## ✨ Highlights

- **COVID-19 admissions** were the strongest driver of occupancy surges nationally (r = 0.73), while influenza showed minimal correlation (r = -0.11)
- **No single model fits all states**: ETS outperformed SARIMAX for Texas, while California required seasonal and exogenous components to capture its strong winter peaks
- **Data quality issues handled**: corrected a Georgia data entry error (63M beds reported vs. ~31K actual) and removed post-May 2024 data following a mandatory-to-voluntary reporting shift that caused artificial declines

## 🔧 Methodology

**Data**
- **Source:** [Weekly Hospital Respiratory Data and Metrics](https://www.kaggle.com/datasets/noeyislearning/weekly-hospital-respiratory-data-and-metrics) (Kaggle / CDC NHSN)
- **Coverage:** National and state/territory level, August 2020 – May 2024 (mandated reporting period only)
- **Frequency:** Weekly
- **Key metrics:** Hospital capacity, inpatient bed occupancy, and new admissions for COVID-19, Influenza, and RSV
- **Target variable:** Number of Inpatient Beds Occupied
- **Exogenous variables:** Total COVID-19 Admissions, Total Influenza Admissions

**Preprocessing**
- Removed RSV variables due to <5% average reporting completeness
- Corrected Georgia outlier via linear interpolation
- Removed post-May 2024 data due to structural break from reporting policy change
- Applied linear interpolation, forward fill and backward fill for remaining missing values

**Modeling Pipeline (per state)**
1. Naïve baseline
2. Stationarity testing (ADF test) and ACF/PACF analysis
3. ARIMA order selection via AIC/BIC comparison
4. Full model comparison: ARIMA, ETS, Seasonal ETS, SARIMA, SARIMAX
5. Residual diagnostics (ACF, distribution check)
6. 13-week out-of-sample forecast on best model

## 🛠️ Technologies
 
- **Python** - pandas, numpy, statsmodels, matplotlib, seaborn
- **Models** - ARIMA, ETS, SARIMA, SARIMAX
- **Environment** - Google Colab

## ▶️ How to Run

1. Clone the repository  
2. Install dependencies: pip install -r requirements.txt 
3. Run the notebook (notebook.ipynb)  

Dataset available via link in Methodology section.

