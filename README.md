# F1 Race Winner Prediction from Qualifying Data

Predicting the winner of the Belgian Grand Prix using qualifying session data.

## Status

Working end-to-end: data pipeline, feature engineering, and model training/evaluation are done. Three classifiers have been trained and compared, and used to predict the 2026 Belgian GP podium.

## Goal

Build a machine learning model that predicts the race winner (not the full podium) based on qualifying results, with **qualifying lap times as the main feature**.

## Approach

1. **Data collection** — qualifying sessions (2021–2026) and race results (2021–2025) for the Belgian GP, pulled via the [FastF1](https://github.com/theOehrly/Fast-F1) API.
2. **Pre-processing** — drop non-predictive columns, convert Q1/Q2/Q3 lap times to seconds, fill missing values, one-hot encode team name.
3. **Feature engineering** — best qualifying time (`BestQualiTime`), and qualifying-round improvement gaps (`Q1_Q2_Improvement`, `Q2_Q3_Improvement`).
4. **Modeling** — race winner (binary target) predicted from qualifying features using:
   - Logistic Regression (baseline, with feature scaling)
   - Random Forest Classifier

## Results

Evaluated on a held-out test split:

| Model                | ROC AUC | Precision | Recall | F1 Score |
|----------------------|---------|-----------|--------|----------|
| Logistic Regression  | 0.935   | 0.500     | 1.000  | 0.667    |
| Random Forest        | 0.870   | 0.000     | 0.000  | 0.000    |

Logistic Regression catches every actual winner in the test set (Recall = 1.000) at the cost of some false positives (Precision = 0.500). Random Forest misses every winner in the test set at the default 0.5 threshold.

Predicted vs. actual podium, 2026 Belgian GP (Logistic Regression):

| place | predicted | actual |
|-------|-----------|--------|
| 1st   | ANT       | ANT    |
| 2nd   | RUS       | LEC    |
| 3rd   | NOR       | VER    |

The model correctly picked the race winner.

## Future Work

This project has potential, but there's still a lot to work on — the current models rely only on qualifying lap times and team, and the dataset is small (six years of a single track).

- **Weather conditions** — incorporate track/air temperature, rainfall, and wind from FastF1's weather data as features, since wet-weather qualifying pace doesn't always translate to race pace.
- **Safety car likelihood** — engineer a feature for the historical rate of safety car deployments at Spa, since a safety car reshuffles the race and can undercut a pure qualifying-based prediction.
- More historical data (more tracks/seasons) to reduce the class imbalance between winners and non-winners.

## Tech Stack

- Python 3.13
- FastF1
- pandas, numpy
- seaborn, matplotlib
- scikit-learn
- Jupyter Notebook