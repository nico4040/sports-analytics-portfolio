# NFL touchdown probability model

[Back to portfolio](../README.md) · [Notebook](../notebooks/nfl_touchdown_model.ipynb)

## Question

How likely is an NFL player to score at least one rushing or receiving touchdown in an upcoming game, conditional on taking an offensive snap?

## Data and approach

The notebook uses nflverse data through `nflreadpy`, combining schedules, rosters, offensive snap counts, player statistics, and play-by-play. Starting from snap counts keeps offensive participants with zero carries and targets in the historical sample.

Features summarize earlier player workload, red-zone opportunities, team production, and position. Input statistics are frozen at the start of the selected NFL week. Logistic regression and histogram gradient boosting model joint rushing/receiving touchdown outcomes; temperature calibration adjusts the resulting probabilities.

For a 2026 slate, the documented chronological comparison fits on 2020–2022, calibrates on 2023, selects on 2024, and evaluates on 2025. Because 2025 was inspected during earlier development, it is a temporal test rather than a fresh untouched holdout. Additional recent-usage and injury-context candidates have explicit checks before replacing the baseline.

## Outputs and evaluation

- Player probabilities, selected model labels, and availability or role flags.
- Brier score, log loss, AUC, and calibration summaries, including a position-only benchmark.
- Saved pregame predictions and later outcome grading, counting the earliest forecast per player-game and model family.
- Optional timestamped odds comparisons with caching and quota limits.

These outputs support reviewing probabilities and identifying where more information is needed. The optional market comparison is not a historical profitability test.

## Limitations

The target excludes passing, return, defensive, and fumble-recovery touchdowns. Active-roster membership does not confirm game-day participation. Historical injury coverage and publication timestamps are incomplete. Weather, offensive-line quality, routes, and coaching decisions are not fully captured. Recent prospective results are needed to judge reliability.

## Run

1. Download the notebook and open it in Google Colab.
2. Run the dependency-installation cell and review Settings. `SUNDAY_ONLY=False` allows non-Sunday slates; a blank date selects the next unstarted game day.
3. Keep Drive enabled to preserve caches and predictions; authorize your own Drive when prompted.
4. Run all cells. The initial historical download can take time.
5. Read the evaluation before interpreting rankings. To use optional odds, add your own `ODDS_API_KEY` through Colab Secrets and explicitly enable `FETCH_ODDS`.

Portfolio preparation checked Python syntax and removed saved outputs. It did not rerun external-data training or establish new performance results.
