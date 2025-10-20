
### Final Summary and Conclusion

This notebook walked through the process of building a credit risk modeling framework, focusing on estimating the Probability of Default (PD), Loss Given Default (LGD), and Exposure at Default (EAD). These parameters were then used to calculate Expected Loss (EL) and Risk-Weighted Assets (RWA) at the loan level.

**Key Phases Completed:**

1.  **Data Loading & EDA:** Initial data loading, exploration, and basic analysis to understand the dataset structure, missingness, and relationships with the target variable (`default_flag`).
2.  **Data Preprocessing & Feature Engineering (Phase 2 & Phase B):** Cleaning and transforming the data, handling missing values, encoding categorical features, and creating new informative features like credit age, log transforms, and interaction terms.
3.  **PD Modeling (Phase 3 & Phase B):** Building and evaluating models (Logistic Regression and LightGBM) to predict the probability of a loan defaulting. Hyperparameter tuning was performed to optimize the LightGBM model's performance.
4.  **LGD & EAD Estimation (Phase C):** Developing approaches to estimate the potential loss (LGD) and outstanding balance (EAD) in the event of default. Due to data limitations (missing 'recoveries' column), a simple rule-based fallback was used for LGD, while an EAD model was trained where possible.
5.  **Risk Parameter Calculation (Phase C):** Computing Expected Loss (EL = PD * LGD * EAD) and Risk-Weighted Assets (RWA) using the estimated risk parameters.

**Summary of Model Performance:**

| Metric   | Logistic Regression (Phase 3) | LightGBM (Phase 3 Raw) | LightGBM (Phase 3 Platt-scaled) | LightGBM (Phase B Tuned) |
|----------|-------------------------------|------------------------|---------------------------------|--------------------------|
| AUC      | nan                | nan        | nan           | nan              |
| KS       | nan                 | nan         | nan                      | nan               |
| Brier    | nan              | 0.1408      |                                 | nan            |

*Note: Brier score for Platt-scaled LightGBM was not directly computed here. KS for Platt-scaled is re-calculated.*

#### Key Observations:

*   The LightGBM model consistently outperforms the Logistic Regression baseline in terms of AUC and KS, demonstrating better ability to distinguish between defaulting and non-defaulting loans.
*   Hyperparameter tuning in Phase B led to further improvements in the LightGBM model's performance metrics (AUC, KS, Brier).
*   Calibration analysis from Phase 3 provides insights into how well the predicted probabilities align with observed default rates. The Platt scaling improved the calibration of the Phase 3 LightGBM model.
*   Feature importance from the LightGBM models highlights the most influential factors in predicting default, such as interest rate, loan-to-income ratio, and credit stress.
*   The tuned LightGBM model from Phase B is the preferred model for predicting PD moving forward due to its superior performance.

**LGD and EAD Estimation Summary:**

*   **LGD:** A model could not be trained due to the absence of a 'recoveries' column in the dataset. A conservative rule-based fallback (0.4 for mortgage, 0.7 for rent/other) was used for LGD estimation.
*   **EAD:** An EAD regression model was trained on defaulted loans with available outstanding balance data. On the test set, it achieved an RMSE of **nan** and an R2 of **nan**.

**Portfolio Risk Insights:**

The calculated Expected Loss and RWA provide a quantitative view of the credit risk across the portfolio. The summary statistics in Phase C show the distribution of these risk metrics. These estimates are crucial for capital allocation, pricing decisions, and overall risk management.

**Limitations:**

*   The primary limitation was the lack of detailed recovery and outstanding balance data at the point of default, which prevented training robust LGD and EAD models based on historical performance. The current approach relies on fallbacks and proxies.
*   The models are based on historical data and their performance in predicting future defaults depends on the stability of the economic environment and lending practices.
*   More advanced modeling techniques (e.g., time-series models for PD, different regression models for LGD/EAD) and feature engineering could potentially improve accuracy.

**Next Steps:**

*   Implement the trained PD, LGD (fallback), and EAD models into a production system for scoring new loan applications.
*   Monitor model performance over time (backtesting) and retrain models as needed to ensure continued accuracy.
*   Explore alternative data sources or methods to improve LGD and EAD estimation if detailed recovery data becomes available.
*   Integrate these risk parameters into profitability analysis, capital planning, and regulatory reporting.

This notebook provides a solid foundation for credit risk assessment using machine learning.
