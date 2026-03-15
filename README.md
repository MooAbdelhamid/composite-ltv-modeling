# 12-Month Customer LTV Prediction

End-to-end machine learning pipeline predicting 12-month revenue at signup
for a subscription-based insurance product (~91k customers).

## The problem
Standard regression fails on insurance LTV because revenue is driven by two
separate events: whether a customer stays, and whether they buy additional
policies. A single model can't capture both cleanly.

## Solution: 3-stage composite model
Rather than predicting LTV directly, the pipeline decomposes it:

1. **Tenure classifier** — probability the customer stays 12 months
2. **Cross-sell classifier** — probability they purchase an additional policy
3. **Cross-sell valuator** — expected value of that policy if purchased

**Formula:** `LTV = (Monthly Commission × Predicted Tenure) + (P_crosssell × Value_crosssell)`

## Results
| Model | MAE | RMSE |
|---|---|---|
| Baseline (mean prediction) | 42.0 | — |
| Linear Regression | ~40 | — |
| Composite XGBoost | **35.49** | 103.50 |

16% reduction in MAE over baseline.

## Key business insights
- Customers starting with **Product C** show the highest cross-sell propensity
- Users on non-standard OS show significantly higher churn — likely UX friction
- Retention drives more total portfolio value than upsell events

## Tech stack
Python · Pandas · scikit-learn · XGBoost · Jupyter

## How to run
```bash
pip install -r requirements.txt
jupyter notebook LTV_Model.ipynb
```

## Project structure
```
composite-ltv-modeling/
├── LTV_Model.ipynb      # Main modeling notebook
├── requirements.txt
└── README.md
```
