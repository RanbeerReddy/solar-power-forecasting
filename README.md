# Solar Power Forecasting with Machine Learning

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-ff6f00)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-ff6f00)
![XGBoost](https://img.shields.io/badge/XGBoost-Enabled-2f8f3f)
![License](https://img.shields.io/badge/License-MIT-green)

![Project Banner](https://via.placeholder.com/1200x320.png?text=Solar+Power+Forecasting)

## Overview

This repository presents a reproducible machine-learning workflow for short-term solar power generation forecasting using historical generation and meteorological observations. The project compares a linear baseline, tree-based ensemble models, and a recurrent neural network approach in a controlled, time-aware evaluation setting.

## Motivation

Solar photovoltaic generation is inherently intermittent because it depends on weather conditions, irradiance, and temperature. Accurate short-term forecasting is essential for balancing the grid, reducing curtailment risk, and supporting the integration of renewable energy into modern power systems.

## Research Problem

The core research question is whether classical regression models and modern sequence models can predict plant-level AC power output reliably from meteorological features and recent temporal context. The study focuses on a single publicly available solar dataset and evaluates several model families under the same preprocessing and time-series constraints.

## Research Objectives

- Compare a linear baseline, tree-based ensembles, and a deep learning sequence model for short-term solar forecasting.
- Evaluate model performance using standard regression metrics.
- Investigate whether feature engineering and temporal context improve predictive quality.
- Document a reproducible workflow suitable for research, teaching, and portfolio showcases.

## Repository Structure

```text
.
├── README.md
├── requirements.txt
├── LICENSE
├── .gitignore
├── CITATION.cff
├── CONTRIBUTING.md
├── CHANGELOG.md
├── RELEASE_NOTES.md
├── data/
│   └── README.md
├── docs/
│   ├── 01_research_plan.md
│   ├── 02_dataset_comparison.md
│   └── 03_literature_review.md
├── figures/
│   └── README.md
├── notebook/
│   └── solar_power_forecasting.ipynb
└── report/
    └── Solar_Power_Forecasting_Report.pdf
```

## Installation

```bash
git clone https://github.com/RanbeerReddy/solar-power-forecasting.git
cd solar-power-forecasting
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Requirements

The notebook uses the following core libraries:

- Python 3.10+
- NumPy
- pandas
- Matplotlib
- Seaborn
- scikit-learn
- XGBoost
- TensorFlow (optional for the LSTM workflow)
- Jupyter / IPython

## Dataset

This project uses the public Kaggle dataset described in the documentation. The dataset is not stored in the repository because of size and licensing considerations.

Please follow the instructions in [data/README.md](data/README.md) to download and place the files in the expected local folder.

## Preprocessing Pipeline

1. Load time-stamped generation and weather sensor data.
2. Merge generation and weather observations on the shared timestamp column.
3. Handle missing values with a causal forward-fill strategy.
4. Clip non-physical negative power values.
5. Engineer calendar features, cyclical time features, and lag-based temporal features.
6. Split the data chronologically to avoid leakage.
7. Scale features for regression models that require it.

## Feature Engineering

The notebook adds:

- hour, day-of-week, and month indicators
- cyclical hour-of-day encoding
- lag features for AC power and irradiation
- rolling irradiance statistics

## Models Implemented

- Linear Regression (baseline)
- Random Forest Regressor
- XGBoost or Gradient Boosting Regressor (depending on availability)
- LSTM sequence model (when TensorFlow is available)

## Evaluation Metrics

The notebook reports:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R-squared (R²)

## Results Table

The exact metrics are generated when the notebook is executed. The repository preserves the evaluation workflow and exports figures to [figures/README.md](figures/README.md) for documentation.

| Model | MAE (kW) | RMSE (kW) | R² |
|------|--------:|----------:|---:|
| XGBoost | 248.58 | 472.93 | 0.9965 |
| Random Forest | 225.55 | 474.64 | 0.9964 |
| Linear Regression | 280.66 | 500.20 | 0.9960 |
| LSTM | 1313.05 | 2587.16 | 0.8939 |

## Key Findings

The repository is structured to support the following investigation:

- Irradiation and temperature are expected to be dominant predictors.
- Tree-based ensembles are expected to provide strong baselines.
- The LSTM model is included to test whether short-term temporal structure improves forecasting beyond engineered lag features.

## Workflow

```text
Data download
   -> Data cleaning and merging
   -> Feature engineering
   -> Time-aware train/test split
   -> Model training and tuning
   -> Evaluation and diagnostic plots
   -> Results summary and reporting
```

## Sample Output Images

The notebook writes figures to the [figures/](figures/) directory. Example output paths include:

- [figures/README.md](figures/README.md)
- figures/01_missing_values.png
- figures/02_target_distribution.png
- figures/03_time_series_relationships.png
- figures/04_correlation_heatmap.png
- figures/05_target_correlation.png
- figures/06_lstm_training_curve.png
- figures/07_metric_comparison.png
- figures/08_model_diagnostics.png
- figures/09_time_series_predictions.png
- figures/10_feature_importance.png
- figures/11_weather_regime_rmse.png

## Reproducibility

To reproduce the workflow:

1. Download the dataset into the local data folder as described in [data/README.md](data/README.md).
2. Install the dependencies from [requirements.txt](requirements.txt).
3. Open [notebook/solar_power_forecasting.ipynb](notebook/solar_power_forecasting.ipynb) in Jupyter.
4. Run the notebook from top to bottom.
5. Review the generated figures in [figures/](figures/).

## References

The research narrative and literature review are documented in [docs/03_literature_review.md](docs/03_literature_review.md). The dataset selection rationale is in [docs/02_dataset_comparison.md](docs/02_dataset_comparison.md).

## Citation

If you use this repository in a project or publication, please cite it using [CITATION.cff](CITATION.cff).

## Acknowledgements

This project was developed as a structured machine-learning research workflow and is intended to support reproducible experimentation and portfolio presentation.

## Future Work

Potential next steps include:

- adding probabilistic forecasting
- benchmarking more models such as CatBoost or Temporal Fusion Transformers
- evaluating on additional solar plants
- extending the notebook to support automated hyperparameter sweeps and experiment tracking

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
