# Fraud Detection

# Business Objective 
Identify fraudulent transaction alerts from card transactions to reduce their fraud loss and increase their revenue; Improving fraud experience is essential to gain customer trust, integrity in financial systems and increase revenue


# Technical objective

Conduct initial data exploration, understand nuances of fraud data, perform feature engineering and prepare the data for modelling

# Data Sources

The data comes from Vesta's real-world e-commerce transactions and contains a wide range of features from device type to product features The data is broken into two files identity and transaction, which are joined by TransactionID. Not all transactions have corresponding identity information.

https://www.kaggle.com/competitions/ieee-fraud-detection/data

#Technicality

Pandas for data reading/wranging/cleanup
Seaborn for Visualization
SKLearn for Pipelines, Encoding, CV, Stratification, Grid search

Models evaluated

Decision Trees- For baseline
To expand to Ensemble models in the next steps

Credits
https://github.com/toby-gardner-ai/uc-berkeley-aiml-course/blob/main/notebooks/Mod4_Data_Analytics.ipynb
For Unbalanced classes, papers suggest usage of AUPRC(Area under Precision-Recall curve) over F1- Macro Citation: https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0118432

