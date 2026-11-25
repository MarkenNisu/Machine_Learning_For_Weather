# Forecast Fusion

**Authors:** Marken Nisu, Pert Koduvere

## Project Overview

This project investigates the accuracy of weather forecasts in the Tartu-Tõravere region of Estonia during the summers of 2024–2026.

We compare three weather forecasting models: ECMWF, GFS, and ICON-EU. We also investigate whether machine learning can improve forecasting accuracy by combining predictions from these models.

## Research Questions

1. Which weather forecasting model provides the most accurate predictions for temperature, precipitation, and wind speed?
2. Can machine learning improve forecasting accuracy by combining predictions from ECMWF, GFS, and ICON-EU?

## Dataset

The dataset combines actual weather observations from the Estonian Environment Agency's Tartu-Tõravere weather station with historical 24-hour-ahead forecasts from the Open-Meteo Previous Runs API.

- **Period:** June–August, 2024–2026
- **Location:** Tartu-Tõravere, Estonia
- **Observations:** 6,624 hourly records
- **Columns:** 13
- **Variables:** Temperature (°C), precipitation (mm/h), and wind speed (m/s)

The prepared dataset is located at `data/processed/weather_dataset_2024_2026.csv`.

## Project Structure

- `01_eda.ipynb` – Exploratory data analysis and visualizations.
- `02_forecast_evaluation.ipynb` – Evaluation and comparison of the original forecasting models.
- `03_machine_learning.ipynb` – Machine learning models, training, evaluation, and visualizations.
- `ML_testing.ipynb` – Additional machine learning experiments, model comparisons, hyperparameter tuning, and previously created visualizations, including prediction plots, error comparisons, and confusion matrices.
- `data/processed/` – Prepared weather dataset used for analysis.

## Methods

For temperature and wind speed prediction, we tested Linear Regression and Random Forest Regressor.

For precipitation occurrence, we tested Logistic Regression and Random Forest Classifier.

The dataset was split chronologically:

- **2024:** Training
- **2025:** Validation and model selection
- **2026:** Independent testing

After model selection, the final models were retrained using data from both 2024 and 2025.

We used MAE and RMSE to evaluate temperature and wind speed predictions, and precision, recall, accuracy, and F1-score for precipitation classification.

## Main Results

ICON-EU was the most accurate original forecasting model according to our primary evaluation metrics.

On the independent 2026 test dataset, Linear Regression reduced temperature MAE by 2.89% and wind speed MAE by 7.79% compared to ICON-EU.

For precipitation occurrence, Logistic Regression achieved an F1-score of 0.5319, compared to 0.5314 for ICON-EU. The difference was negligible.

Overall, machine learning improved temperature and wind speed prediction accuracy, while precipitation classification showed no meaningful improvement in F1-score.

## How to Reproduce the Analysis

1. Clone or download the repository.
2. Install Python and Jupyter Notebook.
3. Install the required libraries:

   `pip install pandas numpy matplotlib seaborn scikit-learn`

4. Ensure the prepared dataset is available in `data/processed/`.
5. Open Jupyter Notebook and run the following notebooks:
   - `01_eda.ipynb` – Exploratory data analysis.
   - `02_forecast_evaluation.ipynb` – Weather forecast model comparison.
   - `03_machine_learning.ipynb` – Machine learning models and final evaluation.
   - `ML_testing.ipynb` – Additional machine learning experiments, model comparisons, hyperparameter tuning, and visualizations.
6. All four notebooks should be executed to reproduce the complete analysis. The `03_machine_learning.ipynb` and `ML_testing.ipynb` notebooks can be run in either order, as they are independent of each other.
7. Adjust the dataset paths if necessary depending on the Jupyter working directory.

## Data Sources

- Estonian Environment Agency – Tartu-Tõravere weather station observations.
- Open-Meteo Previous Runs API – Historical forecasts from ECMWF, GFS, and ICON-EU.