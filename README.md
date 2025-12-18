# 🏈 Reproducible Rivalry: Quantifying UGA–Alabama Football Intensity

<div align="center">
  <img src="https://ats.io/wp-content/uploads/2025/09/alabama-vs-georgia-prediction-and-preview.png" width="760" />
  <br />
</div>

## Overview

This project builds a reproducible analytics pipeline to quantify rivalry intensity in the historic University of Georgia vs. University of Alabama football matchup. Using officially sourced game statistics, I introduce a custom **Rivalry Intensity Index (RII)** that captures not only final scores, but also competitive pressure, offensive production, turnovers, and game stakes.

The project begins with a focused analysis of recent matchups and is designed to scale to a broader historical dataset, enabling trend analysis across seasons and eras.

---

## Motivation

Being a Georgia Bulldawg means growing up with moments that are bigger than the scoreboard.
UGA vs. Alabama is not just another matchup. It is where seasons are defined, legacies are questioned, and emotions swing with every possession.
With another SEC Championship game approaching, I wanted to look beyond wins and losses and ask a deeper question:

**How intense are these games, and how has that intensity evolved over time?**

---

## Data Sources
All game data is sourced from **official University of Georgia Athletics records**:

- UGA Football Opponent History vs. Alabama  
  https://georgiadogs.com/sports/football/opponent-history/university-of-alabama/28

This page documents every matchup between UGA and Alabama from **1895 to 2025**.  

This model was originally built ahead of the 2025 SEC Championship using a curated subset of recent games with detailed box-score statistics. Following the conclusion of the championship, the pipeline is designed to remain continuously updatable, allowing newly played games and additional historical matchups to be seamlessly incorporated.
The goal is not a static snapshot, but a living model that evolves as this rivalry continues to be written.

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

## Model Overview & Methodology

This project introduces a custom **Rivalry Intensity Index (RII)** designed to quantify the competitive and emotional intensity of the historic UGA–Alabama football rivalry.

Rather than relying solely on wins and losses, the model focuses on **how the game was played**, capturing multiple dimensions that collectively reflect rivalry intensity.

### Core Components

For each game, the Rivalry Intensity Index is computed as a weighted combination of four factors:

1. **Score Closeness**  
   Measures how competitive the game was based on the final score margin. Games decided by smaller margins contribute more heavily to rivalry intensity.

2. **Offensive Production**  
   Captures the total offensive yards accumulated by both teams, reflecting pace, momentum swings, and sustained pressure throughout the game.

3. **Turnover Impact**  
   Accounts for turnovers committed by both teams. Turnovers introduce volatility and frequently shift momentum, amplifying emotional stakes.

4. **Championship Pressure Adjustment**  
   Applies an additional weight to games played in high-stakes environments such as SEC Championships or College Football Playoff matchups.

### Formal Definition

Let:

- ΔS = absolute score difference  
- Y = total offensive yards (UGA + Alabama)  
- T = total turnovers  
- C = championship indicator (binary or scaled weight)

The Rivalry Intensity Index for a single game is defined as:

$$
\text{RII} = w_1 \cdot f(\Delta S) + w_2 \cdot Y + w_3 \cdot T + w_4 \cdot C
$$

Where:

- \( f(\Delta S) \) is a score-closeness transformation that assigns higher values to tighter games  
- \( w_1, w_2, w_3, w_4 \) are tunable weights calibrated to balance competitiveness, production, volatility, and stakes  

The model is intentionally modular, allowing both weights and functional forms to be refined as additional historical data is incorporated.

---

## Example Results

Below is a sample visualization generated from the initial model using a subset of recent UGA–Alabama matchups. The chart illustrates how rivalry intensity fluctuates across games, highlighting the influence of close finishes and championship pressure.

<div align="center">
  <img width="1540" height="880" alt="uga_bama_rivalry_index" src="https://github.com/user-attachments/assets/a24bd273-48d6-42db-ae91-af78854b9068" />

  <br />
  <em>Figure 1. Rivalry Intensity Index (RII) across selected UGA–Alabama matchups</em>
</div>

While this model was originally constructed ahead of the most recent SEC Championship, it is designed to remain continuously updatable as new games are played and additional historical matchups are added.

---

## How to Run This Project

### Prerequisites

- Python 3.9 or higher  
- Required packages listed in `requirements.txt`

Install dependencies:

```bash
pip install -r requirements.txt

```

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
