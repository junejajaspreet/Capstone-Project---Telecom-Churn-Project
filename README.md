# Telecom Churn Prediction – High-Value Customers

## 📌 Business Objective
Predict churn for **high-value customers** in the telecom sector using customer-level data from 4 months, and identify key indicators of churn to help design targeted retention strategies.

---

## 📂 Dataset
- **Months covered:** June (6), July (7), August (8), September (9)  
- **High-value definition:** Top 30% customers by average recharge in first 2 months (≥ 70th percentile)  
- **Churn definition:** In September, no incoming calls, outgoing calls, or internet usage.  

---

## 🛠️ Approach
1. **Data Preparation**
   - Filtered high-value customers
   - Tagged churners
   - Removed churn phase attributes (`*_9`)
2. **EDA**
   - Usage patterns in churners vs. non-churners
   - Recharge and call volume trends
3. **Modeling**
   - Logistic Regression (with & without PCA)
   - SVM models  
   - Class imbalance handling
4. **Evaluation**
   - Compared Accuracy, Sensitivity, Specificity

---

## 📊 Key Results
- **Final Logistic Regression (No PCA):**
  - Train: Accuracy 0.84, Sensitivity 0.81, Specificity 0.83
  - Test: Accuracy 0.78, Sensitivity 0.82, Specificity 0.78

### Top Predictors
| Variable             | Coefficient | Impact |
|----------------------|-------------|--------|
| loc_ic_mou_8         | -3.33       | ↓ usage → ↑ churn risk |
| og_others_7          | -2.47       | ↓ usage → ↑ churn risk |
| ic_others_8          | -1.51       | ↓ usage → ↑ churn risk |
| roam_og_mou_8        | +0.71       | ↑ roaming calls → ↑ churn risk |

---

## 📌 Recommendations
1. Target customers with declining incoming/outgoing minutes in action phase.  
2. Provide offers to customers with increased value-based costs.  
3. Monitor and incentivise 2G/3G data users with declining monthly usage.  
4. Address roaming call dissatisfaction with special roaming packs.

---

## 🖼️ Sample Visuals
**Churn Rate Distribution**  
![Churn Rate](images/churn_rate.png)  

**Top Feature Importance**  
![Feature Importance](images/feature_importance.png)  

---

## 🛠 Tools & Libraries
- Python (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn)
- Jupyter Notebook

---

## ▶️ How to Run
1. Clone repository  
2. Install dependencies from `requirements.txt`  
3. Run Jupyter Notebook:  
   ```bash
   jupyter notebook "Capstone Project - Telecom Churn Project.ipynb"
