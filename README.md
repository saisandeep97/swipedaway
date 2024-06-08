Swiped Away: Decoding Fraud in the Digital Wallet
A case study on credit card fraud detection
Data Loaing & Cleaning
Empty columns were removed.
Missing values in some columns were imputed with "Unknown".
Duplicate columns (e.g., account number and customer ID) were identified and removed.
Data Exploration
The dataset is highly imbalanced (1.58% fraudulent transactions).
Most transactions (99%) originated from the United States.
Online transactions (cardholder not present) were most frequent (80%).
Transaction amount follows a Pareto distribution (many small transactions, few large ones).
Fraudulent transactions are more likely for higher amounts (except for very high amounts).
Reversal and multi-swipe transactions were identified and analyzed.
Certain account number prefixes correlated with higher fraud rates.
An upward trend in transaction volume with a constant fraud rate was observed over time.
Merchant names with unknown country codes or POS entry modes had higher fraud rates.
Transaction categories like online gifts and rideshare had higher fraud rates.
Incorrect CVV entries increased fraud likelihood, while incorrect expiry dates did not.
Feature Engineering
Hamming distance was used to measure CVV difference from the correct value.
Date features (year, month, etc.) were extracted from datetime columns.
Low-frequency merchant names were grouped into a single category.
Categorical data was encoded using one-hot encoding.
Modeling
F1 score, AUC-ROC, and precision-recall were used for evaluation (class imbalance).
The dataset was standardized before modeling.
Class weights were used to emphasize the minority fraud class.
XGBoost achieved the best performance ( AUC-ROC: 0.7626, Accuracy - 98%).
Things that didn't work
To handle class imbalance, data balancing techniques such as SMOTE and majority class downsampling were attempted but didn't give expected results.
To encode categorical variables, the label encoder technique was attempted but didn't work well as label encoding works well only for data when ordinality is present.
Although various models including Logistic Regression, Random Forest, Decision Trees, and neural networks were used for model building, apart from XGBoost, the remaining models were not able to generate accurate predictions.
Further Roadmap
A thorough analysis of incorrectly tagged predictions can help us identify patterns missing in our input variables.
Generate a User-Merchant matrix and use dimensionality reduction techniques such as PCA to create merchant and user vectors.
Detailed analysis of fraud transactions from a time series dimension to understand if there are any patterns and incorporate them as features in our model.
An ensemble of multiple models with different sets of input features can help improve model performance.
Refine the set of input features by analyzing top important features and remove features that aren't necessary.
