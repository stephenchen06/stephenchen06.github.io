---
layout: page
title: NCAA Men's Basketball Wins Prediction
description: Predicts NCAA Division I men's regular-season wins from team-season efficiency stats using season-based evaluation and interpretable models.
img: /assets/img/ncaa-predictions-thumbnail.jpg
importance: 2
category: work
---

This project predicts NCAA Division I men’s basketball regular-season wins from team-season efficiency metrics. The dataset is one row per team-season from 2013–2023 (plus a separate 2020 file) from [BartTorvik.com](https://barttorvik.com/#). The goal is to show that a compact, interpretable feature set can explain a large share of team success. I built a reproducible pipeline: a single script generates all metrics, plots, and tables, and a clean notebook documents the full analysis.

{% include figure.liquid path="/assets/img/predicted_vs_actual_holdout.png" title="Predicted vs Actual Wins (Holdout 2023). MAE is 2.16 wins on the 2023 holdout; good predictions sit near the diagonal." width="85%" max-width="900px" %}

### What I Used

- Data: one row per team-season (2013–2023, plus a separate 2020 file). Features

include ADJOE, ADJDE, and shooting/turnover rates (e.g., EFG_O and EFG_D).

- Target: regular-season wins.

### How I Tested It

I held out the most recent season (train on seasons before 2023, test on 2023) and ran rolling year-by-year tests for 2019–2023. I compared Linear Regression, Ridge, and Lasso against two baselines: mean wins and ADJOE–ADJDE only. I report R^2 and MAE, where MAE is the average error in wins.

### What I Found

Holdout 2023 performance: R^2 0.807 and MAE 2.16 wins (about two wins off on
average). This beats the baselines (MAE 5.08 for mean wins; 3.14 for ADJOE–ADJDE only). The standardized coefficients show that shooting efficiency and turnover-related signals are among the strongest drivers of predicted wins.

{% include figure.liquid path="/assets/img/standardized_coefficients.png" title="Standardized coefficients (Linear Regression). Larger magnitudes indicate stronger drivers; some overlap is expected because features are correlated." width="85%" max-width="900px" %}

{% include figure.liquid path="/assets/img/learning_curve_mae.png" title="Learning curve (MAE). Train and validation curves stay close, suggesting limited overfitting on recent seasons." width="85%" max-width="900px" %}

### Limitations + Next Steps

This is correlational and some features are collinear (I ran correlation/VIF checks). Next steps: add schedule strength/tempo, improve error breakdowns, and continue stress-testing validation splits.

### Packages Used

scikit-learn, pandas, matplotlib, numpy,

### Links

GitHub: [Repository README](https://github.com/stephenchen06/ncaa-mbb-win-model/blob/main/README.md)

## Sources

Data: [Bart Torvik’s college basketball database](https://barttorvik.com/#)
