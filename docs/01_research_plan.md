# Research Plan

**Research Title:** A Comparative Study of Machine Learning Models for Short-Term Solar Power Generation Forecasting Using Meteorological Data

---

## 1. Research Problem

Solar photovoltaic (PV) generation is highly intermittent because it depends directly on weather conditions such as solar irradiance, ambient temperature, cloud cover, and humidity. This variability makes it difficult for grid operators to balance supply and demand, schedule backup generation, and integrate growing shares of solar capacity without risking curtailment, instability, or financial loss. Traditional physical forecasting methods (e.g., Numerical Weather Prediction) and classical statistical models (e.g., ARIMA) struggle to capture the non-linear relationships between meteorological variables and power output, particularly over short forecasting horizons (minutes to a day ahead). Machine learning (ML) models have shown strong potential to model these non-linear dependencies, but the literature reports inconsistent conclusions about which model family (tree-based ensembles, kernel methods, or deep sequence models) performs best, largely because studies use different sites, datasets, feature sets, and evaluation protocols. There is therefore a practical need for a controlled, reproducible comparison of several ML models on a single, well-documented dataset with matched meteorological features.

## 2. Research Gap

From the literature (see Section: Literature Review), three gaps recur:

1. **Inconsistent comparative evidence.** Studies rarely compare more than two or three algorithms under identical preprocessing, feature sets, and train/test splits, making cross-study comparison unreliable (Aouidad and Bouhelal, 2024; Rahimi et al., 2023).
2. **Limited attention to preprocessing and evaluation design.** Many papers report headline accuracy metrics without examining how missing values, zero-inflated night-time readings, or skewed weather variables affect model behaviour, and without stress-testing models on peak generation periods, which are operationally the most important (Aouidad and Bouhelal, 2024).
3. **Narrow model coverage.** Several studies focus only on either classical ML (Random Forest, XGBoost) or only deep learning (LSTM), rather than benchmarking both families side by side on the same short-term regression task (Balal et al., 2023; Ledmaoui et al., 2023).

This project addresses these gaps by benchmarking a linear baseline, two tree-based ensembles (Random Forest, Gradient Boosting/XGBoost), and a sequence model (LSTM) on one publicly available, meteorologically rich dataset, using a single reproducible pipeline, consistent evaluation metrics, and explicit analysis of error behaviour under different weather conditions.

## 3. Aim

To develop, compare, and evaluate multiple machine learning models for short-term solar power generation forecasting using historical meteorological and power-output data, in order to identify which model provides the most accurate and reliable predictions.

## 4. Objectives

1. To review and synthesise recent peer-reviewed literature on ML-based solar power forecasting and identify the research gap this project addresses.
2. To identify, compare, and select a suitable public dataset containing solar power generation and meteorological data.
3. To design a reproducible data preprocessing pipeline (cleaning, missing-value handling, feature engineering, train/test splitting) suitable for short-term regression forecasting.
4. To implement at least four machine learning models (Linear Regression as baseline, Random Forest, Gradient Boosting/XGBoost, and LSTM) for predicting short-term solar power output.
5. To evaluate and compare model performance using standard regression metrics (MAE, RMSE, R²) and error analysis across different weather conditions.
6. To interpret feature importance and discuss the practical implications of the findings for solar power grid management.

## 5. Research Questions

- **RQ1:** Which meteorological variables have the strongest influence on short-term solar power generation?
- **RQ2:** How do tree-based ensemble models (Random Forest, Gradient Boosting) compare with a deep learning sequence model (LSTM) in short-term solar power forecasting accuracy?
- **RQ3:** How does model performance vary between clear-sky and cloudy/variable weather conditions?
- **RQ4:** What is the trade-off between model complexity/training time and forecasting accuracy for this task?

## 6. Hypothesis

**H1:** Ensemble tree-based models (Random Forest and Gradient Boosting/XGBoost) will achieve lower prediction error (RMSE, MAE) than a simple linear regression baseline on short-term solar power forecasting, because they can capture non-linear relationships between irradiance, temperature, and power output.

**H2:** The LSTM model will outperform the tree-based models specifically in capturing short-term temporal dependencies (e.g., ramp-up/ramp-down periods), but this advantage will diminish if temporal/lag features are also engineered into the tree-based models.

**H0 (null):** There is no statistically meaningful difference in forecasting accuracy (RMSE/MAE) between the tree-based ensemble models and the LSTM model on this dataset.

*(These are stated as testable expectations to be confirmed or rejected by the experimental results in the notebook — not pre-determined conclusions.)*

## 7. Scope

- **Included:** Short-term forecasting (15-minute to intra-day / next-day horizon) of solar PV power output using historical power generation and co-located meteorological sensor data (irradiance, ambient temperature, module temperature). Comparison limited to four representative, commonly used model families: linear regression (baseline), Random Forest, Gradient Boosting (XGBoost), and LSTM.
- **Excluded:** Long-term (seasonal/annual) energy yield forecasting; satellite-image or sky-image—based nowcasting; multi-site spatial forecasting; probabilistic/interval forecasting; economic/market-impact analysis; and forecasting for wind or hybrid renewable systems.
- **Dataset boundary:** The project uses a single publicly available dataset (see dataset comparison) to ensure full reproducibility within the time and computational constraints of a mini research project.

## 8. Expected Contribution

- A reproducible, openly documented ML pipeline and Jupyter notebook comparing four model families under identical preprocessing and evaluation conditions, usable as a template for similar forecasting projects.
- Empirical evidence (with real, non-fabricated results filled in after running the notebook) on the relative accuracy and computational cost of classical vs. deep learning approaches for short-term solar forecasting on a real-world Indian solar plant dataset.
- A thematic synthesis of recent peer-reviewed literature that clarifies where consensus exists (e.g., irradiance as the dominant predictor) and where it does not (e.g., which model family is universally "best").
- Practical insight for small-to-medium solar plant operators on which low-cost, easily deployable model provides an acceptable accuracy/complexity trade-off for day-to-day forecasting.
