# Dataset Guide

The solar forecasting dataset used in this project is a public Kaggle dataset and is not stored in this repository.

## Why the dataset is not stored here

- The dataset files are larger than what is appropriate for a source repository snapshot.
- The project is designed to remain lightweight and reproducible.
- The original dataset remains under the upstream Kaggle source and can be downloaded directly.

## Kaggle download link

https://www.kaggle.com/datasets/anikannal/solar-power-generation-data

## Expected local folder structure

Place the downloaded files in a local data directory with the following structure:

```text
data/
├── Plant_1_Generation_Data.csv
└── Plant_1_Weather_Sensor_Data.csv
```

## Filenames

The notebook expects the following files:

- Plant_1_Generation_Data.csv
- Plant_1_Weather_Sensor_Data.csv

## Instructions

1. Download the Kaggle archive and extract it locally.
2. Copy the CSV files into the repository data folder.
3. Launch the notebook and run it from the repository root.
4. Keep the dataset out of Git commits by relying on the patterns in .gitignore.
