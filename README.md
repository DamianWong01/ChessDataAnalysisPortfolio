# Are there variations in opening popularity and success rates among different player ratings?
##### Author: Damian Wong

##### Date: September 25, 2023

#

_The case study follows the six step data analysis process:_

### ❓ [Ask](#1-ask)
### 💻 [Prepare](#2-prepare)
### 🛠 [Process](#3-process)
### 📊 [Analyze](#4-analyze)
### 📋 [Share](#5-share)
### 🧗‍♀️ [Act](#6-act)

## 1. Ask
Task : In Chess, are there variations in opening popularity and success rates among different player ratings?

## 2. Prepare
Data Soucre: Filtered all games from lichess to only keep games by players rated 2400+ against players rated 2200+, excluding bullet games.
https://database.nikonoel.fr/ from https://database.lichess.org/

Positive aspects of the dataset:
* Relevance: By focusing on games played by top-rated players, I am likely to capture high-level opening theory and strategies, which can be valuable for players interested in the latest developments in chess.
* Quality of Play: Strong players tend to play high-quality chess, and their games can provide insights into how strong opponents handle various openings in practice.

The dataset has limitations:
* Limited Sample Size: Filtering games to such specific rating ranges may reduce the size of your dataset significantly. Be mindful of potential limitations due to a smaller sample size, which could affect the statistical significance of your findings.
*   From December 2021 on, the author of the dataset only kept games of 2500+ vs. 2300+ rated players.

## 3. Process
Using {chess} is an opinionated wrapper for R around python-chess: https://github.com/curso-r/chess
```{R}
install.packages("chess")
```

## 4. Analyze

## 5. Share 

## 6. Act
