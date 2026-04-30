# Kaggle Homework - Darren Barkins - darrenbarkins
## Competition: Predicting Irrigation Need (S6E4)

---

## Upvoted Resources

1. [S6E4: 0.970 | Stacked LGB+XGB+CAT | Feature Engineering](https://www.kaggle.com/code/aliafzal9323/s6e4-0-970-stacked-lgb-xgb-cat-feature-engine)

   This notebook reached 0.970 balanced accuracy by combining LightGBM, 
   XGBoost, and CatBoost into a stacked ensemble with feature engineering. 
   It shaped much of my approach for later homeworks.

2. [S6E4 EDA + Baseline](https://www.kaggle.com/code/mehranhamidian/s6e4-eda-baseline)

   A clean EDA notebook that helped me understand the feature distributions 
   and class imbalance in this dataset early on.

3. [S6E4 XGBoost Tuned](https://www.kaggle.com/code/tumpossible/s6e4-xgboost-irrigation)

   Useful for understanding how to tune XGBoost hyperparameters specifically 
   for this competition's target metric.

4. [S6E4 Feature Engineering Ideas](https://www.kaggle.com/code/paddykb/s6e4-feature-engineering)

   Explored interaction features between weather and soil variables, which 
   gave me ideas for my own feature engineering in HW4.

---

## Homework 2 — Baseline Models

### Notebooks
- [EDA Notebook](https://www.kaggle.com/code/darrenbarkins/eda-irrigation-need-s6e4)
- [Random Forest Notebook](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-random-forest)
- [XGBoost Notebook](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-xgboost)

### Results

| Model | Validation Balanced Accuracy | Leaderboard Score |
|-------|------------------------------|-------------------|
| Random Forest | 0.954 | 0.95350 |
| XGBoost | 0.960 | 0.95987 |

### Discussion

The dataset has three classes (Low, Medium, and High irrigation need) 
with a noticeable imbalance (High is only ~3% of the data). This made 
balanced accuracy the right metric to optimize, since regular accuracy 
would be misleading.

Random Forest served as a solid baseline. XGBoost improved on it slightly, 
likely because boosting is better at correcting errors on the minority class. 
Both models used imbalance-handling parameters (class_weight='balanced' for 
RF, scale_pos_weight for XGBoost).

---

## Homework 3 — LightGBM & CatBoost

### Notebooks
- [LightGBM Notebook](https://www.kaggle.com/code/darrenbarkins/s6e4-lightgbm)
- [CatBoost Notebook](https://www.kaggle.com/code/darrenbarkins/s6e4-catboost)

### Results

| Model | Hyperparameters Tested | Best Leaderboard Score |
|-------|------------------------|------------------------|
| LightGBM | 3 sets (learning rate, depth, estimators) | 0.96791 |
| CatBoost | 3 sets (depth, iterations, learning rate) | 0.96579 |

### Discussion

LightGBM was the strongest individual model tested so far, reaching 0.96791 
on the leaderboard. Its leaf-wise tree growth gave it an edge on this dataset 
compared to the level-wise approach used by XGBoost and Random Forest.

CatBoost also performed well but required more careful preprocessing, 
categorical columns needed to be handled in a specific order to avoid errors. 
Cross-validation wasn't feasible with CatBoost's cat_features parameter, so 
test set scores were used instead.

Both models confirmed that boosting approaches outperform bagging on this 
dataset.

---

## Homework 4 — Feature Engineering, Selection & Ensemble

### Notebook
- [Feature Engineering & Ensemble Notebook](https://www.kaggle.com/code/darrenbarkins/notebook1fac9023fb?scriptVersionId=315640273)

### Feature Engineering

Five new features were created based on real-world relationships between 
weather, soil, and irrigation:

| Feature | Description |
|---------|-------------|
| Temp_Humidity_interaction | Temperature × Humidity (heat stress proxy) |
| Rainfall_per_SunHour | Rainfall ÷ Sunlight Hours (evaporation risk) |
| Moisture_Carbon_ratio | Soil Moisture ÷ Organic Carbon |
| Wind_Humidity_interaction | Wind Speed × Humidity |
| Prev_Irrigation_per_Area | Previous Irrigation ÷ Field Area |

### Feature Selection

A quick Random Forest (100 trees) was used to assess feature importance 
across all 48 features. The top features were Soil_Moisture, Temperature_C, 
and Moisture_Carbon_ratio, confirming that the engineered features added 
value. Wind_Speed_kmh and Rainfall_mm also ranked highly. All 5 engineered 
features were retained based on their importance scores.

### Models & Results

| Model | Validation Balanced Accuracy | Leaderboard Score |
|-------|------------------------------|-------------------|
| Random Forest | 0.9628 | — |
| XGBoost | 0.9650 | — |
| LightGBM | 0.9649 | — |
| **Ensemble (avg)** | **0.9654** | **0.95971** |

### Discussion

Three models were trained, Random Forest, XGBoost, and LightGBM — each 
using their respective imbalance-handling parameters. All three performed 
closely, with XGBoost and LightGBM tied at around 0.965 validation balanced 
accuracy.

The ensemble combined predictions by averaging the predicted probabilities 
from all three models equally. This produced a small but consistent 
improvement over any individual model on the validation set (0.9654 vs 
0.9650). The leaderboard score came in at 0.95971.

A StackingClassifier with Logistic Regression as the meta-model was 
attempted but proved too computationally expensive for Kaggle's free tier 
on 630,000 rows. Probability averaging was used as an effective and 
lightweight alternative.

Feature engineering contributed meaningfully, Moisture_Carbon_ratio 
appeared in the top 20 features, confirming that creating ratio-based 
features can surface patterns not visible in the raw columns alone.

Moving forward, more aggressive feature engineering and threshold tuning 
could help push the leaderboard score further.
