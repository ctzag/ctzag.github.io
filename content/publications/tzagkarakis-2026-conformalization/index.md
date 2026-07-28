---
title: 'When Does Conformalization Help? A Cross-Paradigm Analysis of Probabilistic Electricity Price Forecasting'
authors:
  - me
  - R. Dekker
date: '2026-09-01T00:00:00Z'
publishDate: '2026-07-01T00:00:00Z'
publication_types: ['paper-conference']
publication: 'In *Proceedings of the 14th EETN Conference on Artificial Intelligence (SETN ''26)* (to appear)'
publication_short: ''
abstract: 'Probabilistic electricity price forecasting (EPF) relies on several uncertainty-quantification paradigms whose behavior under regime shift is not well understood. Conformalized Quantile Regression (CQR) guarantees coverage only when calibration and test data are exchangeable, which regime shift violates. We ask whether the base-model paradigm affects CQR''s cost in the Continuous Ranked Probability Score (CRPS). On the Dutch EPEX day-ahead market across six origins spanning 2018–2024, we evaluate Quantile Regression (QR), LASSO-regularized QR (LQR-BIC), Quantile Regression Forests (QRF), quantile Light Gradient Boosting Machine (LGBM-Q), and Natural Gradient Boosting (NGBoost), each with and without CQR. Three findings emerge. The paradigms agree in calm regimes but linear methods lead in crisis. CQR is sharply paradigm-dependent: at the September 2021 regime shift, tree models incur 40–68% higher CRPS while linear models are unaffected or improve. And LQR-BIC+CQR achieves 13% lower CRPS than QR+CQR. We trace the mechanism to the differing residual-scale behavior of tree versus linear base models under regime shift and discuss its implications for regime-aware probabilistic forecasting practice.'
summary: ''
tags: []
featured: false
links:
  - type: custom
    name: Preprint
    url: preprint_ctzag_SETN2026.pdf
image:
  caption: ''
  focal_point: ''
  preview_only: false
projects: []
slides: ''
---
