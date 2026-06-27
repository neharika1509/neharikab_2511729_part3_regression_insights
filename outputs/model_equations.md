# Model Equations & Dummy Variable Explanation



## 1. Simple Regression Equations

### Simple Model 1: Sales ~ Footfall

```
monthly_sales = 446,411 + 35.678 × footfall
```

| Term | Value | Meaning |
|---|---|---|
| Intercept (β₀) | 446,411 | Baseline predicted sales when footfall = 0 |
| Coefficient (β₁) | 35.678 | Each additional visitor adds £35.68 in monthly sales |
| R² | 0.7363 | Footfall alone explains **73.6%** of sales variance |
| P-value | < 0.001 | Highly statistically significant |

**Business reading:** Footfall is the single strongest predictor of sales. For every 1,000 additional customers entering a store, monthly sales increase by approximately £35,678. This suggests that efforts to drive in-store traffic (events, location, advertising) are strongly linked to revenue.



### Simple Model 2: Sales ~ Marketing Spend

```
monthly_sales = 560,777 + 2.130 × marketing_spend
```

| Term | Value | Meaning |

| Intercept (β₀) | 560,777 | Baseline predicted sales when marketing spend = 0 |
| Coefficient (β₁) | 2.130 | Each additional £1 in marketing spend adds £2.13 in sales |
| R² | 0.1672 | Marketing spend alone explains **16.7%** of sales variance |
| P-value | < 0.001 | Statistically significant but weaker predictor |

**Business reading:** Marketing spend returns approximately £2.13 in sales per £1 spent when considered in isolation. However, the low R² shows that marketing spend alone is not a reliable predictor — its impact likely works *through* footfall and should be evaluated in combination with other factors.



## 2. Multiple Regression Equation

```
monthly_sales =   30,213
              +   28.53  × footfall
              +    1.18  × marketing_spend
              +  (−49,245) × avg_discount_pct
              +   3,041  × staff_count
              +   3,048  × inventory_availability_pct
              +  14,214  × customer_rating
              +  42,282  × type_Airport
              +  19,057  × type_High_Street
              +  29,872  × type_Mall
              +   5,270  × reg_North
              +  19,280  × reg_South
              +  18,017  × reg_West
```

**Overall model fit: R² = 0.8353 (83.5% of sales variance explained)**



## 3. Explanation of Each Coefficient

| Variable | Coefficient | P-value | Significant? | Business Meaning |
|---|---|---|---|---|
| Intercept | 30,213 | 0.533 | No | Theoretical base when all inputs = 0; not meaningful on its own |
| footfall | 28.53 | < 0.001 | ✅ Yes *** | Each additional customer adds £28.53 in monthly sales (holding all else constant) |
| marketing_spend | 1.18 | < 0.001 | ✅ Yes *** | Each extra £1 in marketing adds £1.18 in sales; ROI is positive |
| avg_discount_pct | −49,245 | 0.174 | ❌ No | Higher discounts weakly associated with lower sales; not statistically significant — discounting does not clearly boost sales |
| staff_count | 3,041 | 0.015 | ✅ Yes * | Each additional staff member adds ~£3,041 in sales; staffing levels matter |
| inventory_availability_pct | 3,048 | < 0.001 | ✅ Yes *** | Each 1% improvement in stock availability adds £3,048; reducing stockouts drives revenue |
| customer_rating | 14,214 | 0.003 | ✅ Yes ** | Each 1-point increase in customer rating associated with £14,214 more in monthly sales |
| reg_North | 5,270 | 0.451 | ❌ No | North region not significantly different from East |
| reg_South | 19,280 | 0.007 | ✅ Yes ** | South region stores sell £19,280 more than East on average |
| reg_West | 18,017 | 0.004 | ✅ Yes ** | West region stores sell £18,017 more than East on average |



## 4. Dummy Variable Explanation

### What are dummy variables?

Categorical variables (text labels like "South") cannot be used directly in a regression equation because regression requires numerical inputs. We convert each category into a **binary (0 or 1) variable** — called a dummy variable.

### How they were created

**region** has 4 categories: East, North, South, West

For each categorical variable, we create **(number of categories − 1)** dummy variables. One category is omitted — this is the **reference category**. Its effect is absorbed into the intercept.

### Reference Categories

| Variable | Reference Category | Reason for Choice |

| region | **East** | Provides a stable geographic baseline for comparison |



## 5. Final Model Selected

**→ Multiple Regression (R² = 0.8353)**

This model was selected because:
- It explains **83.5%** of the variation in monthly sales — far superior to either simple model
- It captures both **operational levers** (footfall, marketing, staff, inventory) and **structural factors** (store type, region)
- Most key predictors are **statistically significant** at the 5% or stricter level
- The model provides **actionable insights** for each business decision the leadership team is considering



## 6. Reason for Selecting the Final Model

The simple models were useful for understanding individual relationships, but they are too limited for business decision-making:

- **Simple Model 1 (footfall only):** R² = 0.74 — good but omits all controllable levers  
- **Simple Model 2 (marketing only):** R² = 0.17 — very limited explanatory power  
- **Multiple Regression:** R² = 0.84 — accounts for the full picture of sales drivers

The multiple regression model allows leadership to ask: *"If we increase marketing spend by £10,000 and improve inventory availability by 5%, what is the estimated impact on sales?"* — something neither simple model can answer.

> **Note:** R² of 83.5% is strong for real-world business data. The remaining 16.5% unexplained variance reflects factors outside the dataset (e.g., local events, competitor promotions, weather, store condition).
