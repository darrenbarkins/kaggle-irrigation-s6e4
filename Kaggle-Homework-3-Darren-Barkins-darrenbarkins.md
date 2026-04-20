# Kaggle Homework 3 - Darren Barkins - darrenbarkins
## Competition: Predicting Irrigation Need (S6E4)
## Assignment: Additional Boosting Models

---

## Modeling Notebooks
- LightGBM: [S6E4 Irrigation Need - LightGBM](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-lightgbm)
- CatBoost: [S6E4 Irrigation Need - CatBoost](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-catboost)

---

## Modeling Results

| Model | Type | CV Balanced Accuracy | Kaggle LB Score |
|-------|------|----------------------|-----------------|
| Random Forest | Bagging | 0.9553 ± 0.0026 | 0.95350 |
| XGBoost | Boosting | 0.9620 ± 0.0020 | 0.95987 |
| CatBoost | Boosting | 0.9690 ± 0.0017 | 0.96579 |
| LightGBM | Boosting | 0.9702 ± 0.0016 | 0.96791 |

---

## LightGBM — Hyperparameter Exploration

| Set | Trees | Learning Rate | Depth | Leaves | CV Balanced Accuracy |
|-----|-------|---------------|-------|--------|----------------------|
| Set 1 — Baseline | 300 | 0.05 | 6 | 31 | 0.9699 |
| Set 2 — Complex | 500 | 0.03 | 8 | 63 | 0.9687 |
| Set 3 — Simpler | 400 | 0.08 | 5 | 20 | 0.9702 |

### LightGBM Notes
- Set 1 served as a solid starting point using near-default 
  settings and produced a strong baseline score of 0.9699.
- Set 2 increased tree complexity by adding more trees, 
  deeper depth, and more leaves. This slightly reduced 
  performance, suggesting the model began overfitting to 
  the training data with the added complexity.
- Set 3 pulled back on complexity with shallower trees and 
  fewer leaves while increasing the learning rate slightly. 
  This produced the best result of 0.9702, confirming that 
  simpler trees generalize better on this dataset.
- The best LightGBM submission achieved a leaderboard score 
  of 0.96791, the highest of all models tested so far.

---

## CatBoost — Hyperparameter Exploration

| Set | Trees | Learning Rate | Depth | Regularization | CV Balanced Accuracy |
|-----|-------|---------------|-------|----------------|----------------------|
| Set 1 — Baseline | 300 | 0.05 | 6 | None | 0.9667 |
| Set 2 — Deeper | 500 | 0.03 | 8 | l2=5 | 0.9669 |
| Set 3 — Faster | 600 | 0.08 | 7 | l2=3 | 0.9690 |

### CatBoost Notes
- Set 1 established a baseline score of 0.9667, slightly 
  lower than LightGBM's baseline but still a competitive 
  result.
- Set 2 added deeper trees and L2 regularization to prevent 
  overfitting. The improvement was minimal, suggesting 
  regularization alone was not enough to meaningfully 
  change performance.
- Set 3 used a faster learning rate with more trees and a 
  moderate depth, producing the best CatBoost result of 
  0.9690 and a leaderboard score of 0.96579.
- Each set showed gradual improvement, demonstrating that 
  tuning in a consistent direction does produce meaningful 
  gains even when individual steps are small.

---

## Model Comparison

Overall LightGBM performed the best across both cross 
validation and the Kaggle leaderboard, followed closely 
by CatBoost. Both outperformed the XGBoost and Random 
Forest models from the previous homework.

A consistent finding across both models was that moderate 
complexity tended to outperform either extreme. Very simple 
settings left performance on the table, while overly complex 
settings led to slight overfitting. The sweet spot for this 
dataset appeared to be a moderate number of trees with 
shallower depth and a slightly faster learning rate.

LightGBM's advantage over CatBoost may be partly due to 
its efficiency with large datasets at ~ 630,000 rows, 
LightGBM's row-wise processing gave it a speed and 
generalization edge. CatBoost is typically stronger when 
there are many categorical features, which was less of a 
factor here since most features were numeric.

---

## What Worked Well
- Both models performed competitively with relatively 
  little tuning effort, suggesting the features in this 
  dataset are informative and well structured.
- Using balanced class weights consistently across all 
  models helped handle the imbalance between Low, Medium, 
  and High irrigation need classes.
- Moderate complexity settings outperformed both very 
  simple and very complex configurations in both models.

---

## What Didn't Work Well
- Increasing tree complexity in Set 2 of both models 
  did not produce meaningful gains and in the case of 
  LightGBM actually reduced performance slightly.
- The gains between hyperparameter sets were relatively 
  small, suggesting that further improvement may require 
  feature engineering or ensemble methods rather than 
  hyperparameter tuning alone.

---

## Phase 2 Plan

Building on the results from both homeworks, the following 
directions are worth exploring next:

- **Ensemble stacking** — combining LightGBM, CatBoost, 
  and XGBoost predictions together into a single stacked 
  model, which was the approach used by the top scoring 
  public notebook to reach 0.970 balanced accuracy.
- **Feature engineering** — creating new features by 
  combining existing ones, such as a heat-wind index 
  using Temperature_C and Wind_Speed_kmh.
- **Optuna tuning** — using automated hyperparameter 
  optimization to search a wider range of settings more 
  efficiently than manual tuning.
- **Pseudo labeling** — adding the model's most confident 
  test predictions back into training data to give the 
  model additional examples to learn from.
