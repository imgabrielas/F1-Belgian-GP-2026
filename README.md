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
   - Gradient Boosting Classifier

## Results

Evaluated on a held-out test split:

| Model                | ROC AUC |
|----------------------|---------|
| Logistic Regression  | 0.935   |
| Random Forest        | 0.870   |
| Gradient Boosting    | 0.957   |

Logistic Regression detail: F1 = 0.667, Accuracy = 0.920, Precision = 0.500, Recall = 1.000 (catches every actual winner, with some false positives).

Predicted vs. actual podium, 2026 Belgian GP (Logistic Regression):

| place | predicted | actual |
|-------|-----------|--------|
| 1st   | ANT       | ANT    |
| 2nd   | RUS       | LEC    |
| 3rd   | NOR       | VER    |

The model correctly picked the race winner.

## Tech Stack

- Python 3.13
- FastF1
- pandas, numpy
- seaborn, matplotlib
- scikit-learn
- Jupyter Notebook