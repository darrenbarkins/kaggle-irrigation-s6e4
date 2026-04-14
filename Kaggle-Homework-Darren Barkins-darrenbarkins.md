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
- Link: [S6E4 Irrigation Need - EDA](https://www.kaggle.com/code/darrenbarkins/eda-irrigation-need-s6e4)

### Key Insights

- The training dataset contains 630,000 rows and 43 features 
  with no missing values, so no additional cleaning or 
  imputation was needed before modeling.

- The target classes are not evenly distributed. "Low" 
  irrigation need is the most common class with 369,917 rows, 
  "Medium" is noticeably smaller with 239,074 rows, and "High" 
  is the least represented with only 21,009 rows, creating a 
  staircase pattern. This is likely why the competition uses 
  balanced accuracy as its evaluation metric rather than 
  standard accuracy.

- Most features follow a roughly normal, bell-shaped 
  distribution. The one exception is "rainfall_mm," which 
  has a notably different distribution. This is expected, 
  as rainfall in nature tends to be skewed with occasional 
  spikes of heavy rain.

- The features most strongly correlated with Irrigation Need 
  are Wind_Speed_kmh, Temperature_C, Rainfall_mm, and 
  Electrical_Conductivity. Wind speed being the leading 
  predictor makes practical sense, as higher winds increase 
  evaporation and dry out soil more quickly. All correlation 
  values are relatively low however, suggesting no single 
  feature drives the prediction on its own.

- The correlation heatmap shows that most features are largely 
  independent from one another. The only mild exception is a 
  slight relationship between Soil_Moisture and Organic_Carbon, 
  which is expected in real-world agricultural data. Overall 
  this suggests there is little redundancy among the features, 
  meaning most columns are likely contributing unique 
  information to the model.

### Most Important Feature
- Wind_Speed_kmh showed the strongest relationship with 
  irrigation need, followed closely by Temperature_C.

### Potential Issues
- The significant class imbalance, particularly the small 
  number of "High" irrigation need cases, may make it 
  harder for models to accurately predict that class. 
  This was addressed in modeling by using balanced 
  class weights.

---

## Modeling Notebooks
- Bagging (Random Forest): [S6E4 Irrigation Need - Random Forest](https://www.kaggle.com/code/darrenbarkins/s6e4-irrigation-need-random-forest)
- Boosting (XGBoost): (link coming soon)

## Modeling Results

| Model | Type | CV Balanced Accuracy | Kaggle LB Score |
|-------|------|----------------------|-----------------|
| Random Forest | Bagging | 0.9553 ± 0.0026 | 0.95350 |
| XGBoost | Boosting | | |

### Random Forest Notes:
- Used 200 trees with balanced class weights to account 
  for the significant imbalance between Low, Medium, and 
  High classes.
- Cross validation was stable across all 5 folds, 
  suggesting the model is consistent and not overfitting.
- Achieved a cross validation balanced accuracy of 0.9553, 
  which is a strong baseline result.

### What worked:
### What didn't:
### Bagging vs Boosting comparison:

---

## Phase 2 Plan
...
