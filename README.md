#  Pesticide Use and Crop Yield Analysis in Kenya from 1990-2022 
### Data Analysis, Forecasting & Machine Learning Project

##  Project Overview

Agricultural productivity remains central to food security, economic stability, and climate resilience in Kenya. One of the most debated drivers of crop productivity is the use of pesticides: while they can increase yields, excessive or inefficient use raises environmental, health, and sustainability concerns.

This project analyzes the **relationship between pesticide usage and crop yields** over time and applies **time-series forecasting and machine learning techniques** to project future crop yields up to **2030**.

---
Link to view the notebook: https://nbviewer.org/github/BrentOchieng/crop-yield-prediction-with-pesticide-data/blob/main/pesticide_usage_and_crop_analysis_trend_in_kenya_.ipynb
---

The project combines:
- Exploratory Data Analysis (EDA)
- Time-series forecasting using **Facebook Prophet**
- Supervised Machine Learning using **Gradient Boosting Regression**
- An interactive **Streamlit dashboard** for visualization and insights

The goal is not just prediction, but **evidence-based insights** that can inform agricultural policy, sustainability planning, and data-driven decision-making.

---

##  Dataset Description

The dataset contains annual observations with:
- **Year**
- **Pesticide usage** (kg/ha and tonnes/ha)
- Crop yields for:
  - Wheat
  - Rice
  - Barley
  - Maize
  - Sorghum
  - Millet
  

The data is structured as a **time series**, making it suitable for both forecasting and temporal machine learning approaches.

---

##  Exploratory Data Analysis (EDA)

### Objectives
The EDA section aims to:
- Understand long-term trends in pesticide usage
- Analyze historical yield patterns across multiple crops
- Identify correlations, volatility, and structural changes over time
- Establish whether pesticide use and yields move together or diverge

### Key Insights
- Pesticide usage shows a **clear upward trend**, reflecting intensification of agriculture.
- Crop yield trends vary by crop, indicating **non-uniform responses** to pesticide application.
- Some crops show diminishing yield gains despite increasing pesticide use, raising sustainability concerns.
- Strong temporal structure justified the use of **time-aware models** rather than random train-test splits.

---

## Time-Series Forecasting (Prophet)

### Why Prophet?
Prophet was selected because it:
- Handles **time-series data** effectively
- Captures long-term trends without requiring extensive feature engineering
- Is robust to small datasets
- Produces **interpretable forecasts with uncertainty intervals**

Each crop was modeled independently using:
- Year as the time variable
- Crop yield as the target

### Outputs
- Forecasted yields from **2024 to 2030**
- Trend components for each crop
- Upper and lower confidence intervals

### Limitations
- Prophet models **trends, not causal relationships**
- Pesticide usage is not directly modeled as a driver unless added as an external regressor

---

##  Machine Learning Section (Gradient Boosting)

### Why Machine Learning?
While Prophet captures *trends*, it does not model **relationships between variables**.  
To understand how pesticide usage influences crop yields, a supervised ML approach was necessary.

### Model Choice: Gradient Boosting Regressor

Gradient Boosting was selected because:
- It captures **non-linear relationships**
- Performs well on small to medium-sized datasets
- Handles feature interactions naturally
- Outperforms linear models when effects are complex

### Features Used
- Current pesticide usage
- Lagged pesticide usage (previous year)
- Lagged crop yield (previous year)
- Year (as a numerical feature)

Lag features allow the model to:
- Capture delayed effects of pesticide application
- Learn yield momentum and inertia

### Validation Strategy
- **TimeSeriesSplit cross-validation** to avoid data leakage
- Evaluation metrics:
  - MAE (Mean Absolute Error)
  - RMSE (Root Mean Squared Error)
  - R² Score

### Key Findings
- ML models revealed that yield response to pesticide use is **non-linear**
- Marginal gains diminish beyond certain pesticide levels
- Lagged yields were strong predictors, highlighting persistence effects in agriculture

---

## Streamlit Dashboard

An interactive Streamlit app was developed to make insights accessible.

### Dashboard Features
**Page 1: Exploratory Analysis**
- Pesticide usage trends
- Individual crop yield trends
- Multi-crop comparisons

**Page 2: Forecasting Results**
- Prophet-based yield projections to 2030
- Crop-by-crop selection
- Visualization of uncertainty bands

The dashboard enables policymakers, researchers, and stakeholders to explore scenarios without writing code.

---

## Policy & Practical Implications

- Rising pesticide usage does not guarantee proportional yield gains
- Data supports the need for **precision agriculture**
- Forecasts highlight crops at risk of stagnation or decline
- Evidence can inform:
  - Sustainable pesticide regulation
  - Crop-specific intervention strategies
  - Long-term food security planning

---

##  Limitations & Future Work

- Dataset size limits deep learning approaches
- Weather and soil variables were not included
- Future improvements could include:
  - Climate data integration
  - Regional-level modeling
  - Causal inference techniques
  - Multi-output ML models

---

##  Tech Stack

- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn
- Prophet


---




