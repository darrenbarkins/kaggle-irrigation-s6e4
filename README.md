# Kaggle Competition - Predicting Irrigation Need (S6E4)

## Overview
This repository contains my work for the Kaggle Playground 
Series Season 6 Episode 4 competition (Predicting Irrigation 
Need). The goal of the competition is to predict whether a 
field has a Low, Medium, or High irrigation need based on 
environmental and soil features.

- **Competition:** [Predicting Irrigation Need](https://www.kaggle.com/competitions/playground-series-s6e4)
- **Evaluation Metric:** Balanced Accuracy
- **Deadline:** April 30, 2026

---

## Homework Documents
- [Homework 2 — Bagging & Boosting](./Kaggle-Homework-Darren%20Barkins-darrenbarkins.md)
- [Homework 3 — Additional Boosting Models](./Kaggle-Homework-3-Darren-Barkins-darrenbarkins.md)

---

## Repository Structure

```
kaggle-irrigation-s6e4/
│
├── README.md
├── Kaggle-Homework-Darren Barkins-darrenbarkins.md
├── Kaggle-Homework-3-Darren-Barkins-darrenbarkins.md
├── notebooks/
│   ├── eda-irrigation-need-s6e4.ipynb
│   ├── s6e4-irrigation-need-random-forest.ipynb
│   ├── s6e4-irrigation-need-xgboost.ipynb
│   ├── s6e4-irrigation-need-lightgbm.ipynb
│   └── s6e4-irrigation-need-catboost.ipynb
└── data/
    └── README — dataset available on Kaggle
```

---

## Notebooks

| Notebook | Description | Link |
|----------|-------------|------|
| EDA | Exploratory data analysis | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/eda-irrigation-need-s6e4) |
| Random Forest | Bagging model baseline | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-random-forest) |
| XGBoost | Boosting model baseline | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-xgboost) |
| LightGBM | Boosting with hyperparameter tuning | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-lightgbm) |
| CatBoost | Boosting with hyperparameter tuning | [View on Kaggle](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-catboost) |

---

## Results

| Model | Type | CV Balanced Accuracy | Kaggle LB Score |
|-------|------|----------------------|-----------------|
| Random Forest | Bagging | 0.9553 ± 0.0026 | 0.95350 |
| XGBoost | Boosting | 0.9620 ± 0.0020 | 0.95987 |
| CatBoost | Boosting | 0.9690 ± 0.0017 | 0.96579 |
| LightGBM | Boosting | 0.9702 ± 0.0016 | 0.96791 |

---

## Tools Used
- Python
- Scikit-learn (Random Forest)
- XGBoost
- LightGBM
- CatBoost
- Pandas, NumPy, Matplotlib, Seaborn
