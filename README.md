# Nicholas Koch
### Sports analytics · Predictive modeling · Sports economics

I study Data Analytics and Economics at Berry College, where I expect to graduate in December 2026. My work focuses on player performance, probability modeling, and the business of sports. I use Python and R to turn sports data into analyses that can inform decisions.

[LinkedIn](https://www.linkedin.com/in/nicholas-koch-3a70501bb/) · [Published research](https://doi.org/10.1177/15586235261499115)

## Selected projects

| Project | Question | Work demonstrated |
| --- | --- | --- |
| [NFL touchdown model](projects/nfl-touchdowns.md) | How likely is a player to score a rushing or receiving touchdown? | Data preparation, lagged usage features, model comparison, calibration, and forecast tracking |
| [NHL points model](projects/nhl-points.md) | How likely is a skater to record at least one point? | API data collection, rolling features, ensemble modeling, chronological evaluation, and reporting |
| [MLB home run model](projects/mlb-home-runs.md) | How likely is a starting hitter to homer? | Statcast features, pitcher matchups, regularized regression, calibration, and lineup-aware reporting |
| [Pirates attendance research](projects/pirates-attendance.md) | How are star players and promotions associated with attendance? | Sports economics, regression analysis, and communicating business implications |

## Featured: NFL touchdown probabilities

The NFL project combines player usage, red-zone opportunities, team context, and historical outcomes to estimate touchdown probabilities. It compares models over time, saves pregame forecasts, and grades them against completed games. Optional market comparisons are separate from model training.

[Read the project](projects/nfl-touchdowns.md) · [View the notebook](notebooks/nfl_touchdown_model.ipynb)

## Background

- **Berry College:** B.S. with Honors, Data Analytics & Economics; expected December 2026.
- **Research:** Sports economics research with Professor E. Frank Stephenson and an honors thesis on NIL and MLB draft outcomes.
- **Leadership:** Game Operations Supervisor for Berry Athletics and member of the men's tennis team.
- **Tools:** Python, R, Power BI, and Microsoft Excel.

## Running the projects

Download a notebook and open it in Google Colab with a CPU runtime. Read its settings before running all cells. Google Drive storage preserves downloaded data and forecast history between sessions. Optional odds fetching is off in these portfolio copies; it requires your own `ODDS_API_KEY` in Colab Secrets.

The notebooks contain the implementation; project pages explain the approach and limitations. Saved outputs have been cleared. No verified performance figures or profitability claims are presented here. End-to-end runs require external data services and have not been repeated for this portfolio edition.
