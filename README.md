This README provides a comprehensive summary of the fraud detection project

# Fraud Detection System 

# Model Analysis & Performance Report 

# 1. Problem Statement

The goal of this project is to develop a robust machine learning system capable of identifying fraudulent financial transactions in real-time.Challenges: The primary obstacle is the extreme class imbalance, where fraudulent activity represents only ~3.6% of the total data. Furthermore, the "missingness" of data in specific fields (e.g., V_Group features) is not random but serves as a high-gain indicator of fraudulent behavior.

**Potential Benefits **

Success in this domain reduces direct financial loss from unauthorized charges, minimizes the operational cost of manual reviews, and maintains customer trust by reducing false positives for legitimate users. Models such as these are essential to maintain integrity of financial systems

# 2. Model Outcomes & Predictions

Learning Type: This is a Supervised Binary Classification task.
Expected Output: The model outputs a continuous probability score between 0 and 1 for each transaction.
Methodology: The project utilized supervised learning algorithms, as historical labels (Fraud vs. Legit) were available to train the models.

# 3. Data Acquisition

The dataset consists of large-scale transactional records including:
Numerical Features: Transaction amounts and time-based deltas.
Categorical Features: Card types, device information, and geographic identifiers.
Engineered Features: A large set of PCA-transformed variables representing complex interactions.

Original data source: The data comes from Vesta's real-world e-commerce transactions and contains a wide range of features from device type to product features The data is broken into two files identity and transaction, which are joined by TransactionID. Not all transactions have corresponding identity information. https://www.kaggle.com/competitions/ieee-fraud-detection/data

**Analysis** 
Feature importance via XGBoost Gain and SHAP values confirmed that V_Group_11_PC2 and TransactionAmt are the strongest predictors of fraud.


# 4. Data Preprocessing & Preparation

Missing Values: We utilized a SimpleImputer with a Missing Indicator strategy. This was critical because the absence of data was found to be a predictive feature in itself.
Encoding & Scaling: Categorical: Handled via OneHotEncoder with handle_unknown='ignore'.
Numerical: Scaled using StandardScaler to ensure convergence, particularly for the Neural Network.
Data Splitting: The data was split into training and test sets using a stratified approach to preserve the 3.6% fraud ratio across both sets, ensuring evaluation remains realistic.

# 5. Modeling

Four distinct architectures were selected and tuned:
Random Forest: Served as the ensemble baseline.
LightGBM: Used for its efficiency with large-scale tabular data.
XGBoost: Selected for its advanced regularization and ability to handle the "missing as a signal" logic natively.
Feed-forward Neural Network (FNN): A deep learning approach (256-128-64 architecture) designed to capture non-linear manifolds.

# 6. Model Evaluation

Metrics: Because of the class imbalance, Mean Average Precision (AP) and Precision-Recall AUC were the primary metrics. 
Traditional accuracy was discarded as it would be 96.4 even if the model predicted "Legit" for every case.

**Optimal Model: XGBoost** is the optimal model for this problem, achieving a Mean AP of 0.8201.Findings: 
The Neural Network significantly underperformed (AP: 0.4833) compared to tree-based models. This suggests that for this specific tabular dataset, the decision-tree logic of "splitting" on missing values is more effective than the "continuous" weight adjustments of a neural network.

**Notebook Location**: https://github.com/vimalkurup/fraud_detection/blob/master/Fraud_Detection.ipynb

**Credits**
https://github.com/toby-gardner-ai/uc-berkeley-aiml-course/blob/main/notebooks/Mod4_Data_Analytics.ipynb
For Unbalanced classes, papers suggest usage of AUPRC(Area under Precision-Recall curve) over F1- Macro Citation: https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0118432

