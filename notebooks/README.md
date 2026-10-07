# Modeling notebooks

## Baseline and logistic regression

`logistic_regression_baseline.ipynb` is self-contained and reads the raw files in `data/`. It can run from the project root or from `notebooks/`.

Install the project dependencies with `pip install -r requirements.txt`, select that Python environment in Jupyter, and run all notebook cells. Scikit-learn 1.3 is incompatible with NumPy 2; the requirements select a newer compatible release.

The notebook compares a smoothed generator/local-hour/season frequency baseline with one L2 logistic regression per generator. It evaluates expanding-window folds for 2020, 2021, and 2022, with seven days excluded before each validation year. Scores use one global micro ROC-AUC over all generator-hour predictions. Scaling, categorical encoding, and baseline frequencies are fitted on each training fold only.

Artifacts use a consistent structure under `outputs/`:

- `baseline/`: baseline submission and validation predictions (CSV).
- `logistic_regression/`: logistic regression submission, validation predictions, and coefficients (CSV).
- `evaluation/`: shared `cv_scores.csv`, `experiment_log.csv`, and configuration in `metadata.json`.

Validation prediction CSV files contain `Run No` and the same 2352 prediction columns as Kaggle submissions. See [the project summary](../report/progress_summary.md) for the current results.

The initial features use initial storage, terminal water values, full-horizon prices and inflows, calendar features, and price rank. Future actual reservoir volume and calculation time are excluded. Check that full-horizon inputs are permitted by the competition specification. These are initial experiments, not tuned models; use the fixed local validation folds to evaluate changes.

This notebook is an experiment notebook. The final two submission notebooks and report still need to be prepared and checked against the course requirements.
