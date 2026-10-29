# NHL point probability model

[Back to portfolio](../README.md) · [Notebook](../notebooks/nhl_points_model.ipynb)

## Question

How likely is a regular-season NHL skater to record at least one point (goal or assist), conditional on appearing in the game?

## Data and approach

Historical player-game statistics come from NHL Stats REST. Schedule and roster candidates come from NHL Gamecenter. Downloads are paginated, cached, and checked for missing fields and duplicate records.

Lagged features describe scoring, shots, total and power-play ice time, team offense, opponent defense, home ice, and rest. Rolling statistics are shifted so a game's outcome cannot enter its own features.

A fixed 50/50 blend of logistic regression and histogram gradient boosting predicts whether a skater records a point. A later-period logistic calibrator adjusts probabilities. A separate Poisson model estimates expected points.

## Evaluation and reporting

The chronological backtest trains on the earliest 65% of game dates, calibrates on the next 15%, and tests on the final 20%. Earlier test-period games can update rolling features while fitted model weights remain fixed.

Brier score, log loss, and calibration are compared with a constant training-average baseline and a smoothed recent player hit rate. Daily outputs include point probability, expected points, recent ice time, and history flags. Saved pregame forecasts are graded after games, with DNPs excluded from conditional-model scoring.

An optional odds module compares predictions with timestamped market prices. A prospective simulation records fixed selections and grades them later; it does not place wagers or establish profitability.

## Limitations

Current rosters are candidate lists, not confirmed lineups. The model does not include confirmed lines, live injury checks, confirmed starting goalies, or expected-goals data. Trades and changing roles can weaken historical estimates. Player outcomes in the same game are correlated, so multiplying probabilities is not a validated parlay-pricing method.

## Run

Download the notebook and open it in Google Colab with a CPU runtime. Review Settings, set a date or leave it blank for today in New York, and run all cells. Drive storage preserves caches and forecasts. Optional odds fetching is disabled in this edition; enable it only after configuring your own `ODDS_API_KEY` in Colab Secrets.

Portfolio preparation checked Python syntax and removed saved outputs. Full data downloads, training, and API requests were not rerun; this page reports no independently verified accuracy or return figures.
