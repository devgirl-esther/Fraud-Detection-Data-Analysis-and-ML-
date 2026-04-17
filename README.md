Fraud Detection Using Machine Learning (PaySim Dataset)

Overview
This project explores fraud detection in financial transactions using machine learning. The goal is to identify patterns that distinguish fraudulent transactions from legitimate ones and build predictive models that can support real-world fraud prevention systems.

Dataset
Synthetic financial transaction dataset (PaySim)
Highly imbalanced (fraud cases are rare)
Includes transaction types, balances, and transfer amounts

Project Workflow
1. Exploratory Data Analysis (EDA)
Analysed class imbalance
Investigated transaction types (TRANSFER, CASH_OUT)
Explored temporal fraud patterns
Identified anomalous behaviour in transaction balances

2. Feature Engineering
Key engineered features:
Balance Error → detects inconsistencies in transaction updates
Log Amount → handles skewed distributions
Amount-to-Balance Ratio → measures transaction aggressiveness
Zero Balance Error Flag → strong fraud indicator

3. Modelling
Models trained:

Logistic Regression (baseline)
Decision Tree
Random Forest

Evaluation metrics:

ROC-AUC
Precision
Recall
F1-score
4. Results
Model	ROC-AUC
Logistic Regression	0.9917
Decision Tree	0.9996
Random Forest	0.9988
5. Key Insights
Fraud transactions are highly concentrated in specific transaction types
Fraudulent behaviour shows near-perfect balance consistency
Engineered features significantly improved model performance
Threshold tuning improved fraud detection recall
6. Threshold Tuning

Instead of using the default 0.5 threshold:

Lower thresholds (0.2–0.3) improved fraud detection (recall)
Trade-off observed with increased false positives

Limitations
Extremely high performance suggests possible data leakage
Some features may not be available in real-time systems
Further validation required on real-world datasets

Future Work
Deploy model with real-time monitoring
Experiment with XGBoost / LightGBM
Implement precision-recall optimisation
Build dashboard for fraud alerts