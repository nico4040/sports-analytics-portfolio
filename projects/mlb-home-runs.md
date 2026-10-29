# MLB home run probability model

[Back to portfolio](../README.md) · [Notebook](../notebooks/home_run_model.ipynb)

## Question

How likely is a starting hitter to hit at least one home run in a game?

The notebook produces an early active-roster board conditional on starting and a separate board using confirmed lineups. It does not estimate a hitter's probability of being in the lineup.

## Data and features

Statcast pitch data come through `pybaseball`; MLB's public API supplies schedules, probable starters, rosters, and lineups. Player IDs connect the records.

Features combine prior hitter power and contact quality, 14- and 30-day recent form, opposing starter tendencies, handedness splits, pitch-type matchups, trailing bullpen results, batting order, and venue. Rolling features exclude the prediction day, including earlier games in a same-day doubleheader. Pitch-fit summaries are model inputs, not standalone home run probabilities.

## Modeling and evaluation

Regularized logistic regression compares a simple hitter-power/batting-order baseline with a fuller feature set. Validation log loss selects the feature set and regularization strength; a separate logistic calibration step adjusts probabilities.

| Period | Purpose |
| --- | --- |
| 2022 | Build historical features |
| 2023–2024 | Fit models |
| January–June 2025 | Select features and regularization |
| July–August 2025 | Calibrate probabilities |
| September–December 2025 | Evaluate on eligible regular-season games |

Evaluation reports log loss, Brier score, average precision, calibration, and the observed home run rate among each day's top 10 entries. A daily refit reserves the latest 60 days for calibration; historical test results describe the earlier frozen model, not an independent test of the later refit.

## Outputs

Rankings include game-level home run probabilities, matchup context, and limited-history flags. The confirmed player/day view combines eligible doubleheader games using an explicitly approximate independence assumption. A tracking cell saves forecast snapshots and scores completed dates.

## Limitations

The historical lineup feed is reconstructed rather than an archived pregame snapshot. Weather, roof status, pull direction, pitch movement/location, and individual bullpen availability are not included. Small matchup samples remain uncertain after smoothing. The model excludes postseason and suspended games.

Forward tracking keeps the latest saved player-game forecast; the grading code does not independently filter snapshot timestamps against first pitch. Treat those summaries as provisional until that timing check is added. The project does not claim verified accuracy or betting profitability.

## Run

1. Download the notebook and open it in Google Colab with a CPU runtime.
2. Run the installation and imports cells, then authorize your own Google Drive in the storage cell.
3. Review `TARGET_DATE` and run the remaining cells in order. Daily forecasts require 2026 or later and enough recent games for calibration.
4. Allow time for the first Statcast download; later runs reuse cached summaries.
5. Inspect backtest results before interpreting the early and confirmed-lineup boards.

The portfolio copy clears stored outputs and preserves model code. Python syntax was checked; external data access and full model execution were not repeated.
