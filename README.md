# Data cleaning effects in one hour wind power forecasting

Code for the paper *Quantifying Data Cleaning Effects in One Hour Wind Power Forecasting with Unseen Turbine Evaluation* (Nhat Khoa Ha, Ngoc Dat Pham, Thu Le; FPT University, Ho Chi Minh City).

We forecast the active power of each turbine one hour ahead on the SDWPF dataset (4.7 million SCADA records, 134 turbines, 245 days). We add three validity rules in sequence (negative power set to zero, rows with unknown state removed, rows with abnormal angles removed), score every variant on the same clean test rows, and repeat the test on turbines held out of training.

## Main results

| Check | Result |
|---|---|
| Persistence MAE | 126.07 kW |
| LightGBM (L1 objective) MAE | 122.22 kW, 3.05% below persistence, 95% bootstrap interval [0.73, 5.38]% |
| Models beating persistence | 4 of 10 (LightGBM, XGBoost, Extra Trees, HistGB) |
| Cleaning ladder, LightGBM skill | 2.47% → 2.48% → 2.76% → 3.05% |
| Unseen turbines | Higher error for every method; LightGBM skill falls from 2.93% to 1.90% |
| Wind speed bands | LightGBM is worse than persistence below 3 m/s and above 11 m/s |

Read these with care. The ladder gain (0.76 kW) is close to the effect of adding 20,000 training rows (about 0.7 kW). The mean over the ten model families does not improve with cleaning. Scored per day, the gain over persistence is not significant (Wilcoxon p = 0.071).

## Repository

| File | Purpose |
|---|---|
| `Notebook_A_OnGoingAssessment2_ICIDST_SDWPF_CleaningRules.ipynb` | Download data, flag the validity rules, EDA, SQL queries, handover to B |
| `Notebook_B_OnGoingAssessment2_ICIDST_SDWPF_CleaningRules.ipynb` | Features, chronological split, ten models, cleaning ladder, unseen turbines, wind bands, bootstrap and Wilcoxon tests |

Only the two notebooks are tracked. Data, tables and figures are created when you run them.

## Run it

```bash
pip install pandas numpy duckdb pyarrow scikit-learn lightgbm xgboost matplotlib scipy
```

1. Put both notebooks in one folder and start Jupyter there (Python 3.11.9 was used).
2. Run Notebook A first. It downloads `sdwpf_245days_v1.csv` (about 334 MB, CC BY 4.0) into `data/raw/`, then writes `data/processed/` and `sql/queries.sql`.
3. Run Notebook B. It checks the parquet file against `manifest.json` and writes tables and figures to `report/`.

If the automatic download fails, get the file from [doi.org/10.6084/m9.figshare.24798654](https://doi.org/10.6084/m9.figshare.24798654) and copy it to `data/raw/`. Random Forest and Extra Trees use the absolute error criterion and are slow.

## Setup in brief

- 47 of 134 turbines; every fourth one (12) is held out of training.
- 17 features; target is the power change six steps (one hour) ahead.
- Split by day: 70% train, 10% validation, 20% test. The saved run uses 60,000 / 40,000 / 40,000 rows.
- Skill score: `100 × (1 − MAE_model / MAE_persistence)`.

## Limitations

One farm, one test period of 49 days, no extensive hyperparameter search. Unseen turbines come from the same farm. Temperature columns contain values near −273 that no rule flags, and the temperature features were not ablated.

## Citation

Ha, N. K., Pham, N. D., Le, T. *Quantifying Data Cleaning Effects in One Hour Wind Power Forecasting with Unseen Turbine Evaluation.* FPT University, Ho Chi Minh City.

Dataset: Zhou, J., et al. SDWPF: a dataset for spatial dynamic wind power forecasting over a large turbine array. *Scientific Data* 11, 649 (2024). https://doi.org/10.1038/s41597-024-03427-5
