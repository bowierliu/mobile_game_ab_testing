# Cookie Cats A/B Testing Project

## Project Motivation

Cookie Cats is a popular mobile puzzle game developed by Tactile Entertainment. In this game, players must connect tiles of the same color to clear the board and win levels. As players progress, they encounter gates that either force them to wait or make in-app purchases to continue. This project aims to analyze the results of an A/B test where the first gate in Cookie Cats was moved from level 30 to level 40. The primary objective is to understand the impact of this change on player retention and game rounds.

## Libraries Used

- **NumPy**: For numerical operations.
- **Pandas**: For data manipulation and analysis.
- **Seaborn**: For creating visualizations.
- **Matplotlib**: For plotting data.
- **Scipy**: For statistical testing (Shapiro, Levene, Mann-Whitney U tests).
- **Warnings**: To handle warning messages.

## Data

The dataset contains player behavior in Cookie Cats, focusing on:
- `userid`: Unique identifier for each player.
- `version`: A/B testing group (`gate_30` or `gate_40`).
- `sum_gamerounds`: The total number of game rounds played by the user.
- `retention_1`: Indicates whether the player returned to the game one day after installing.
- `retention_7`: Indicates whether the player returned to the game seven days after installing.

### Data Loading

A custom `load` function is used to load the dataset (`cookie_cats.csv`) and provide an overview of the data, such as:
- The number of rows and columns.
- Data types of each column.
- Presence of missing values (there were no missing values in this dataset).

### Data Summary

- **Unique Users**: 90,189 users in total.
- **Game Rounds**: The average user played approximately 51.87 rounds, with a maximum of 49,854 rounds.
- **Retention**: Retention data shows that around 55% of players did not return the next day (`retention_1`), and 81% did not return after seven days (`retention_7`).

## Data Exploration and Visualization

- **Game Rounds**: We explored the distribution of game rounds between the two groups (`gate_30` and `gate_40`) and visualized the data using histograms and box plots. Outliers were identified and removed to better understand the distribution of game rounds.
  
- **User Activity**: The majority of users played very few game rounds, and the number of users decreased as the levels progressed. We investigated how many users reached level 30 and 40 and found that 642 users reached level 30, while 505 reached level 40.

### Retention Analysis

We analyzed player retention data:
- **Retention Day 1**: 55% of players did not return the next day after installing the game.
- **Retention Day 7**: 81% of players did not return after 7 days.
- **Retention Summary**: Players who stayed engaged for 7 days tended to play significantly more game rounds.

## A/B Testing

### Assumptions for A/B Testing

1. **Normality**: We applied the Shapiro-Wilk test to check if the data follows a normal distribution.
2. **Homogeneity of Variances**: If the data was normally distributed, we applied Levene's Test to check for equal variances between groups.
3. **T-Test or Mann-Whitney U Test**: Based on the test results, we chose the appropriate statistical test (parametric or non-parametric) to compare the two groups.

### Testing Steps

- **Define Control and Test Groups**: The A/B test groups are labeled as "A" for `gate_30` and "B" for `gate_40`.
- **Shapiro Test**: Normality was rejected for both groups, so we used a non-parametric test (Mann-Whitney U) for further analysis.

### Results

The Mann-Whitney U Test was conducted to compare the two groups:
- **p-value**: 0.0509
- **Conclusion**: The test failed to reject the null hypothesis, meaning there was no statistically significant difference between the groups (`gate_30` and `gate_40`) in terms of game rounds played.

## Conclusion

This project analyzed the impact of moving the first gate from level 30 to level 40 in the Cookie Cats game using A/B testing. Our analysis showed that:
- There is no significant difference between the two groups in terms of game rounds played.
- Retention rates are low, and Tactile Entertainment should focus on understanding why players churn early in the game and explore strategies like adjusting game difficulty or offering rewards to improve retention.

## How to Run the Project

1. Clone this repository to your local machine.
2. Install the required dependencies using:
   ```bash
   pip install -r requirements.txt
