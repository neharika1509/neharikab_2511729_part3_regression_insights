# Model Comparison


## Overview

Three regression models were built and compared to identify the best approach for explaining monthly sales performance across stores.


## Model Summary Table

| Item | Simple Model 1 | Simple Model 2 | Multiple Regression |

| **Model Name** | Sales ~ Footfall | Sales ~ Marketing Spend | Full Multiple Regression |
| **Dependent Variable** | monthly_sales | monthly_sales | monthly_sales |
| **Independent Variables** | footfall | marketing_spend | footfall, marketing_spend, avg_discount_pct, staff_count, inventory_availability_pct, customer_rating, store_type dummies, region dummies |
| **R-squared** | 0.7363 (73.6%) | 0.1672 (16.7%) | **0.8353 (83.5%)** |
| **Significant Variables** | footfall *** | marketing_spend *** | footfall ***, marketing_spend ***, staff_count *, inventory_availability_pct ***, customer_rating **, store_type (Airport, Mall, High Street), reg_South, reg_West |
| **Business Usefulness** | Good starting point; footfall is clearly the dominant driver | Weak standalone predictor; marketing matters more in context | Best model — covers all major business levers and structural effects |
| **Limitations** | Ignores every other driver; cannot inform operational decisions | Very low explanatory power; misleading as a standalone tool | Cannot prove causation; 16.5% variance unexplained; may not generalise to new regions or store formats |



## R-squared Comparison

```
Simple Model 1  (footfall)          73.6%
Simple Model 2  (marketing_spend)   16.7%
Multiple Model  (all predictors)    83.5%
```

The multiple regression model explains nearly **10 percentage points more** of sales variance than the best simple model, even though it already had a strong R².



## Significant Variables in Final Model

| Variable | Coefficient | P-value | Significance |
|---|---|---|---|
| footfall | +28.53 per visitor | < 0.001 | *** Very High |
| marketing_spend | +1.18 per £1 | < 0.001 | *** Very High |
| inventory_availability_pct | +3,048 per 1% | < 0.001 | *** Very High |
| type_Airport | +42,282 vs Residential | < 0.001 | *** Very High |
| type_Mall | +29,872 vs Residential | < 0.001 | *** Very High |
| customer_rating | +14,214 per star | 0.003 | ** High |
| type_High Street | +19,057 vs Residential | 0.002 | ** High |
| reg_South | +19,280 vs East | 0.007 | ** High |
| reg_West | +18,017 vs East | 0.004 | ** High |
| staff_count | +3,041 per staff member | 0.015 | * Moderate |

**Not significant:** avg_discount_pct (p=0.174), reg_North (p=0.451)


## Business Usefulness

### Simple Model 1 (Sales ~ Footfall)
- **Useful for:** Understanding that foot traffic is the core engine of sales
- **Limitation:** Cannot answer *how to improve* footfall or what else matters
- **Decision support:** Weak — only one lever visible

### Simple Model 2 (Sales ~ Marketing Spend)
- **Useful for:** A rough check that marketing investment is positively associated with sales
- **Limitation:** Only 17% explanatory power; footfall, inventory, store type all swamp the marketing signal alone
- **Decision support:** Very limited

### Multiple Regression (Final Model)
- **Useful for:** Simultaneously evaluating all key business levers — footfall, marketing, inventory, staffing, customer experience, store type, and region
- **Decision support:** Strong — leadership can model the estimated impact of changing any single factor while holding others constant
- **Example question answerable:** "If we improve inventory availability from 80% to 90% in our Residential stores, what is the estimated monthly sales uplift?" → Approximately £30,480 per store



## Limitations of All Models

1. **Correlation ≠ Causation:** Regression identifies statistical associations, not causal relationships. For example, high footfall may be caused by external factors (e.g., shopping centre location) rather than actions the business can directly control.

2. **Omitted variables:** The 16.5% unexplained variance in the multiple regression likely reflects factors not in the dataset — local competition activity, weather, seasonal events, store condition, and management quality.

3. **Aggregation:** Data is at the store-month level. Individual transaction-level patterns or intra-month variation are not captured.

4. **Short time horizon:** Only 4 months of data (Jan–Apr 2025) — seasonal effects and longer-term trends cannot be reliably assessed.

5. **No interaction effects:** The model assumes each variable acts independently. In reality, marketing spend may be more effective in high-footfall locations — an interaction the current model does not test.



## Recommended Model

** Multiple Regression (R² = 0.8353)**

This model provides the most complete, statistically rigorous, and business-actionable view of what drives monthly sales across this retail chain.
