# Energy Load Forecaster

A concise, production-style time series project that builds day-ahead forecasts of UK electricity demand. Given a day’s 48 half-hourly load values, the model predicts the next day’s 48 values to support smarter grid operations: better storage dispatch, improved renewable integration, and reduced imbalance costs.

Date Completed: November 2024

## Project Overview

This repo contains a complete, reproducible workflow for short‑term load forecasting:
- Data loading and integrity checks (duplicate removal, NA handling)
- Feature/label construction for day‑ahead prediction (48 → 48 half‑hourly profile mapping)
- Baseline model (Multivariate Linear Regression)
- Model exploration with a tree ensemble (Random Forest + cross‑validated hyperparameter tuning)
- Evaluation on a held‑out dataset with clear quantitative metrics and visual diagnostics

Artifacts:
- `Energy-Forecast-Model.ipynb` — The end‑to‑end notebook you can run top‑to‑bottom.
- `UKLoad2023.json` — Historical UK load data for 2023 (training/analysis).
- `UKLoad2023_test.json` — A held‑out dataset for lightweight evaluation.

Business impact:
- Improves day‑ahead accuracy for operational planning
- Enables more economic storage dispatch and demand flexibility
- Supports greater renewable penetration and lower carbon intensity

## Technical Stack

- Language: Python 3.x
- Core: pandas, numpy, scikit‑learn
- Visualization: matplotlib, seaborn
- Environment: Jupyter (VS Code Notebooks or JupyterLab)

Optional extensions explored in the notebook narrative:
- Cross‑validation via `GridSearchCV`
- Normalized performance indicators for comparability across scales

## How to Run

Run locally with Jupyter or VS Code. On Windows (cmd.exe):

1) Create and activate a virtual environment (recommended)
```
python -m venv .venv
.venv\Scripts\activate
```

2) Install dependencies
```
pip install -U pip
pip install pandas numpy scikit-learn matplotlib seaborn jupyterlab
```

3) Launch Jupyter (pick one)
```
jupyter lab
```
Or open the folder in VS Code and use the built-in Jupyter support to run the notebook.

4) Open and run the notebook
- Open `Energy-Forecast-Model.ipynb`
- Run cells from top to bottom to reproduce the workflow

Notes
- The notebook expects `UKLoad2023.json` and `UKLoad2023_test.json` in the repo root.
- For deterministic model splits, set a fixed `random_state` where provided.
- The Random Forest block performs a small grid search for clarity (fast to run). Scale the grid for deeper tuning as needed.

## What Recruiters Should Notice

- Clear problem framing: 48-period day‑ahead forecasting aligned to grid operations
- Clean, readable code with explicit data integrity checks
- Baseline + ensemble comparison with visual diagnostics and normalized KPIs
- Practical next steps outlined (calendar/weather features, rolling-origin evaluation, sequence models)

## Next Steps (Future Work)

- Add calendar features (day‑of‑week, holidays, seasonal markers) and weather covariates
- Use rolling‑origin evaluation to mirror deployment conditions
- Explore ARIMA/SARIMA, Prophet, LSTM/TCN for sequence modeling and uncertainty quantification
