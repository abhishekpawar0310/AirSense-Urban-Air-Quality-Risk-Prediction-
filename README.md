# AirSense: Urban Air Quality Risk Prediction

Analyzing 5 years of real government air quality data to identify high-risk pollution zones, uncover the biggest drivers of poor air quality, and forecast next-day AQI across major Indian cities.

## 📌 Overview

Air pollution is one of India's most pressing public health issues, but most public dashboards just display raw AQI numbers without explaining *why* a day is risky or *what's coming next*. AirSense goes a step further — it builds a transparent, health-weighted risk score, classifies each day into an official risk category using machine learning, and forecasts tomorrow's AQI, all on real government-collected data.

## 📂 Dataset

- **Source:** Central Pollution Control Board (CPCB), Government of India
- **Coverage:** 26 major Indian cities, daily readings from 2015–2020
- **Size:** 29,531 records, 16 columns (24,850 after cleaning)
- **Variables:** PM2.5, PM10, NO, NO2, NOx, NH3, CO, SO2, O3, Benzene, Toluene, Xylene, AQI, AQI Bucket
- **Type:** 100% real, publicly released sensor data — no synthetic or simulated values

## 🛠️ Tech Stack

- **Language:** Python 3
- **Data handling:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Machine Learning:** Scikit-learn (Random Forest Classifier & Regressor)
- **Environment:** Google Colab / Jupyter Notebook

## 🔍 Methodology

1. **Data Cleaning** — Interpolated short sensor gaps within each city's own time series; removed records with no verifiable AQI value.
2. **Feature Engineering** — Extracted year, month, day-of-week, and season; added a lag feature (previous day's AQI) to enable forecasting.
3. **Composite Health Risk Score** — A custom 0–100 score weighting pollutants by real health impact (PM2.5 35%, PM10 25%, NO2 15%, SO2 10%, CO 10%, O3 5%).
4. **Model A — Risk Classification:** Random Forest Classifier predicting the official CPCB risk category (Good → Severe) from raw pollutant readings.
5. **Model B — AQI Forecasting:** Random Forest Regressor predicting tomorrow's AQI value using today's readings + lag feature.

## 📊 Key Results

| Model | Metric | Score |
|---|---|---|
| Risk Category Classifier | Accuracy | ~82% |
| Next-Day AQI Forecast | R² Score | ~0.91 |
| Next-Day AQI Forecast | MAE | ~18–21 AQI points |

**Top insights:**
- Ahmedabad, Delhi, and Patna recorded the highest average AQI across the 5-year period.
- PM2.5 and CO were the strongest predictors of AQI risk category — consistent with established public-health research on particulate matter.
- AQI is highly seasonal, with winter months showing sharply elevated pollution levels across nearly every city (crop-burning season combined with lower wind dispersal).

## 🚀 How to Run

1. Open `AirSense_Project.ipynb` in [Google Colab](https://colab.research.google.com/).
2. Runtime → Run all — no installs or manual downloads required; the notebook pulls the dataset directly from a public URL.
3. Outputs (cleaned dataset, trained models, city summary) are saved automatically and can be downloaded from the Colab file panel.

## 📜 Data Attribution

Data originally published by the Central Pollution Control Board (CPCB), Government of India, via [cpcb.nic.in](https://cpcb.nic.in/). Used here for academic and research purposes.

## 👤 Author

**Pawar Abhishek Kishor**
Msc Data Science | Data Analytics & Machine Learning Enthusiast
