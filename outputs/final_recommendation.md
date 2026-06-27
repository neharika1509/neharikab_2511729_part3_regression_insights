# Final Business Recommendation

**Prepared for:** Retail Chain Leadership Team  
**Analysis type:** Multiple Linear Regression  
**Dataset:** 320 store-month observations across 80 stores (Jan–Apr 2025)  
**Final model R²:** 0.8353 — the model explains **83.5% of variation in monthly sales**

---

## 1. Which Factors Appear Most Strongly Associated with Monthly Sales?

Based on the multiple regression model, the following factors have the **strongest and most statistically significant** associations with monthly sales:

| Rank | Factor | Estimated Impact | Confidence |
|---|---|---|---|
| 1 | **Footfall (store visitors)** | +£28.53 per additional visitor per month | Very High (p < 0.001) |
| 2 | **Store Type – Airport** | +£42,282 vs Residential stores | Very High (p < 0.001) |
| 3 | **Inventory Availability** | +£3,048 per 1% improvement | Very High (p < 0.001) |
| 4 | **Store Type – Mall** | +£29,872 vs Residential stores | Very High (p < 0.001) |
| 5 | **Customer Rating** | +£14,214 per 1-star improvement | High (p = 0.003) |
| 6 | **Store Type – High Street** | +£19,057 vs Residential stores | High (p = 0.002) |
| 7 | **Region – South** | +£19,280 vs East region | High (p = 0.007) |
| 8 | **Marketing Spend** | +£1.18 per £1 spent | Very High (p < 0.001) |
| 9 | **Region – West** | +£18,017 vs East region | High (p = 0.004) |
| 10 | **Staff Count** | +£3,041 per additional staff member | Moderate (p = 0.015) |

---

## 2. Which Variables Should Leadership Focus On?

Leadership should prioritise the **controllable levers** with the strongest evidence:

### Highest Priority — Act Now

**Footfall (driving in-store traffic)**  
Footfall is the single strongest numerical predictor. Every 1,000 additional visitors per month is associated with approximately £28,530 more in sales. Strategies to increase footfall — events, loyalty programmes, advertising targeted at driving visits, improved signage and accessibility — are likely to yield the highest sales return.

**Inventory Availability**  
Each 1 percentage point improvement in stock availability is associated with £3,048 more in monthly sales. Across 80 stores, improving average availability from 87% to 92% (a 5pp gain) would be associated with an estimated **£1.2M increase in total monthly chain sales**. Reducing stockouts is a high-leverage, operationally actionable improvement.

**Customer Rating**  
A 1-star improvement in average customer rating is associated with £14,214 more in monthly sales. This reflects the compounding value of service quality — it likely both retains existing customers and attracts new ones through word of mouth and online reviews.

### Medium Priority — Optimise Allocation

**Marketing Spend**  
Marketing returns approximately £1.18 in sales per £1 spent in the model. This is a **positive ROI** on average, but the return is modest. Leadership should not simply increase total marketing spend — rather, they should ensure budgets are allocated to stores and channels where the return is highest (e.g., high-footfall stores, airport and mall locations, South and West regions).

**Staff Count**  
Each additional staff member is associated with £3,041 in additional monthly sales. This justifies adequate staffing in busy stores, but overstaffing in low-footfall locations would not be cost-effective.

### Strategic — Store Portfolio

**Store Type**  
Airport stores outperform Residential by £42,282/month, and Mall stores by £29,872/month. Where feasible, prioritising investment in Airport and Mall-format stores — or considering converting underperforming Residential stores where viable — offers structural upside.

**Region**  
South and West region stores generate approximately £19,000 more per month than East stores, all else being equal. These regions appear to have structural advantages and may warrant additional investment or expansion priority.

---

## 3. Which Variables Should NOT Be Over-Interpreted?

**Average Discount Percentage (avg_discount_pct)**  
This variable showed a **negative** association with sales in the model (suggesting higher discounts are associated with lower sales), but the result is **not statistically significant** (p = 0.174). Leadership should not conclude that discounting hurts sales — the result is simply too uncertain to act on directionally. Discounting strategy should be evaluated separately, ideally through A/B testing.

**Region – North**  
The North region coefficient was not statistically significant (p = 0.451), meaning there is insufficient evidence that North stores perform differently from East stores after controlling for other factors. Do not draw conclusions about regional performance from this coefficient alone.

**Marketing Spend as the Primary Driver**  
In the simple regression model, marketing spend showed a positive association with sales (R² = 0.167). However, in the full multiple model its coefficient drops significantly, and footfall explains much more of the variation. This suggests marketing spend may be working *through* footfall — rather than independently driving sales. Over-investing in marketing without addressing footfall conversion or inventory quality is unlikely to maximise returns.

---

## 4. Recommended Business Actions

Based on the regression evidence, the following actions are recommended in priority order:

1. **Invest in footfall-driving initiatives** — particularly in underperforming stores with good location characteristics but below-average visitor numbers. Target stores with negative residuals (e.g., STR-1017, STR-1007) where the model suggests their inputs should yield higher sales.

2. **Improve inventory availability chain-wide** — set a minimum availability target of 90%+ for all stores. Each percentage point gained delivers approximately £3,048/month per store. This is likely one of the highest-ROI operational improvements available.

3. **Invest in customer experience** — focus on improving customer ratings in stores with below-average scores (below 3.5). Even a 0.5-star improvement is associated with approximately £7,100 more in monthly sales.

4. **Review marketing spend allocation** — redistribute budgets from stores where marketing is not translating into footfall or sales (large negative residuals) to stores where the environment supports strong returns (Airport, Mall, high-footfall locations).

5. **Study best-practice stores** — STR-1028, STR-1073, STR-1030 consistently outperform model predictions. Understanding *why* they over-deliver should be a priority for knowledge transfer.

6. **Conduct targeted operational reviews** for STR-1017, STR-1023, STR-1012, and STR-1007, which significantly underperform their predicted sales despite having measured inputs that should support higher revenue.

---

## 5. Risks and Limitations Leadership Should Keep in Mind

| Risk | Detail |
|---|---|
| **Causation not proven** | Regression reveals statistical association, not cause and effect. Footfall may be high *because* a store is already successful, not purely *causing* success. |
| **Short time window** | Only 4 months of data. Seasonal effects, year-on-year trends, and long-term patterns cannot be assessed. |
| **Omitted variables** | 16.5% of sales variance is unexplained — local competition quality, store condition, management capability, and economic conditions in the catchment area are not in the dataset. |
| **Average effects** | Coefficients are chain-wide averages. The effect of footfall or marketing may be much higher or lower for specific store types or markets. |
| **No interaction effects tested** | Marketing may be more effective in high-footfall stores. Inventory improvements may matter more in Airport stores. These compound effects are not modelled here. |
| **Data quality** | 14 missing values were imputed (median). Results should be revisited as complete data becomes available. |

---

## 6. Why Regression Shows Association but Not Causation

Regression analysis identifies which variables **move together** with monthly sales. However, it cannot establish that changing one variable will *cause* a change in sales, for three key reasons:

**Reverse causation:** High-performing stores may attract higher marketing budgets (not the other way around). Successful stores may be rewarded with more staff. The causal arrow may run in either direction.

**Confounding variables:** A third unmeasured variable (e.g., local economic prosperity, mall anchor tenants) may be causing *both* high footfall and high sales, making footfall appear to "cause" sales when both are actually driven by something else.

**Selection effects:** Airport and Mall stores are in premium locations that attract more affluent shoppers. The store type coefficient captures this structural advantage — not something leadership can simply replicate by changing a Residential store's label.

**To establish causation, leadership would need:**
- Controlled experiments (e.g., randomly increase marketing spend in half the stores and measure the result)
- Longitudinal tracking of specific interventions
- Natural experiments (e.g., a competitor closing near some stores but not others)

The regression findings in this analysis are best used as a **starting point for hypothesis generation and prioritisation**, not as a final proof of what will work.

---

*Analysis completed June 2025. Data source: business_regression_data.xlsx (80 stores, Jan–Apr 2025, 320 observations).*
