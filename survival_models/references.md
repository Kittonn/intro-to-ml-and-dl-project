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

## Cox Model Step

## Random Survival Forest Model
https://scikit-survival.readthedocs.io/en/stable/user_guide/random-survival-forest.html

For prediction, a sample is dropped down each tree in the forest until it reaches a terminal node. 
Data in each terminal is used to non-parametrically estimate the survival and cumulative hazard function 
using the Kaplan-Meier and Nelson-Aalen estimator, respectively. 
In addition, a risk score can be computed 
that represents the expected number of events for one particular terminal node. 
The ensemble prediction is simply the average across all trees in the forest.

## Plan

Cox Proportional Harzard Model, Kaplan-Meier, and Random Survival Forest can answer the same questions: "What's the chance that X event happen at Y time given it hasn't happen before?"

In my use cases, I had 2 questions.

Regression: How long will this breast cancer patient survive?
Classification: Will this breast cancer patient live longer than 6 years?

If I want to make a survival model that is more accurate than those regression and classification model. However, since the question is different, I need to find a way to make the survival model answer the "How long will this breast cancer patient survive?" somehow.

I can do this by getting the median or expected survival time from the model.

I want to make a random survival forest model from scratch, and before I code it out, I want to know about the general steps of the process of how this thing make a prediction. Like...

Decide hyperparameters
Bootstrap samples (bagging)
Build each survival tree

Compute survival curves in each leaf

Aggregate trees to get final survival estimates