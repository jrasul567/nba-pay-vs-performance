# NBA Pay vs. Performance (2021-22 Season)

**Are NBA teams paying for performance?** This project combines salary, player stats, draft history and injury data for 540 players to see what actually lines up with pay, and where teams may be finding (or missing) value.

## Key Findings

**Salary tracks scoring, but minutes explain a lot of it.** Salary has a strong correlation with points per game (0.74), followed by rebounds (0.64) and assists (0.62). For players with 20+ games, the points correlation is 0.67, but it drops to 0.46 when scoring is measured per 36 minutes. Highly paid players score more largely because they play more.

**Draft position still matters years later.** Draft pick correlates with salary at −0.66 and with points at −0.54 (earlier picks earn and score more).

| Draft group | Median salary | Median points | Median minutes |
|---|---|---|---|
| First round | $6.35M | 10.4 | 24.8 |
| Second round | $2.06M | 5.8 | 16.3 |
| Undrafted | $0.53M | 4.0 | 12.8 |

**Higher paid players land on the injured list more often.** Injury placements correlate with salary at 0.46 overall and 0.33 for players with 20+ games. Average placements rise from 1.07 for players earning under $2.5M to 3.32 for players earning $30M+. Even among players with similar minutes, higher paid players averaged 2.29 placements vs 1.33 for lower paid players.

**Age has almost no relationship with salary** (correlation 0.01).

## Recommendations

1. **Evaluate players per minute, not per game.** Per game stats reward playing time, which favors players who are already paid well.
2. **Look for value in the second round and undrafted pool.** These players cost a fraction of first rounders and some produce well in limited minutes.
3. **Plan roster depth around big contracts.** Top earners are placed on the injured list more often, so teams should budget for reliable backups.

## Data

Three Kaggle datasets, downloaded in the notebook with `kagglehub`:

* [NBA Player Stats and Salaries 2010-2025](https://www.kaggle.com/datasets/ratin21/nba-player-stats-and-salaries-2010-2025) for stats and salaries
* [NBA Players Data](https://www.kaggle.com/datasets/justinas/nba-players-data) for draft round and pick
* [NBA Injury Stats 1951-2023](https://www.kaggle.com/datasets/loganlauton/nba-injury-stats-1951-2023) for injured list placements

Players were matched across files by name, using Python's `difflib` for close matches. Undrafted players are coded as round 3, pick 61.

## Limitations

* One season only, and 2021-22 was affected by COVID protocols, which likely inflated injured list placements.
* 65 players in the draft file were not found in the stats file, 38 of them because of suffixes or initials in their names.
* Injury data counts placements, not games missed.
* Salaries appear to be inflation adjusted (about 16% above actual figures).
* Correlation does not show causation, and some groups are small.

## Repository Structure

| File | Description |
|---|---|
| `nba_pay_vs_performance.ipynb` | Main analysis: cleaning, merging, correlations and charts. Creates `cleaned_data.csv`. |
| `nba_data_explorer.ipynb` | Menu driven tool for exploring the cleaned data (summaries, counts, group averages, crosstabs, scatter plots). |
| `requirements.txt` | Python packages used. |

## How to Run

```
pip install -r requirements.txt
jupyter notebook
```

Run `nba_pay_vs_performance.ipynb` first. It downloads the data through `kagglehub` and saves `cleaned_data.csv`, which the explorer notebook reads.

## Tools

Python, pandas, NumPy, matplotlib, Jupyter
