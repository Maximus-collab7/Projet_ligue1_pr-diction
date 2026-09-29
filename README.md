# Ligue 1 Match Outcome Prediction (2025-2026 season)

Applied algorithmics project at ESILV (Paris), carried out in pairs.

## Objective

Predict the result of each French Ligue 1 match of the 2025-2026 season as a three-class classification problem:

- `1`: home team wins
- `0`: draw
- `-1`: away team wins

## Data

Eight CSV files are combined:

| Dataset | Rows | Content |
|---|---|---|
| Historical matches (2012-2024) | 4,691 | Teams, scores, results |
| Matches to predict (2025) | 233 | Fixtures without results |
| Clubs | 36 | Club information |
| Player valuations | 32,856 | Market value before each season |
| Player appearances | 128,240 | Individual statistics per match |
| Lineups | 161,049 | Starting line-ups |
| Match events | 61,944 | Goals, cards, substitutions |

## Data preparation

- Dates converted to datetime and all time-dependent tables sorted chronologically, so that features computed at a given date never use future matches (no data leakage).
- Data quality checks on table sizes and structure after loading.

## Exploratory analysis

- **Outcome distribution:** home wins about 44%, draws about 27%, away wins about 29%. Always predicting a home win gives a **44% baseline** that any model must beat.
- **Home advantage over time:** stable at around 43-46% per season, except in 2019-2020, when matches behind closed doors (COVID) reduced it.
- **Goals by result:** average goals scored by each side depending on the outcome, motivating rolling features on goals scored and conceded.

## Planned modelling

- Feature engineering: recent form, squad quality (market values), head-to-head history
- Models: logistic regression, Random Forest, Gradient Boosting, XGBoost
- Stratified cross-validation, comparison with the naive baseline, error analysis

## Tools

Python, pandas, NumPy, Matplotlib, Seaborn, scikit-learn, XGBoost, Jupyter Notebook

## Note

The notebook comments are written in French.
