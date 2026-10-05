# Three Blind Mice

TDT4173 course project (NTNU, autumn 2026): predicting unit commitment (ON/OFF per generator per hour) for the Tokke–Vinje hydropower system, as a Kaggle InClass competition from SINTEF Energy Research.

Metric: micro-averaged ROC-AUC over all unit-hour predictions.

## Setup

```bash
pip install -r requirements.txt
```

Data is not tracked in Git. Download it from Kaggle and place it in `data/`.

## Structure

- `notebooks/`: EDA and experiments
- `submission/`: Short_notebook_1.ipynb, Short_notebook_2.ipynb
- `report/`: project report
- `experiments.csv`: experiment log

## Team

- Bilal Saher
- Marco Josefsen
- Teresa Tran
