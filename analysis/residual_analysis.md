# Residual Analysis

**Model used:** Multiple Regression (R² = 0.8353)  
**Residual = Actual monthly_sales − Predicted monthly_sales**

A positive residual means the store sold **more** than the model expected.  
A negative residual means the store sold **less** than the model expected.

---

## Predicted vs Actual Sales (Sample)

Predicted sales were calculated by applying the multiple regression equation to each of the 320 store-month observations. Full predictions and residuals are stored in Sheet 6 of `regression_workbook.xlsx`.

---

## Top 5 Records with Largest Positive Residuals

These are stores that **outperformed** model predictions — they generated more sales than their footfall, marketing spend, store type, and other factors would suggest.

| Rank | Store ID | Store Type | Region | Actual Sales (£) | Predicted Sales (£) | Residual (£) |
|---|---|---|---|---|---|---|
| 1 | STR-1028 | Mall | East | 713,611 | 601,419 | **+112,192** |
| 2 | STR-1073 | Residential | East | 813,317 | 711,191 | **+102,125** |
| 3 | STR-1030 | Residential | West | 820,519 | 730,256 | **+90,263** |
| 4 | STR-1026 | Mall | East | 625,514 | 536,308 | **+89,206** |
| 5 | STR-1027 | High Street | West | 795,154 | 708,389 | **+86,765** |

### What these residuals may mean (business interpretation)

Stores with large positive residuals are **punching above their weight**. Possible explanations include:

- **Exceptional store management:** Strong local managers who drive customer conversion beyond what metrics capture
- **Micro-location advantages:** Proximity to busy transport links, offices, or anchor tenants not captured in competitor distance data
- **Local loyalty:** Long-established stores with repeat customers and community ties
- **Unmeasured product mix:** These stores may stock higher-margin or higher-demand products relative to peers
- **Recent investment:** Capital improvements (refits, extended hours) that are not yet reflected in the predictor variables

> **Business action:** These stores should be studied as **best practice benchmarks**. Identifying what makes STR-1028, STR-1073, and STR-1030 outperform their predicted sales could yield insights applicable across the chain.

---

## Top 5 Records with Largest Negative Residuals

These are stores that **underperformed** model predictions — they generated less sales than their inputs would predict.

| Rank | Store ID | Store Type | Region | Actual Sales (£) | Predicted Sales (£) | Residual (£) |
|---|---|---|---|---|---|---|
| 1 | STR-1017 | High Street | West | 685,379 | 838,966 | **−153,587** |
| 2 | STR-1023 | Mall | South | 627,172 | 766,067 | **−138,895** |
| 3 | STR-1012 | Residential | West | 595,468 | 722,545 | **−127,077** |
| 4 | STR-1007 | Mall | West | 800,452 | 915,179 | **−114,727** |
| 5 | STR-1077 | Residential | South | 538,376 | 634,950 | **−96,574** |

### What these residuals may mean (business interpretation)

Stores with large negative residuals are **underdelivering relative to their resources and characteristics**. Possible explanations include:

- **Local competition pressure:** A strong competitor nearby that is not fully captured in competitor_distance_km (which only measures distance, not competitor size or quality)
- **Operational issues:** Stock management problems, customer service issues, or store condition problems that suppress conversion despite good footfall
- **Poor marketing effectiveness:** Marketing spend may be reaching the wrong audience or in the wrong format for that local market
- **Temporary disruption:** Store refurbishments, staff turnover, or local events during the observation period
- **Catchment area quality:** Footfall may be high but from lower-spending demographics not captured in the dataset

> **Business action:** These stores warrant **operational review**. STR-1017, STR-1023, and STR-1007 in particular are significantly underperforming their potential based on all measured factors. Targeted interventions — management coaching, promotional changes, or competitive response — should be considered.

---

## Under-prediction and Over-prediction Patterns

### By Store Type

| Store Type | Avg Residual (£) | Pattern |
|---|---|---|
| Mall | Mixed (both over and under) | Model performs reasonably well; some Mall outliers in both directions |
| Residential | Slightly positive residuals | Model may slightly **under-predict** Residential store performance |
| High Street | Mixed | STR-1017 is a strong negative outlier; otherwise reasonable fit |
| Airport | Near zero on average | Model fits Airport stores well |

### By Region

| Region | Pattern |
|---|---|
| East | Several positive residuals — model tends to **under-predict** East stores |
| West | Several large negative residuals — model may **over-predict** West stores |
| South | Mixed — one strong negative outlier (STR-1023) skews the picture |
| North | Generally well-fit by the model |

### Overall Assessment

The model **does not show a systematic bias** across all stores, which is a good sign. However:

- **West region Mall stores** (STR-1007, STR-1023) show a tendency to underperform predictions, suggesting there may be local competitive dynamics in the West that the model does not fully capture
- **East region** stores tend to outperform predictions, possibly reflecting unmeasured advantages (e.g., higher footfall quality, stronger brand presence)

---

## Residual Summary Statistics

| Metric | Value |
|---|---|
| Mean residual | ~0 (expected for OLS regression) |
| Largest positive residual | +£112,192 (STR-1028, Mall/East) |
| Largest negative residual | −£153,587 (STR-1017, High Street/West) |
| Approx. 95% of residuals within | ±£60,000 |

A mean residual near zero confirms the model is **unbiased on average**, even if individual store predictions vary. The full residual table is available in Sheet 6 (`6_Predictions_Residuals`) of `regression_workbook.xlsx`.
