# neharikab_2511729_part3_regression_insights


## 1. Business Problem Summary

The leadership team of a retail chain wants to understand what factors are driving monthly sales performance across their stores. They are evaluating business actions including:

- Increasing marketing spend
- Improving inventory availability
- Changing discounting strategy
- Reallocating staff
- Prioritising certain store types or regions

The objective of this analysis is to use regression analysis to identify which factors are most strongly associated with monthly sales, quantify their estimated impact, and provide a data-driven business recommendation.


## 2. Dataset Description

the file data/business_regression_data.xlsx consiste of:
- 320 observations (rows)
- 14 variables (columns)
- giving us information about 80 stores over the span of 4 months (Jan–Apr 2025)
- there are 14 total missing values (6 in "competitor_distance_km", 8 in "customer_rating") — imputed with median 

### Description of All Variables

| Variable | Type | Description |
| `store_id` | Identifier | Unique store code (STR-1001 to STR-1080) |
| `month` | Date | Month of observation (Jan–Apr 2025) |
| `region` | Categorical | Geographic region: East, North, South, West |
| `store_type` | Categorical | Store format: Residential, High Street, Airport, Mall |
| `monthly_sales` | Numerical | Total monthly revenue (£) — **dependent variable** |
| `monthly_profit` | Numerical | Monthly profit (£) — excluded (downstream outcome) |
| `footfall` | Numerical | Number of customers entering store per month |
| `marketing_spend` | Numerical | Monthly marketing budget (£) |
| `avg_discount_pct` | Numerical | Average discount applied (decimal, e.g. 0.12 = 12%) |
| `staff_count` | Numerical | Number of staff in store |
| `inventory_availability_pct` | Numerical | % of products in stock when needed |
| `competitor_distance_km` | Numerical | Distance to nearest competitor (km) |
| `customer_rating` | Numerical | Average customer satisfaction rating (1–5 stars) |
| `holiday_flag` | Binary | 1 = holiday month, 0 = standard month |


## 3. Dependent and Independent Variables

### Dependent Variable (What we are predicting)

 "monthly_sales" is a dependent variable of continuous numerical type - The core business outcome leadership wants to understand and improve 

### Independent Variables (Predictors used in final model)

| Variable | Type | Role in Model |

| footfall | Numerical | Strongest predictor of sales; captures customer demand |
| marketing_spend | Numerical | Controllable business lever; drives customer acquisition |
| avg_discount_pct | Numerical | Pricing strategy lever; tested but not significant |
| staff_count | Numerical | Operational capacity indicator |
| inventory_availability_pct | Numerical | Operational quality measure; impacts conversion |
| customer_rating | Numerical | Experience quality signal; drives repeat visits |
| store_type | Categorical → Dummy | Structural format effect (Airport, Mall, High Street vs Residential) |
| region | Categorical → Dummy | Geographic effect (North, South, West vs East) |

### Variables Excluded from Regression

| Variable | Reason |

| store_id | Unique identifier — no predictive value |
| month | Only 4 time points — insufficient to model time trends |
| monthly_profit | Downstream outcome of sales — using it would cause circular logic |
| holiday_flag | Not statistically significant; excluded from final model |
| competitor_distance_km | Weak predictor in preliminary testing; not included in final model |



## 4. Regression Approach

Three models were built using Ordinary Least Squares regression:

### Model 1 – Simple Regression: Sales ~ Footfall
- One predictor only
- Used to establish the baseline relationship between foot traffic and sales
- Equation: monthly_sales = 446,411 + 35.678 × footfall

### Model 2 – Simple Regression: Sales ~ Marketing Spend
- One predictor only
- Used to evaluate marketing ROI in isolation
- Equation: monthly_sales = 560,777 + 2.130 × marketing_spend

### Model 3 – Multiple Regression: Sales ~ All Key Predictors
- Combines all significant numerical and categorical (dummy) predictors
- Allows leadership to assess the impact of each lever while holding others constant
- Full equation documented in outputs/model_equations.md

All models use monthly_sales as the dependent variable. Categorical variables were converted to dummy variables before inclusion. Missing values were imputed using the median prior to modelling.


## 5. Dummy Variable Approach

A categorical variable were converted to binary dummy variables for use in regression:

### region (4 categories → 3 dummies)

| Region | reg_North | reg_South | reg_West |
|---|---|---|---|
| East | 0 | 0 | 0 |
| North | 1 | 0 | 0 |
| South | 0 | 1 | 0 |
| West | 0 | 0 | 1 |

**Reference category: East** — provides a stable geographic baseline.

> One category is always dropped per variable to avoid the **dummy variable trap** (perfect multicollinearity). The dropped category becomes the reference group, and its effect is captured in the model intercept.

Full dummy variable explanation is in outputs/model_equations.md.

---

## 6. Model Comparison Summary

| Model | Predictors | R-squared | Significant Variables | Suitable For |
|---|---|---|---|---|
| Simple Model 1 (footfall) | 1 | **0.7363** (73.6%) | footfall *** | Understanding primary driver only |
| Simple Model 2 (marketing) | 1 | **0.1672** (16.7%) | marketing_spend *** | Marketing ROI check only |
| Multiple Regression | 12 | **0.8353** (83.5%) | 10 variables significant | Full business decision support |

The multiple regression model explains **83.5% of the variation** in monthly sales — a strong result for real-world business data. It outperforms both simple models substantially and captures all key business levers simultaneously.

Full comparison is in `analysis/model_comparison.md` and `outputs/regression_summary.xlsx`.

---

## 7. Final Model Selected

**→ Multiple Regression (R² = 0.8353)**

This model was selected because:
- It explains **83.5% of monthly sales variance** — the highest of all models tested
- It incorporates **all major business levers** leadership is considering: marketing, inventory, staffing, discounting, store type, and region
- **10 out of 12 predictors** are statistically significant at the 5% level or better
- It enables **scenario modelling** — e.g., estimating the impact of improving inventory availability from 85% to 92%
- The residual analysis confirms the model fits the data well with no systematic bias

The full model equation, coefficient interpretations, and selection rationale are documented in `outputs/model_equations.md`.

---

## 8. Business Recommendation

Based on the multiple regression model, the leadership team should prioritise the following actions:

**1. Drive footfall** — It is the single strongest predictor of sales. Every 1,000 additional monthly visitors is associated with ~£28,500 more in revenue. Investments in store accessibility, local marketing, and customer attraction initiatives are likely to yield the highest return.

**2. Improve inventory availability** — Each 1 percentage point improvement in stock availability is associated with £3,048 more in monthly sales. Raising average availability from 87% to 92% across all 80 stores could be associated with over **£1.2M in additional monthly chain revenue**.

**3. Invest in customer experience** — Each 1-star improvement in customer rating is associated with £14,214 more in monthly sales. Stores below 3.5 stars should be prioritised for service improvement programmes.

**4. Prioritise Airport and Mall locations** — Airport stores generate £42,282 more per month than Residential stores (all else equal); Mall stores generate £29,872 more. Capital investment should favour these formats.

**5. Maintain marketing spend** — Marketing returns approximately £1.18 in sales per £1 spent; it is a positive ROI lever but should be allocated to the highest-performing store types and regions.

**6. Do not over-invest in discounting** — The `avg_discount_pct` variable was not statistically significant (p = 0.174). There is insufficient evidence that discounting reliably boosts sales in this dataset.

Full business recommendation is in `outputs/final_recommendation.md`.

---

## 9. Assumptions and Limitations

### Regression Assumptions
- **Linearity:** The model assumes a linear relationship between each predictor and monthly sales. Non-linear relationships may exist but were not tested.
- **Independence:** Observations are assumed to be independent. In practice, the same store appears across 4 months — this introduces mild autocorrelation that is not corrected for in this analysis.
- **Homoscedasticity:** The model assumes constant variance of residuals. Some heteroscedasticity may exist across store types.
- **No multicollinearity:** Predictors are assumed to be sufficiently independent. Footfall and marketing spend may have some correlation (higher-budget stores may be in higher-traffic areas) but variance inflation was not formally tested.

### Limitations
| Limitation | Impact |
|---|---|
| Correlation ≠ causation | Regression shows association, not proof of cause and effect |
| Short time window (4 months) | Cannot assess seasonality, year-on-year trends, or long-term effects |
| 14 missing values imputed | Results may shift slightly with complete data |
| 16.5% unexplained variance | Unmeasured factors (local economy, competition quality, store condition, management) affect sales |
| No interaction effects | Marketing may be more effective in high-footfall stores — this is not modelled |
| Average chain-wide effects | Coefficients represent averages; individual store responses may differ significantly |



## 10. Screenshots Included

screenshots/simple_regression_output.png contains Scatter plots and statistics tables for Simple Models 1 and 2 
screenshots/multiple_regression_output.png contains Coefficient bar chart and full coefficient table for the multiple regression model 
screenshots/residuals_preview.png contains Residuals vs Fitted plot, residual distribution histogram, and annotated outlier chart 
screenshots/model_comparison_preview.png contains R² bar chart and model comparison summary table across all three models 


