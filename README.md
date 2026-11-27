# Discovering Customer Lifecycle States and Behavioral Drift for Early Churn Detection

Break Through Tech AI Studio, Fall 2026 · Amazon 1A

---

### 👥 **Team Members**

| Name              | GitHub Handle          | Contribution                                                                                  |
|-------------------|------------------------|-----------------------------------------------------------------------------------------------|
| Noemie Florant    | @emielol               | Data loading, feature engineering, logistic regression, model evaluation, lifecycle clustering |
| Siya Timsina      | @athensara             | Missing values, feature engineering, code cleanup, model evaluation, risk summaries           |
| Sanchita Modi     | @sanchitamodi          | Missing values, feature table, logistic regression, random forest, lifecycle clustering, SHAP |
| Juan Apolo        | @Vn0m                  | 90-day churn label, behavioral drift features, model comparison, README                       |
| Emily Yang        | @emilyyng              | EDA, random forest, XGBoost, SHAP explainability, risk summaries                              |
| Anindita Bhowmik  | @anindita-bhowmik28    | 90-day churn label, EDA, behavioral drift features, model comparison, risk summaries          |
| Meher Khatoon     | @meherkhatoon28-debug  | Feature table, random forest, XGBoost, SHAP explainability                                    |

---

## 🎯 **Project Highlights**

- Built a pipeline that turns raw e-commerce transactions into a customer-month feature table with a 90-day forward-looking churn label.
- Trained Logistic Regression, Random Forest, and XGBoost churn models. XGBoost scored best, with a ROC-AUC of 0.85 and a PR-AUC of 0.55.
- Lowered the decision threshold to raise recall (the share of churners caught) from about 28–43% to about 76–80%.
- Added behavioral drift features that compare each customer's current month with their own recent past.
- Grouped customers into four lifecycle states with K-Means: Active, Occasional, Declining, and At-risk.
- Used SHAP to explain which features drive each customer's churn risk.

---

## 👩🏽‍💻 **Setup and Installation**

The notebooks are written for Google Colab with Google Drive.

1. Clone the repository:
   ```
   git clone https://github.com/Break-Through-Tech/Amazon-1A-discovering-customer-lifecycle-states-and-behavioral-drift-for-early-churn-detection.git
   ```
2. Download the [Online Retail II dataset](https://archive.ics.uci.edu/dataset/502/online+retail+ii) (`online_retail_II.xlsx`) and put it in a Google Drive folder named `BTT_Amazon1A_Studio`.
3. Open `notebooks/EDA.ipynb` in Colab and run all cells. It cleans the data, builds the features, and creates `feat.csv`. Save `feat.csv` into the same Drive folder.
4. Run the modeling notebooks, which all read `feat.csv`:
   - `baseline_modeling.ipynb`: Logistic Regression
   - `random_forest.ipynb`: Random Forest
   - `xgboost_modeling.ipynb`: XGBoost
   - `behavioral_drift.ipynb`: drift scoring
   - `lifecycle_states_clustering.ipynb`: lifecycle states
   - `shap_explainability.ipynb`: SHAP explanations

Main libraries: pandas, numpy, scikit-learn, xgboost, shap, matplotlib, seaborn. Colab includes all of them except `shap`, which installs with `pip install shap`.

---

## 🏗️ **Project Overview**

This project was completed as part of the Break Through Tech AI Program's AI Studio, with Amazon as the host company.

Most churn models only answer *"will this customer leave?"*, and usually too late to act. Our goal was to detect churn **early** by looking at how a customer's behavior changes over time:

- **Lifecycle states:** which stage a customer is in, such as active, occasional, declining, or at-risk.
- **Behavioral drift:** whether the customer is buying less often, spending less, or going longer between orders than they usually do.
- **Explanations:** why a customer is flagged, so a retention team knows what to act on.

Catching customers earlier gives businesses more time to keep them with targeted offers or outreach.

---

## 📊 **Data Exploration**

**Dataset:** [Online Retail II](https://archive.ics.uci.edu/dataset/502/online+retail+ii) (UCI). It contains about 1 million transactions from a UK online retailer between December 2009 and December 2011, split across two Excel sheets.

**Preprocessing:**
- Combined both Excel sheets into one table.
- Dropped rows with no Customer ID and filled missing product descriptions with "Unknown".
- Netted canceled invoices against purchases instead of deleting them, and kept a cancellation count as a feature.
- Converted timestamps and grouped transactions into one row per customer per month.

**Churn definition:** a customer churns at a given month if they make **no purchase in the next 90 days**. Months without a full 90-day window at the end of the data were dropped. All features use only information available up to that month, so the models don't see the future.

**Features:**
- **Monthly activity:** orders, revenue, quantity, unique items, cancellations.
- **Customer history:** tenure, recency (days since last order), total orders, order frequency, orders in the last 30/60/90 days.
- **Behavioral drift:** change in orders, revenue, unique items, and average order value compared with the customer's previous 3 months, plus the change in days since last purchase.

**EDA insights:**
- About 22% of customer-months are churn months, so the classes are imbalanced. That makes accuracy misleading, so we focused on recall, F1, and PR-AUC.
- Months with a cancellation had about the same churn rate as other months, so cancellations alone are a weak churn signal.

---

## 🧠 **Model Development**

- **Models:** Logistic Regression (baseline), Random Forest, and XGBoost.
- **Training setup:** 80/20 train/test split. Hyperparameters were tuned with 5-fold cross-validated grid search, optimizing F1.
- **Threshold tuning:** the default 0.5 cutoff missed most churners, so we chose a lower threshold from the precision-recall curve to catch more of them.
- **Lifecycle states:** K-Means with 4 clusters on log-transformed, standardized frequency, tenure, total orders, and cancellation rate.
- **Explainability:** SHAP TreeExplainer on the XGBoost model, with bar, beeswarm, and per-customer waterfall plots.

---

## 📈 **Results & Key Findings**

**Model performance** (test set, default 0.5 threshold):

| Model                  | Precision | Recall | F1    | ROC-AUC | PR-AUC |
|------------------------|-----------|--------|-------|---------|--------|
| Logistic Regression    | 0.515     | 0.275  | 0.359 | 0.816   | 0.495  |
| Random Forest (tuned)  | 0.554     | 0.392  | 0.459 | 0.814   | 0.530  |
| XGBoost                | 0.579     | 0.429  | 0.493 | 0.845   | 0.554  |

**With a lower threshold:**
- **Logistic Regression** (threshold 0.25): recall 0.80, precision 0.46, F1 0.59.
- **Random Forest** (threshold 0.28): recall 0.77, precision 0.47, F1 0.58.
- **XGBoost** (threshold 0.29): recall 0.76, precision 0.48, F1 0.59.

**Key findings:**
- Tree models beat the logistic regression baseline. XGBoost was strongest, and tuning it did not improve on the default settings.
- Lowering the threshold roughly doubled the number of churners caught, at a small cost in precision. For churn, missing a customer usually costs more than a false alarm.
- Tenure, monthly revenue, item variety, and quantity were the most important Random Forest features.
- **Lifecycle states:**

  | State      | Median orders | Median tenure (days) | Churn rate |
  |------------|---------------|----------------------|------------|
  | Active     | 22            | 322                  | ~3%        |
  | Occasional | 6             | 203                  | ~13%       |
  | Declining  | 3             | 98                   | ~29%       |
  | At-risk    | 1             | 25                   | ~37%       |

  The states line up with risk: churn rises steadily from Active to At-risk (overall rate is about 22%).

---

## 🚀 **Next Steps**

- Add the behavioral drift features and lifecycle states as model inputs and compare against the baselines.
- Use a time-based train/test split instead of a random one, to better mimic predicting the future.
- Measure the early-warning horizon: how many days before churn a customer gets flagged.
- Finish the template-based customer risk summaries and the end-to-end demo.
- Try the approach on a second dataset such as RetailRocket.

---

## 📝 **License**

This project is licensed under the MIT License.

---

## 📄 **References**

- Chen, D. (2019). [Online Retail II](https://archive.ics.uci.edu/dataset/502/online+retail+ii). UCI Machine Learning Repository.
- Lundberg, S. M., & Lee, S.-I. (2017). A Unified Approach to Interpreting Model Predictions (SHAP). *NeurIPS*.

---

## 🙏 **Acknowledgements**

Thank you to our Challenge Advisor, **Aryyama Kumar Jana**, our AI Studio Coach, **Ayush Amberkar**, and the Break Through Tech team for their guidance and support.
