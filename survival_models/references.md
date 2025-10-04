# Reference

<!-- You can ask KP since he's doing model for churning which probably has censored data -->

## ChatGPT

Regression

| Model Type                 | Model                                                                              | Notes                                                                                                                          |
| -------------------------- | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Tree-based (nonlinear)** | 🌳 **Random Forest Regressor**                                                     | Great baseline; robust, interpretable (feature importances). May overfit small data.                                           |
|                            | 🌲 **Gradient Boosting / XGBoost / LightGBM / CatBoost**                           | Often best for tabular data. Can handle nonlinear feature interactions.                                                        |
| **Linear models**          | 📈 **Linear Regression / Ridge / Lasso**                                           | Simple baseline. Works well if data has linear trends.                                                                         |
| **Neural models**          | 🧠 **MLPRegressor (small NN)**                                                     | Good if you have a large dataset; otherwise may overfit.                                                                       |
| **Survival-specific**      | ⏳ **Cox Proportional Hazards Model**, **Kaplan–Meier**, **Random Survival Forest** | If you have *censored data* (e.g., patient still alive at last follow-up), use these — they’re designed for survival analysis. |

Classification

| Model Type        | Model                                      | Notes                                                                                        |
| ----------------- | ------------------------------------------ | -------------------------------------------------------------------------------------------- |
| **Tree-based**    | 🌳 **Random Forest Classifier**            | Strong baseline. Nonlinear, interpretable, handles missing data fairly well.                 |
|                   | 🚀 **XGBoost / LightGBM / CatBoost**       | Usually best for tabular classification. Handles imbalanced data well.                       |
| **Probabilistic** | 📦 **Naive Bayes (Gaussian or Bernoulli)** | Simple and interpretable, but assumes feature independence.                                  |
| **Linear**        | 📈 **Logistic Regression**                 | Good for interpretability and small datasets. Works well if features are linearly separable. |
| **Neural**        | 🧠 **MLPClassifier (small NN)**            | Only beneficial if you have lots of data and nonlinear patterns.                             |


## Survival Analysis & Censored Data
https://bdi.or.th/big-data-101/survival-analysis/

Censored data is data with unknown result at the time

Survival Months is censored because
- Some people are still alive at the time
- They could be dead later
- Missing follow up

Censored data can make normal regression analysis inaccurate

## Cox Model with Code Example
https://www.geeksforgeeks.org/data-science/cox-proportional-hazards-model/

Cox model short explanation with code example.

Cox answers
```
How does each variable (like age, gender, income, etc.) affect the risk of the event happening at any point in time?
```

Censoring happens when we don't see the event before the end of the study (e.g., the customer hasn’t left yet).

It does not assume any particular shape for the distribution of survival times, which makes it a semi-parametric model.

Cox calculate harzard.
Hazard is just the risk of the event happening right now.