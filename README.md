# Fraud Detection System (PaySim)

##  Overview
Built an end-to-end fraud detection pipeline on a highly imbalanced financial dataset (PaySim), focusing on **maximising fraud detection (recall)** while managing false positives — a key real-world trade-off.

---

## Dataset
- Synthetic financial transactions (PaySim)  
- Highly imbalanced (fraud is rare)  
- Includes transaction type, amount, and account balances  

---

## Approach

### EDA
- Identified strong class imbalance  
- Fraud concentrated in **TRANSFER** and **CASH_OUT**  
- Detected anomalies in balance updates  

### Feature Engineering
- **Balance Error** → detects inconsistencies  
- **Log Amount** → handles skew  
- **Amount Ratio** → transaction aggressiveness  
- **Zero Balance Flag** → strong fraud signal  

---

##  Models & Results

| Model                | ROC-AUC | Notes             |
|---------------------|--------:|------------------|
| Logistic Regression | 0.9917  | Baseline         |
| Decision Tree       | 0.9996  | Overfitting risk |
| Random Forest       | 0.9988  | Best trade-off   |

👉 **Final Model:** Random Forest  

---

## Threshold Tuning
- Default (0.5): misses fraud  
- Tuned (0.2–0.3):  
  - ↑ Recall (captures more fraud)  
  - ↑ False positives (acceptable trade-off)  

---

##  Key Insights
- Fraud concentrated in specific transaction types  
- Engineered features significantly improved performance  
- Threshold tuning is critical in fraud systems  

---

##  Limitations
- Possible **data leakage** from balance-based features  
- Some features may not be available in real-time  
- Synthetic data ≠ full real-world complexity  

---

##  Production Thinking
- Real-time scoring constraints  
- Data drift monitoring  
- False positive management (alert fatigue)  

---

##  Next Steps
- Try XGBoost / LightGBM  
- Deploy as API  
- Build fraud monitoring dashboard  

---

## 🛠️ Tech Stack
Python • Pandas • Scikit-learn • Matplotlib • Seaborn  

---

## 💡 Key Takeaway
Designed with **real-world fraud detection trade-offs in mind**, balancing model performance with practical deployment constraints.
