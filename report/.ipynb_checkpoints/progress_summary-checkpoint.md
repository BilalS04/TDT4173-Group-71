# Project progress — Group 71

We inspected the Tokke–Vinje dataset and reviewed the preprocessing notebook. We then implemented and ran a standalone modeling notebook from raw data, comparing two predictors:

- **Baseline:** historical ON frequencies per generator, local hour, and season, smoothed towards each generator's overall training frequency.
- **Logistic regression:** one L2-regularized model per generator using calendar features, prices, weekly price ranks, initial storage, terminal water values, inflows, and selected interactions.

Both models use expanding-window validation for 2020, 2021, and 2022 with a seven-day gap. Frequencies, scaling, and categorical encoding are fitted on training data only. Actual future reservoir volumes and calculation time are excluded. The score is global micro-averaged ROC-AUC.

| Model | 2020 | 2021 | 2022 | Mean ± SD |
|---|---:|---:|---:|---:|
| Baseline | 0.5693 | 0.5132 | 0.5731 | 0.5519 ± 0.0335 |
| Logistic regression | 0.8467 | 0.9046 | 0.9432 | 0.8982 ± 0.0486 |

Logistic regression outperformed the baseline in all three years. Both models were fitted on all labeled cases, and their test predictions were exported and checked against the Kaggle format. Coefficients and validation predictions are saved for interpretation and comparison. No predictions have been submitted to Kaggle in this work.

**Next step:** compare the other group members' models on the same validation splits. Full-horizon prices, inflows, and terminal water values are assumed to be permitted scheduling inputs; this assumption still needs verification against the competition rules.

[Model notebook](../notebooks/logistic_regression_baseline.ipynb) · [CV results](../outputs/evaluation/cv_scores.csv) · [Experiment log](../outputs/evaluation/experiment_log.csv)
