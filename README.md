<h1>Swiped Away: Decoding Fraud in the Digital Wallet</h1>
<h2>A case study on credit card fraud detection</h2>
<h2>Data Loaing & Cleaning</h2>
<ul>
<li>Empty columns were removed.</li>
<li>Missing values in some columns were imputed with "Unknown".</li>
<li>Duplicate columns (e.g., account number and customer ID) were identified and removed.</li>
</ul>

<h2>Data Exploration</h2>
<ul>
<li>The dataset is highly imbalanced (1.58% fraudulent transactions).</li>
<li>Most transactions (99%) originated from the United States.</li>
<li>Online transactions (cardholder not present) were most frequent (80%).</li>
<li>Transaction amount follows a Pareto distribution (many small transactions, few large ones).</li>
<li>Fraudulent transactions are more likely for higher amounts (except for very high amounts).</li>
<li>Reversal and multi-swipe transactions were identified and analyzed.</li>
<li>Certain account number prefixes correlated with higher fraud rates.</li>
<li>An upward trend in transaction volume with a constant fraud rate was observed over time.</li>
<li>Merchant names with unknown country codes or POS entry modes had higher fraud rates.</li>
<li>Transaction categories like online gifts and rideshare had higher fraud rates.</li>
<li>Incorrect CVV entries increased fraud likelihood, while incorrect expiry dates did not.</li>
</ul>

<h2>Feature Engineering</h2>
<ul>
<li>Hamming distance was used to measure CVV difference from the correct value.</li>
<li>Date features (year, month, etc.) were extracted from datetime columns.</li>
<li>Low-frequency merchant names were grouped into a single category.</li>
<li>Categorical data was encoded using one-hot encoding.</li>
</ul>

<h2>Modeling</h2>
<ul>
<li>F1 score, AUC-ROC, and precision-recall were used for evaluation (class imbalance).</li>
<li>The dataset was standardized before modeling.</li>
<li>Class weights were used to emphasize the minority fraud class.</li>
<li>XGBoost achieved the best performance ( AUC-ROC: 0.7626, Accuracy - 98%).</li>
</ul>

<h2>Things that didn't work</h2>
<ul>
  <li>To handle class imbalance, data balancing techniques such as SMOTE and majority class downsampling were attempted but didn't give expected results.</li>
  <li>To encode categorical variables, the label encoder technique was attempted but didn't work well as label encoding works well only for data when ordinality is present.</li>
  <li>Although various models including Logistic Regression, Random Forest, Decision Trees, and neural networks were used for model building, apart from XGBoost, the remaining models were not able to generate accurate predictions.</li>
</ul>

<h2>Further Roadmap</h2>
<ul>
  <li>A thorough analysis of incorrectly tagged predictions can help us identify patterns missing in our input variables.</li>
  <li>Generate a User-Merchant matrix and use dimensionality reduction techniques such as PCA to create merchant and user vectors.</li>
  <li>Detailed analysis of fraud transactions from a time series dimension to understand if there are any patterns and incorporate them as features in our model.</li>
  <li>An ensemble of multiple models with different sets of input features can help improve model performance.</li>
  <li>Refine the set of input features by analyzing top important features and remove features that aren't necessary.</li>
</ul>
