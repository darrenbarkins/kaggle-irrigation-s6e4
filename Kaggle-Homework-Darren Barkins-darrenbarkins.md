# Kaggle Homework - [Darren Barkins] - [darrenbarkins]
## Competition: Predicting Irrigation Need (S6E4)

---

## Upvoted Resources

1. [S6E4: 0.970 | Stacked LGB+XGB+CAT | Feature Engineering](https://www.kaggle.com/code/aliafzal9323/s6e4-0-970-stacked-lgb-xgb-cat-feature-engine)

   This notebook caught my attention because it reached a 0.970 balanced 
   accuracy score by combining three boosting models (LightGBM, XGBoost, 
   and CatBoost) into a single stacked approach. It also walks through 
   feature engineering steps specific to this dataset, which I plan to 
   reference when looking for ways to improve my own model.

2. [S6E4: Irrigation Prediction LightGBM Baseline](https://www.kaggle.com/code/sarcasmos/s6e4-irrigation-prediction-lightgbm-baseline)

   This notebook offers a straightforward starting point using LightGBM, 
   a boosting algorithm known for its speed and accuracy. Baseline 
   notebooks are helpful because they show a simple, working version of 
   the solution, giving me a clear benchmark to measure my own progress 
   against.

3. [S6E4: The Most Detailed EDA 100%](https://www.kaggle.com/code/aryankaisth/s6e4-the-most-detailed-eda-100)

   I found this notebook helpful because it takes a thorough look at all 
   the features in the dataset, including their distributions and 
   relationships with the target variable. I will use it as a guide when 
   building my own EDA notebook to better understand which features may 
   be most important for predicting irrigation need.

4. [PS6E4: XGB, cuDF + Pseudo Labels](https://www.kaggle.com/code/include4eto/ps6e4-xgb-cudf-pseudo-labels)

   This notebook introduces a technique called pseudo-labeling, where the 
   model's high-confidence predictions on the test set are used as 
   additional training data. While this is a more advanced approach than 
   what I am currently working on, the XGBoost pipeline it uses is 
   practical and gave me some ideas for how I might improve my model in 
   a later phase.

---

## EDA Notebook
- Link: [01_EDA.ipynb](./notebooks/01_EDA.ipynb)
- Key insights: ...

---

## Modeling

| Model | Type | CV Score | Kaggle LB Score |
|-------|------|----------|-----------------|
| Random Forest | Bagging | | |
| XGBoost | Boosting | | |

### What worked:
### What didn't:
### Bagging vs Boosting comparison:

---

## Phase 2 Plan
...
