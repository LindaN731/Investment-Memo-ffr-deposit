# Investment Memo
# Deposit Rate Pass-Through & Bank Characteristics

&gt; Empirical analysis of deposit rate pass-through asymmetry across 4,189 U.S. banks (2016–2025). Examines how bank characteristics predict deposit beta during mild vs. aggressive Federal Funds Rate cycles using sub-sample OLS and LASSO variable selection.

---

## Overview

This project investigates how U.S. banks adjust deposit rates in response to Federal Funds Rate (FFR) changes, and which bank characteristics matter most for this pass-through. Using a panel of 163,371 bank-quarter observations, we compare two distinct monetary regimes:

- **2016–2021**: Mild, gradual FFR changes (79,591 obs.)
- **2022–2025**: Aggressive hiking cycle, up to +1.46% per quarter (67,024 obs.)

Key techniques include bank-clustered robust standard errors, PanelOLS with entity fixed effects, and LASSO regularization for variable selection.

---

## Methods & Libraries

| Method | Purpose | Library |
|:---|:---|:---|
| **Pooled OLS** | Baseline full-sample estimation | `statsmodels` |
| **Sub-sample OLS** | Regime-dependent deposit beta (2016–2021 vs. 2022–2025) | `statsmodels` |
| **PanelOLS + EntityEffects** | Bank fixed effects with full interaction terms | `linearmodels` |
| **LASSO (L1 Regularization)** | Variable selection & elimination path (5-fold CV) | `scikit-learn` |
| **Robust Inference** | Bank-clustered standard errors (IDRSSD level) | `statsmodels` / `linearmodels` |
| **Data Wrangling** | Panel cleaning, regime dummies, lag construction | `pandas`, `numpy` |
| **Visualization** | Time-series, coefficient charts, LASSO paths | `matplotlib` |

---

## Tech Stack

`Python` `pandas` `numpy` `statsmodels` `linearmodels` `scikit-learn` `matplotlib`


## Key Findings (Summary)

- **Regime-dependent beta**: Estimated deposit beta during the 2022–2025 aggressive cycle (~0.14) is roughly 3.7× larger than the 2016–2021 mild cycle (~0.04).
- **Asymmetric pass-through**: In our sample, rate cuts appear to transmit ~45% faster than rate hikes (cutting beta > hiking beta).
- **Bank characteristics**: Loan intensity (`loanlag`) emerges as the strongest predictor of deposit rate adjustment; leverage (`leveragelag`) is eliminated by LASSO and shows limited predictive power in this sample.
- **Size effect**: Large banks behaved differently across regimes (negative in 2016–2021, slightly positive in 2022–2025), but the effect is modest and dropped under stricter regularization.

---

## Data

- **Source**: FFIEC Call Reports (U.S. bank regulatory filings)
- **Panel**: 4,189 unique banks × 40 quarters (2016Q2–2025Q4)
- **Key variables**: Deposit rate change, FFR change, bank size, non-interest income ratio, ROA, leverage, loan ratio, liquidity ratio (all controls lagged)

---

## Author

**Yihan (Linda) Niu**  
- University of California, Davis 
- Economics & Mathematical Analytics and Operations Research 
- Date: June 2026

---

*Disclaimer: This project is for educational and research purposes. It does not constitute personalized financial or investment advice.*
