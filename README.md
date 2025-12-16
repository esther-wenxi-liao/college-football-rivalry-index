# 🏈 Reproducible Rivalry: Quantifying UGA–Alabama Football Intensity

## Overview
This project builds a reproducible analytics pipeline to quantify rivalry intensity in the historic University of Georgia vs. University of Alabama football matchup. Using officially sourced game statistics, I introduce a custom **Rivalry Intensity Index (RII)** that captures not only final scores, but also competitive pressure, offensive production, turnovers, and game stakes.

The project begins with a focused analysis of recent matchups and is designed to scale to a broader historical dataset, enabling trend analysis across seasons and eras.

---

## Motivation
UGA and Alabama share one of the most competitive rivalries in college football, with frequent high-stakes matchups in SEC Championships and the College Football Playoff. With another SEC Championship matchup approaching, this project aims to move beyond wins and losses and answer a deeper question:

**How intense are these games, and how has that intensity changed over time?**

---

## Data Sources
All game data is sourced from **official University of Georgia Athletics records**:

- UGA Football Opponent History vs. Alabama  
  https://georgiadogs.com/sports/football/opponent-history/university-of-alabama/28

This page documents every matchup between UGA and Alabama from **1895 to 2025**.  
For the initial model, I curated a subset of recent games with detailed box-score statistics. The pipeline is designed to incorporate additional historical games as more data is added.

---

## Dataset Structure
Each game is represented as a single observation with structured features, including:

- `season`
- `game_date`
- `game_type` (Regular Season, SEC Championship, CFP National Championship)
- `uga_score`, `bama_score`
- `uga_total_yards`, `bama_total_yards`
- `uga_turnovers`, `bama_turnovers`

Additional features can be incorporated as the dataset expands (rankings, overtime flags, home/away indicators, etc.).

---

## Rivalry Intensity Index (RII)
The **Rivalry Intensity Index (RII)** is a composite metric designed to capture how competitive and chaotic a game feels, rather than simply who won.

The index combines four core components:

1. **Score Closeness**  
   Closer final scores indicate higher competitive tension.

2. **Offensive Production**  
   Total combined yards serve as a proxy for game pace and sustained action.

3. **Turnover Chaos**  
   Turnovers introduce volatility and momentum swings.

4. **Game Stakes**  
   Championship games receive additional weight to reflect higher pressure environments.

The result is a single interpretable score that allows meaningful comparison across games and seasons.

---

## Methods
The analysis pipeline follows a standard data science workflow:

1. Load curated game data into a structured DataFrame  
2. Enforce appropriate data types (dates, categorical variables)  
3. Perform feature engineering (point differential, RII calculation)  
4. Apply custom functions for analysis and ranking  
5. Aggregate results by game type  
6. Visualize rivalry intensity trends over time  

All steps are implemented in Python using `pandas` and `matplotlib`.

---

## Visualization
The project includes a line-chart visualization that tracks **Rivalry Intensity Index values across seasons**, with special labeling to distinguish high-stakes matchups such as:

- 2021 SEC Championship  
- 2021 CFP National Championship  

This visualization highlights how intensity peaks during postseason and championship environments.

---

## Repository Structure
reproducible-rivalry-uga-bama/

│

├── data/

│ └── uga_bama_stats.csv

│

├── src/

│ └── rivalry_index.py

│

├── figures/

│ └── uga_bama_rivalry_index.png

│

├── README.md

├── requirements.txt

└── .gitignore




---

## Reproducibility
To run this project locally:

```bash
pip install -r requirements.txt
python src/rivalry_index.py

```

This will:
load the dataset
compute the Rivalry Intensity Index
print summary outputs
generate the rivalry intensity visualization

---

### Future Work
Planned extensions for this project include:
Expanding the dataset to include additional modern-era matchups
Incorporating team rankings and overtime indicators
Learning index weights from data rather than fixed heuristics
Building an interactive dashboard for game-level exploration

---

### Acknowledgments
All statistics are derived from official University of Georgia Athletics records.
This project was developed as an independent analytics exploration of college football rivalry dynamics.


---

### ✅ What to do now
1. Go to your GitHub repo  
2. Open `README.md`  
3. **Paste everything above**  
4. Commit  

It will render **exactly** as intended.

If you want, next I can:
- tailor a **shorter public-facing README** vs an **academic version**
- add **badges**, screenshots, or charts
- help you write a **“Key Insights”** section once you add more data
- polish this for **grad admissions reviewers**

Just tell me the next step.
