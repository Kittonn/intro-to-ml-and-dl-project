# intro-to-ml-and-dl-project

## prerequisites

The tree for Decision Tree can be shown using this package.
```bash
brew install graphviz
```

## preprocessing

- df_balanced_classification (downsampled, TMN, no non medical: race, marital status)
- df_unbalanced_classification (TMN, no non medical: race, marital status)
- test_df_unbalanced_classification (downsampled, onehot race, marital status, TMN)
- Label_Encoded_Breast_Cancer (oversampled, all features, all label encoded)

## classification cheatsheet

Can you make like a cheatsheet as to which of these algorithm to choose based on what?

- Logistic Regression
- Decision Tree
- Random Forest
- Naive Bayes
- Support Vector Machine

## presentation

the data is really imbalance in many features

Decision Tree & RF
https://www.kaggle.com/code/albertobircoci/decisiontree-randomforest#Decisional-Tree-&-Random-Forest

- sample alive to be 2*dead
- grid search

acc: 0.8

5 Models | 97%
https://www.kaggle.com/code/mohammedezzeldean/breast-cancer-prediction-5-models-97

- handle imbalanced data with over sampling

## interesting references

- https://www.kaggle.com/code/albertobircoci/decisiontree-randomforest#Models
- https://www.kaggle.com/code/antoniosabatini/techniques-for-highly-unbalanced-data
- 5 Model 97% https://www.kaggle.com/code/mohammedezzeldean/breast-cancer-prediction-5-models-97
- https://www.kaggle.com/code/saeedeheydarian/recall-97-xgboost-and-randomforest