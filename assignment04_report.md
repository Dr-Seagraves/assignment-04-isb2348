# Assignment 04 Interpretation Memo

**Student Name:** Isabella
**Date:** February 16
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable | X Variable | Interpretation Focus |
|-------|------------|------------|----------------------|
| 1 | ret (annual) | div12m_me | Dividend yield |
| 2 | ret (annual) | prime_rate | Interest rate sensitivity |
| 3 | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.

---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**
- Intercept (β₀): [0.1082] (SE: [0.006], p-value: [0.000])
- Slope (β₁): [-0.0687] (SE: [0.032], p-value: [0.035])
- R²: [0.002] | N: [0.001]

**Model 2: ret ~ prime_rate**
- Intercept (β₀): [0.6194] (SE: [0.106], p-value: [0.000])
- Slope (β₁): [-0.0930] (SE: [0.019], p-value: [0.000])
- R²: [0.009] | N: [0.009]

**Model 3: ret ~ ffo_at_reit**
- Intercept (β₀): [0.0973] (SE: [0.009], p-value: [0.000])
- Slope (β₁): [0.5770] (SE: [0.567], p-value: [0.309])
- R²: [0.000] | N: [0.000]

*Note: Model 3 may have fewer observations if ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**
- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a [slope value] change in annual return.
- [Your interpretation: Is higher dividend yield associated with higher or lower returns? Neither, there is no correlation. The line of best fit is completely straight. This couold be because dividends are not declared based on a companies return.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a [slope value] change in annual return.
- [Your interpretation: Does the evidence suggest REIT returns are sensitive to interest rates? In which direction?] Slightly, in a negative direction.

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a [slope value] change in annual return.
- [Your interpretation: Do more profitable REITs (higher FFO/Assets) earn higher returns?] Yes, because the slope is positive.

---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** [Significant] — [slope p is negative]
- **prime_rate:** [Significant] — [slope p is negative]
- **ffo_at_reit:**  Not significant] — [slope p is positive]

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** [prime_rate]

---

## 5. Model Fit (R-squared)

Compare R² across the three models:
- [Your interpretation: Which predictor explains the most variation in annual returns? Is R² high or low in general? What does this suggest about other factors driving REIT returns?]Low, this means the other factors do not explain the variation in REIT annual returns.

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- [Assets]: the income the company generates based on its assets
- [dividends]: [valuable information for all the stakeholders]
- [prime loan rate]: [important information for stakeholders and banks]

**Potential bias:** If omitted variables are correlated with both the X variable and ret, our slope estimates may be biased. Omitted variables such as market returns, interest rates and inflation couold all have a negative or positive effect on the x variable or the return and couold go in either directions. The information could be very inaccurate.
---

## 7. Summary and Next Steps

**Key Takeaway:**
The Prime Loan rate has the strongest relationship with REIT annual returns. This makes sense as the company needs more money because they are not generating enough returns. The more loans, the less returns.

**What we would do next:**
- Extend to multiple regression (include two or more predictors) Interest rate and Liabilities.
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector

---

## Reproducibility Checklist
- [ ] Script runs end-to-end without errors
- [ ] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [ ] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [ ] Report accurately reflects regression results
- [ ] All interpretations are in economic units (not just statistical jargon)
