# Methodology, limitations and reproducibility

## Scope
This project is a compact and deliberately synthetic demonstration of structured-data regression. It is **not** a recreation of Ibrar Pervaiz's 61-participant FlyEase study.

## Data-generation assumptions
- The generator creates numerical friction factors (checkout steps, delay, payment errors), categorical booking frequency/age band and 1–5 satisfaction.
- The target includes intentionally scripted relationships, random noise and clipping. The resulting correlations arise by construction.
- Fixed seeds support reproducibility; these values are **not** measurements of real travelers.

## Evaluation
- The pipeline is fit on the 75% training partition only, with a seeded 25% holdout.
- Numeric imputation/standardization and categorical one-hot encoding are inside the estimator pipeline to prevent transformation leakage.
- A DummyRegressor is evaluated on the same holdout, alongside Ridge MAE and R².
- Permutation importance is evaluated on holdout predictions; it measures sensitivity, **not causality**.
- Training/test split is row-based and assumes rows are independent. A longitudinal user-level dataset would require grouped splitting instead.

## Interpretation and responsible use
- Reported performance is strictly on the generator's synthetic distribution.
- Small changes in class mix, noise or sample size can change metrics.
- The demo has no direct clinical, operational or commercial validity.

## Future work
Collect genuinely consented datasets, document the instrument and sampling frame, pre-register evaluation criteria, add repeated splits and uncertainty intervals, and compare alternative modeling families.