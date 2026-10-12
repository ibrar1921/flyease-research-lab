<div align="center">

# ✈️ FlyEase Research Lab
### Reproducible UX analytics and machine-learning evaluation

**Python · pandas · scikit-learn · feature engineering · research methodology**

[![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![CI](https://github.com/ibrar1921/flyease-research-lab/actions/workflows/python-tests.yml/badge.svg)](https://github.com/ibrar1921/flyease-research-lab/actions/workflows/python-tests.yml)
[![Research](https://img.shields.io/badge/Focus-Human--Centred_AI-118F89)](#research-context)

[Source](analysis.py) · [Tests](test_analysis.py) · [Methodology](docs/methodology.md)

</div>

---

## Why this project?

Good AI research begins with **careful data preparation, baselines and transparent evaluation**. This standalone laboratory is inspired by Ibrar Pervaiz's MSc **FlyEase** research at York St John University, which investigated mobile flight-booking usability through a 16-question survey of 61 participants, SPSS analysis, regression-model comparison and Figma prototyping.

**Crucial distinction:** this repository does **not** contain the original survey or replicate its conclusions. It generates entirely **synthetic responses** with intentional relationships so researchers can practice a reproducible ML workflow without exposing personal data.

## ✨ Implemented features

- Seeded synthetic survey with booking frequency, checkout steps, loading delay, pricing clarity and payment errors.
- A `ColumnTransformer` pipeline: imputation and scaling for numeric inputs; imputation and one-hot encoding for categorical inputs.
- `Ridge` regression compared to a mean-value dummy baseline on a held-out test set.
- Mean absolute error (MAE), R² and permutation importance, all exported as structured JSON.
- Reproducible CSV export and automated `unittest` checks.

## 🧰 Quick start

Requires **Python 3.11+**.

```bash
git clone https://github.com/ibrar1921/flyease-research-lab.git
cd flyease-research-lab
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS / Linux: source .venv/bin/activate
python -m pip install -r requirements.txt
python analysis.py --responses 500 --seed 42 --out results
python -m unittest discover -v
```

Outputs: `results/synthetic_survey.csv` and `results/report.json`. `results/` is gitignored.

### Sample report structure

```json
{
  "dataset": "synthetic_flight_booking_ux",
  "responses": 500,
  "holdout_responses": 125,
  "ridge_mae": 0.0,
  "baseline_mae": 0.0,
  "ridge_r2": 0.0,
  "feature_importance_mae_increase": {}
}
```

**Note:** The zero values above show the **JSON schema**, not measured model results. Run the script to produce real outputs.

## 🏗️ Project structure

```text
flyease-research-lab/
├── analysis.py              # Synthetic data, preprocessing and evaluation
├── test_analysis.py         # Deterministic and validation tests
├── requirements.txt
├── docs/
│   └── methodology.md       # Assumptions, validity threats and next steps
└── .github/workflows/
    └── python-tests.yml     # Automated test workflow
```

## 🔬 Research context

Research interests: **human-centred AI, usability analysis, quantitative methods and interpretable models**. Interpret permutation importance as sensitivity of this *synthetic* benchmark, **not** causal influence or a finding from human participants.

See [Methodology & limitations](docs/methodology.md) for dataset construction, split strategy and validation risks.

## 🗺️ Roadmap

- [ ] Add cross-validation and bootstrap confidence intervals
- [ ] Implement a reproducible comparison of Linear, Ridge, Lasso, Elastic Net, decision trees, random forests and SVR
- [ ] Add a privacy-reviewed real survey import format, with consent and ethical review
- [ ] Document usability experiments and associated Figma mockups

## 👤 About the author

**Ibrar Pervaiz** · Software Engineer, K.M.S Business Services Ltd. · MSc Computer Science, York St John University

[GitHub profile](https://github.com/ibrar1921) · [LinkedIn](https://www.linkedin.com/in/ibrar-pervaiz-0b1a2a158/)

> Educational research-methods implementation. Synthetic data only. No personal or proprietary survey data.
