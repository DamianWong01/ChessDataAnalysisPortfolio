# Are there variations in opening popularity and success rates among different player ratings?
##### Author: Damian Wong

##### Date: 02/10/2023

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

To prepare the data, I selected only the relevant columns.

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

## 3. Process
In this section, we look into the initial exploration of the dataset. Exploratory Data Analysis (EDA) serves as the foundation for the subsequent analyses and visualizations.

### Distribution of Average Player Ratings
To look at the rating distribution, I made a histogram of the average player rating against the frequency of played games.
```{r}
ggplot(cleaned_data, aes(x = avg_player)) +
  geom_histogram(binwidth = 50, fill = "blue", color = "black") +
  labs(title = "Distribution of Average Player Ratings",
       x = "Average Player Rating",
       y = "Frequency")
```
<img width="686" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/4d983374-0d70-432c-991a-fcc41721a69a">

From this, we see that the peak rating is 2300. We also see that the minimum rating in the dataset is 1500 and the maximum is 2500.

## 4. Analyze
- [< 2000]
- [2000-2200]
- [> 2200]
- [Across Ratings]

### < 2000
In this section, we delve into the analysis of chess openings among players with ratings below 2000.

<img width="682" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/b7c84d79-3096-4b47-ae6a-96065261b4a5">

**Top 10 Most Popular Openings**: I identified the top 10 most frequently played openings within this rating category. These openings had the highest total number of games played. The openings, such as the Spanish Game, Steinitz Defence and the Sicilian Defence, Smith-Morra Gambit, stood out as favorites among this group of players.

**Win Rates**: I calculated win rates for each of the top 10 openings. This analysis provided insights into which openings tend to lead to more victories for players in this rating range. Take not that in this rating category, each opening has a higher win rate for either black or white compared to higher rating categories. This is likely due to lower accuracy in their play by players in this categories.

### 2000-2200
<img width="692" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/3c063508-33f8-4eb8-abae-4bd89b05b622">

**Top 10 Most Popular Opening**s: Similar to the < 2000 rating category, I identified the top 10 openings that were most frequently played by players in this range. These openings, such as several variations of the Sicilian Defence and an increasing number of games played with the Queen's pawn first, were prominent choices among higher-rated level players.

**Win Rates**: I analyzed the win rates for each of the top 10 openings within this category. As we can see, win rates are more even compared to the lower rating category. This is likely due to players at this level being more familiar with opening theory.

### > 2200
<img width="690" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/b6ba2341-5ec2-4bf5-8005-d41229e47a7c">

Top 10 Most Popular Openings: I identified the top 10 openings that were most frequently played by players in the 2200+ rating category. These openings, such as multiple variations of the Sicilian Defence and openings such as the King's Indian Defence, were particularly prominent among master-level players.

Win Rates: In this rating category, the percentage of draws increase compared to the other rating categories. This is likely due to these players having more knowledge on chess and the latest opening theory and ideas.

### Across Ratings
<img width="681" alt="image" src="https://github.com/DamianWong01/ChessDataAnalysisPortfolio/assets/88598436/49d5cbe5-8e7c-4602-8a76-97b561924896">

The analysis of opening popularity and success rates among different player rating categories offers a comprehensive view of chess strategies at various skill levels. Here are the key findings:

Overall Trends: Across all three rating categories, certain openings consistently appeared in the top 10 most frequently played openings, such as the Sicilian Defence. However, different variations were popular at certain levels, suggesting that there may be some difficulty for lower rated players to understand higher level concepts in the Sicilian Defence.

Divergence in Win Rates: While some openings were popular across all categories, their win rates varied. The Spanish Game, Steinitz Defence and the Queen's Gambit Declined, Marshall Defence both had an overwhelming higher win rate for white in the lower rating category, suggesting that players with the black pieces in this category should avoid playing these openings without a thorough understanding of the opening and its nuances. 

Strategic Considerations: Understanding the differences in opening popularity and success rates can help players tailor their strategies. Novice players might focus on openings with high success rates in the < 2000 category.

#### [Interactive Scatterplot](http://rpubs.com/damianw189/ChessDataAnalysisPortfolio)
The interactive scatterplot provides a dynamic visual representation of the relationship between player ratings and the number of games played with each opening. Users can explore the data by hovering over points to see opening names and win rates.

By interacting with the scatterplot, users can gain insights into the distribution of openings across player ratings. It becomes apparent which openings are popular at different skill levels and how they correlate with player ratings.

For the scatterplot, click [HERE](http://rpubs.com/damianw189/ChessDataAnalysisPortfolio).

## 5. Share 
Data Visualization
To effectively share my findings and insights, I created a series of data visualizations that highlight the relationships between chess opening popularity, success rates, and player ratings. These visualizations provide a clear and intuitive way to explore the data and understand the trends:

1. Top 10 Opening Popularity: I created bar charts for each player rating category, showcasing the top 10 most frequently played openings. These charts reveal which openings are favored by players in each skill range.
2. Win Rates per Opening: In the same player rating categories, I visualized the win rates for each of the top 10 openings. The bar charts display the distribution of wins, draws, and losses for each opening, offering insights into their performance.
3. Interactive Scatterplot: I developed an interactive scatterplot that allows users to explore the relationship between player ratings, the number of games played with each opening, and win rates. Users can hover over data points to view opening names and win rates, enabling a dynamic exploration of the data.

Documentation
To ensure transparency and reproducibility, I documented all of the data analysis process using R Markdown. The R Notebook contains detailed explanations of data cleaning, exploratory data analysis, and the creation of visualizations. Users can refer to this documentation to understand our methodology and reproduce our analysis

## 6. Act
**Chess Enthusiasts**
For chess enthusiasts, this analysis provides valuable insights into the world of chess openings at different skill levels. Based on my findings, players can make more informed decisions about which openings to explore and master. Novices can focus on openings with high success rates in the < 2000 rating category, while advanced players may find inspiration in the preferences of 2200+ rated players.

**Chess Educators**
Chess educators and coaches can also use this analysis to tailor their teaching strategies. They can recommend openings that align with their students' skill levels and help them understand the nuances of each opening's performance. This data-driven approach to chess instruction can enhance the learning experience for students of all levels.
