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
Data Source: [High-Elo Games Chess Opening Dataset by MÖBIUS](https://www.kaggle.com/datasets/arashnic/chess-opening-dataset/)

Positive aspects of the dataset:
* Relevance: By focusing on games played by top-rated players, I am likely to capture high-level opening theory and strategies, which can be valuable for players interested in the latest developments in chess.
* Quality of Play: Strong players tend to play high-quality chess, and their games can provide insights into how strong opponents handle various openings in practice.

The dataset has limitations:
* Limited Sample Size: Filtering games to such specific rating ranges may reduce the size of your dataset significantly. Be mindful of potential limitations due to a smaller sample size, which could affect the statistical significance of your findings.
* The data is only till 2018 and there may have been new trends and improvements in opening theory.

## 3. Process
Read CSV files
```{r}
# Read the data file
data <- read.csv("high_elo_opening.csv")

# Clean the data file
columns_to_keep <- c(
  "opening_name",
  "side",
  "num_games",
  "ECO",
  "last_played_date",
  "avg_player",
  "perc_draw",
  "perc_white_win",
  "perc_black_win"
)

# Create a new dataset with only the relevant columns
cleaned_data <- data %>%
  select(all_of(columns_to_keep))
```
To look at the rating distribution, I made a histogram of the average player rating against the frequency of played games.
```{r}
ggplot(cleaned_data, aes(x = avg_player)) +
  geom_histogram(binwidth = 50, fill = "blue", color = "black") +
  labs(title = "Distribution of Average Player Ratings",
       x = "Average Player Rating",
       y = "Frequency")
```
<img width="686" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/4d983374-0d70-432c-991a-fcc41721a69a">

## 4. Analyze
- [< 2000]
- [2000-2200]
- [> 2200]
- [Across Ratings]

### < 2000
<img width="682" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/b7c84d79-3096-4b47-ae6a-96065261b4a5">


### 2000-2200
<img width="692" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/3c063508-33f8-4eb8-abae-4bd89b05b622">


### > 2200
<img width="690" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/b6ba2341-5ec2-4bf5-8005-d41229e47a7c">

### Across Ratings
<img width="681" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/49d5cbe5-8e7c-4602-8a76-97b561924896">

To look at the distribution of openings against the frequency they are played at and the average rating of the players of that particular opening, I have made an interactive scatterplot graph.
<img width="357" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/1b105d66-9b81-4dc5-a270-ada10b974a5c">

## 5. Share 

## 6. Act
