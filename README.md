# 12-Month Customer LTV Prediction: InsurTech Case Study

## Project Overview
This project aims to predict the 12-Month Loan-to-Value (LTV) for new insurance customers data available at the moment of signup. 

The primary challenge was the non-linear nature of customer tenure and the sparse, high-value nature of cross-sell events. I developed a 3-Stage Composite Model that outperforms standard regression by separating churn risk from expansion potential.

## Key Results
* **Mean Absolute Error (MAE):** 35.49
* **Root Mean Squared Error (RMSE):** 103.50
* **Approach:** Transitioned from simple Regression to an XGBoost Classifier Model to better handle the skewed 12-month tenure data.



## The Composite Model Architecture
Rather than predicting a single LTV figure, the model decomposes "Yearly Income" into its core components:
1.  **Tenure Classifier:** Predicts the probability of a user staying 12 months and number of tenure months.
2.  **Cross-Sell:** A binary classifier to predict the probability of an additional policy purchase.
3.  **Cross-Sell Valuator:** A regressor to estimate the value of that cross-sell if it occurs.

**Final Formula:** $LTV_{12m} = (Monthly\ Commission \times \text{Pred\_Tenure}) + (\hat{P}_{xs} \times \hat{V}_{xs})$

## Top Business Insights
* **The "Product C" Gateway:** Customers starting with Product C show the highest propensity for cross-selling and long-term retention.
* **Platform Friction:** Users on "Other" Operating Systems showed a significantly higher churn rate compared to iOS/Android, suggesting technical or UX barriers.
* **Retention > Upsell:** While cross-sells are high-value, 12-month retention of the core subscription remains the primary driver of total portfolio value.



## 🚀 How to Use
1. **Clone the repo:** `git clone https://github.com/your-username/repo-name.git`
2. **Install dependencies:** `pip install -r requirements.txt`
3. **Run the analysis:** Open `Getsafe_LTV_Analysis.ipynb`
