End-to-End Fraud Detection System for Imbalanced Financial Transactions (PaySim)
📌 Overview

This project develops an end-to-end fraud detection pipeline using the PaySim synthetic financial dataset. The primary objective is to identify fraudulent transactions while addressing the challenges of extreme class imbalance.

The solution focuses on maximising fraud detection (recall) while managing false positives — a critical trade-off in real-world financial systems. The project demonstrates not only model development but also practical decision-making, feature engineering, and deployment considerations.

📊 Dataset
Source: PaySim (synthetic financial transactions dataset)
Nature: Highly imbalanced (fraud cases are rare)
Features include:
Transaction type (TRANSFER, CASH_OUT, etc.)
Transaction amount
Account balances before and after transactions
🔍 Project Workflow
1. Exploratory Data Analysis (EDA)
Analysed class imbalance between fraudulent and non-fraudulent transactions
Identified fraud concentration in specific transaction types (TRANSFER, CASH_OUT)
Explored temporal patterns in fraudulent behaviour
Detected anomalies in account balance updates
2. Feature Engineering

To improve model performance and capture fraud patterns, the following features were engineered:

Balance Error → Detects inconsistencies in balance updates
Log Amount → Reduces skewness in transaction amounts
Amount-to-Balance Ratio → Measures transaction aggressiveness
Zero Balance Error Flag → Strong indicator of fraudulent behaviour

These features significantly improved class separability and model performance.

3. Modelling

The following models were trained and evaluated:

Logistic Regression (baseline, interpretable)
Decision Tree
Random Forest

Evaluation Metrics:

ROC-AUC
Precision
Recall
F1-score

| Model               | ROC-AUC | Recall (Fraud) | Precision | Notes                          |
| ------------------- | ------: | -------------: | --------: | ------------------------------ |
| Logistic Regression |  0.9917 |           High |  Moderate | Strong baseline, interpretable |
| Decision Tree       |  0.9996 |      Very High |     Lower | Risk of overfitting            |
| Random Forest       |  0.9988 |           High |  Balanced | Best trade-off                 |


👉 Final Model Selected: Random Forest
Chosen for its ability to balance fraud detection (recall) with precision, reducing missed fraud while controlling false positives.

⚖️ Threshold Optimisation

In fraud detection, missing fraudulent transactions is more costly than false positives. Therefore, threshold tuning was applied:

Default threshold (0.5):
Balanced performance but misses some fraud cases
Tuned threshold (0.2–0.3):
Increased recall (captures more fraudulent transactions)
Increased false positives (acceptable in fraud systems)



💡 Key Insights
Fraud is highly concentrated in specific transaction types (TRANSFER, CASH_OUT)
Fraudulent transactions exhibit near-consistent balance manipulation patterns
Feature engineering significantly improves fraud detection performance
Threshold tuning is critical for aligning models with business objectives
⚠️ Limitations & Risks
Extremely high model performance suggests potential data leakage, particularly from balance-related features
Some engineered features may not be available in real-time systems
Synthetic dataset may not fully represent real-world fraud behaviour
✅ Mitigation Strategies
Remove or validate leakage-prone features
Use time-based validation to simulate real-world deployment
Test models on real-world datasets
🏗️ Production Considerations
Real-time feature availability constraints
Low-latency requirements for transaction scoring
Monitoring for data drift and fraud pattern changes
Managing alert fatigue due to false positives
Integration with fraud investigation systems
🚀 Future Improvements
Implement advanced models (XGBoost, LightGBM)
Optimise precision-recall trade-offs further
Deploy as a real-time fraud detection API
Build an interactive dashboard for fraud monitoring
🛠️ Tech Stack
Python
Pandas, NumPy
Scikit-learn
Matplotlib, Seaborn
