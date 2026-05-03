# Kaggle Competition - Predicting Irrigation Need (S6E4)

## Overview
This repository contains my work for the Kaggle Playground Series Season 6 
Episode 4 competition (Predicting Irrigation Need). The goal is to predict 
whether a field has Low, Medium, or High irrigation need based on 
environmental and soil features.

- **Competition:** [Predicting Irrigation Need](https://www.kaggle.com/competitions/playground-series-s6e4)
- **Kaggle Username:** darrenbarkins
- **Evaluation Metric:** Balanced Accuracy

---

## Repository Structure

```
kaggle-irrigation-s6e4/
│
├── README.md
├── Kaggle-Homework-Darren-Barkins-darrenbarkins.md
└── notebooks/
    ├── eda-irrigation-need-s6e4.ipynb
    ├── s6e4-irrigation-need-random-forest.ipynb
    ├── s6e4-irrigation-need-xgboost.ipynb
    ├── s6e4-lightgbm.ipynb
    ├── s6e4-catboost.ipynb
    └── s6e4-feature-engineering-ensemble.ipynb
```

---

## Notebooks

| Notebook | Description | Link |
|----------|-------------|------|
| EDA | Exploratory data analysis | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/eda-irrigation-need-s6e4) |
| Random Forest | Bagging baseline model | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-random-forest) |
| XGBoost | Boosting baseline model | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-xgboost) |
| LightGBM | Boosting with hyperparameter tuning | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/s6e4-lightgbm) |
| CatBoost | Boosting with hyperparameter tuning | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/s6e4-catboost) |
| Feature Engineering & Ensemble | Feature engineering, selection, and probability averaging ensemble | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/notebook1fac9023fb) |

---

## Results Summary

| Homework | Model | Leaderboard Score |
|----------|-------|-------------------|
| HW2 | Random Forest | 0.95350 |
| HW2 | XGBoost | 0.95987 |
| HW3 | LightGBM | 0.96791 |
| HW3 | CatBoost | 0.96579 |
| HW4 | Ensemble (RF + XGB + LGB avg) | 0.95971 |

---

## Tools Used
- Python, Pandas, NumPy, Matplotlib
- Scikit-learn, XGBoost, LightGBM, CatBoost
- Kaggle Notebooks
- GitHub
