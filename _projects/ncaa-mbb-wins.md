---
layout: page
title: NCAA Men's Basketball Wins Prediction
description: Predicts NCAA Division I men's regular-season wins from team-season efficiency stats using season-based evaluation and interpretable models.
img: /assets/img/ncaa-m-predictions-thumbnail.png
importance: 2
category: work
---

This project predicts NCAA Division I men's basketball regular-season wins from
team-season performance metrics, aiming to show how a compact, interpretable
feature set can explain team success. I built a portfolio-ready pipeline: a
single script reproduces all metrics, plots, and tables, and a clean notebook
documents the full analysis.

The dataset contains one row per team-season from 2013-2023 (plus a separate
2020 file), with features such as adjusted offense/defense (ADJOE/ADJDE) and
shooting/turnover rates. Models were evaluated with a season holdout (train on
seasons before 2023, test on 2023) and rolling year-by-year tests for
2019-2023. Three simple models-Linear Regression, Ridge, and Lasso-were
compared to baselines (mean wins and ADJOE-ADJDE only). The chosen model was
Linear Regression for simplicity, reaching R^2 0.807 and MAE 2.16 wins on the
2023 holdout, substantially better than the baselines (MAE 5.08 and 3.14 wins).

To keep the model honest, I added correlation/VIF checks for multicollinearity
and diagnostic plots (predicted vs actual, residuals, and a learning curve) to
visualize generalization. The results show the model is accurate on average
within about two wins and identify the teams most over- and under-predicted in
2023.

**Key Methods**
- Season-based holdout and rolling-year evaluation
- Linear Regression, RidgeCV, LassoCV (standardized)
- Residual/learning-curve diagnostics + VIF for multicollinearity

**Results**
- Holdout 2023: R^2 0.807, MAE 2.16 wins
- Baselines: MAE 5.08 (mean) and 3.14 (ADJOE-ADJDE)

**Figures**
{% include figure.liquid path="/assets/img/predicted_vs_actual_holdout.png" title="Predicted vs Actual Wins (Holdout 2023)" %}
{% include figure.liquid path="/assets/img/learning_curve_mae.png" title="Learning Curve (MAE) - Linear Regression" %}
{% include figure.liquid path="/assets/img/standardized_coefficients.png" title="Standardized Coefficients (Linear Regression)" %}

**Links**
GitHub: [Repository README](https://github.com/stephenchen06/ncaa-mbb-win-model/blob/main/README.md) | Report: N/A | Demo: N/A
