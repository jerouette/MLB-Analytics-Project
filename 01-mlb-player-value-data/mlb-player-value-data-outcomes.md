# MLB Player Value Data: Project Outcomes
## Overview

This repository establishes the dataset used throughout the larger MLB analytics project. The goal was to combine traditional baseball statistics, advanced sabermetrics, Statcast measurements, player characteristics, and salary information into one consistent player-season dataset.

The final dataset contains 1,377 qualified hitter player-season observations and 50 variables, covering the 2015 through 2025 seasons, excluding 2020. Each observation represents one qualified hitter in one season.

The exploratory analysis identified three important patterns: salary was strongly right-skewed, player performance varied across several dimensions, and average salary increased over time while selected performance averages remained relatively stable. These findings motivate the later projects examining player value, salary, and prediction.

## Dataset Construction and Preparation

The dataset combines information from four public sources:

- Baseball Savant: Statcast measurements and offensive performance information.

- FanGraphs: Advanced statistics, including WAR, wRC+, Offensive Runs (Off), Baserunning Runs (BsR), and Defensive Runs (Def).

- Baseball Reference: Player characteristics, including position, batting handedness, service time, and team.

- Spotrac: Base salary information.

The completed dataset includes traditional offensive statistics, advanced sabermetrics, Statcast and expected-performance metrics, player characteristics, salary, and categorical player or team profiles.

The sample was restricted to qualified hitters in each included season, helping make rate-based statistics more comparable by focusing on players with substantial playing time.

The primary data-quality checks found no missing values, duplicate player-season combinations based on MLBAMID and Year, or negative base salaries. The key fields used to identify player-seasons, including player ID, year, salary, and WAR, also had no missing values.

Two derived variables were created for later modeling:

- log_salary: The natural logarithm of base salary. This transformation reduces the influence of extremely high salaries and provides a more balanced response variable for salary regression. Raw salary was retained for interpretation in dollars.

- Contract_Regime: Players were classified by service time into Pre-Arbitration (less than 3 years), Arbitration (3 to less than 6 years), and Free Agency (6 years or more). The dataset contained 480 Pre-Arbitration, 430 Arbitration, and 467 Free Agency observations.

Predictor standardization was reserved for methods where it is appropriate, particularly Ridge and LASSO regression.

## Exploratory Data Analysis Outcomes

### Dataset Composition

The dataset contained players from several position groups, financial tiers, and hitter profiles. Outfielders were the largest position group, with 465 observations, while Balanced hitters accounted for 1,083 observations. Big Market, Mid Market, and Small Market teams contributed 480, 473, and 424 observations, respectively.

The average player-season included 605.45 plate appearances. Player age averaged 28.30 years, while service time averaged 4.58 years. These characteristics provide context for later analyses involving player performance, position, and compensation.

### Traditional and Advanced Performance

The typical observation recorded an average of 21.84 home runs, 75.22 RBI, 78.35 runs, and 10.03 stolen bases. Batting average averaged .270, while OPS averaged .790. Average walk rate was 8.84%, and average strikeout rate was 19.89%.

WAR averaged 2.91, with a median of 2.76, and ranged from -2.54 to 11.33. Most observations were concentrated between approximately 0 and 6 WAR, with the greatest concentration around 2 to 4. However, the distribution also included negative-value player-seasons and a smaller group of substantially higher-value seasons.

Average wRC+ was 112.54, above the league-average reference point of 100. Average wOBA was .340, while Offensive Runs averaged 10.01, Baserunning Runs averaged 0.25, and Defensive Runs averaged -1.56.

The performance distributions showed that traditional statistics such as home runs, runs scored, and OPS had right tails, while batting average was more concentrated around the middle of its range. The variation in Off, BsR, and Def also demonstrated that players contribute differently through offense, baserunning, and defense.

### Statcast Outcomes

The Statcast variables provided additional information about contact quality and expected performance.

Average exit velocity was 89.31 mph, while average launch angle was 12.84 degrees. Sweet Spot percentage averaged 34.12%, Barrel percentage averaged 8.65%, and Hard-Hit percentage averaged 39.53%.

Exit velocity and launch angle were relatively concentrated compared with some traditional statistics. Barrel percentage and Hard-Hit percentage also showed variation in contact quality across player-seasons.

Expected-performance statistics such as xBA, xSLG, xwOBA, and xISO complement recorded offensive results by providing additional information about the quality of contact. These variables were retained for later comparisons between traditional performance and underlying expected performance.

### Salary and WAR Distributions

Salary was the most strongly skewed of the main variables examined. Average base salary was approximately $8.23 million, compared with a median of $5.20 million. Salaries ranged from $500,000 to $70 million, with a standard deviation of approximately $8.69 million.

The difference between the mean and median, along with the salary histogram and boxplot, showed that a relatively small number of highly paid player-seasons increased the average salary.

The log-transformed salary distribution was more balanced because the transformation compressed the upper end of the salary range. This supports using log_salary in many salary regression models while retaining raw salary for dollar-based interpretation.

WAR was more concentrated than salary. Most observations fell between approximately 0 and 6 WAR, with the greatest concentration around 2 to 4. The distribution included negative values and a moderate upper tail.

Overall, salary varied more widely and was more strongly skewed than WAR. This distinction is important when examining the relationship between player value and compensation.

### Yearly Trends

The yearly analysis compared average base salary, WAR, OPS, wRC+, and xwOBA across the included seasons.

Average base salary increased from $7.05 million in 2015 to $10.03 million in 2025, an increase of approximately $2.98 million. Although the increase was not perfectly steady each year, the overall trend was upward.

In contrast, average WAR remained comparatively stable, ranging from 2.75 to 3.06. Average wRC+ ranged from 110.3 to 115.3, while average xwOBA ranged from .328 to .344.

OPS varied more noticeably across seasons, reaching .826 in 2019 and falling to .761 in 2022 before finishing at .767 in 2025.

These trends show that average salary increased substantially while the selected performance averages remained comparatively stable. This descriptive pattern does not establish why salaries increased or prove that performance was unrelated to compensation.

Instead, it motivates examining individual-level factors such as service time, contract regime, age, position, organizational context, and player performance in the salary-modeling repository.

## Main Takeaways

The main outcome of this repository is a combined, checked, and documented dataset that supports the other parts of the MLB analytics project.

  1. The dataset passed the primary quality checks. No missing values, duplicate player-season           combinations, or negative salaries were identified.

  2. Player performance varies across several dimensions. Traditional statistics, advanced               sabermetrics, and Statcast measures capture different aspects of offensive production and           player contribution.

  3. Salary is strongly right-skewed. The difference between mean and median salary supports using       log_salary in salary regression while retaining raw salary for interpretation.

  4. Average salary increased while selected performance averages remained relatively stable. This       motivates examining individual performance and labor-market factors rather than relying only        on yearly averages.

## Conclusion

This repository creates the data foundation for the full MLB analytics project by combining traditional statistics, advanced sabermetrics, Statcast measurements, player characteristics, and salary information into one player-season dataset.

The data-quality checks support its use for further analysis, while the exploratory results show that salary is highly skewed, player performance varies across several dimensions, and average salary increased over time even as selected performance averages remained comparatively stable.

These findings provide the starting point for the remaining repositories. The fWAR project examines which statistics explain player value, the salary project evaluates performance and labor-market factors associated with compensation, the diagnostics project investigates relationships and unusual observations, and the advanced modeling project compares approaches to salary prediction.

Together, these projects build on the dataset established here to examine what makes MLB players valuable and how performance and other factors relate to how much they are paid.
