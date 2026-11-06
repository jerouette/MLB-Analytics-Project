# MLB-Analytics-Project

## Overview

This project is a statistical analysis of Major League Baseball player performance, player value, and player salary. The main goal is to better understand what statistics are associated with player value and how player performance and other factors relate to MLB compensation.

The project uses player-season data from the 2015 through 2025 MLB seasons, excluding the 2020 season because of the shortened 60-game schedule. The analysis focuses on qualified hitters and combines traditional offensive statistics, advanced sabermetrics, Statcast metrics, player characteristics, organizational factors, and salary information.

The project is intended to demonstrate how statistical analysis can be applied to real baseball data to investigate player performance, value, and compensation. It also provides a collection of related projects that progress from data preparation and exploratory analysis to regression modeling, correlation analysis, and more advanced predictive methods.

The project is organized into five separate repositories. Each repository addresses a different research question while contributing to the overall goal of understanding MLB player value and compensation.

### Overall Research Question

How are MLB player performance, player value, and salary related, and how can statistical methods help explain and predict these relationships?

### Data

The dataset combines information from several publicly available baseball sources:
- Baseball Savant: Traditional offensive statistics and Statcast measurements.
- FanGraphs: fWAR, Off, BsR, Def, wRC+, wOBA, and other advanced metrics.
- Baseball Reference: Player information such as position, batting handedness, service time, and team.
- Spotrac: Player base salary information.

The final dataset contains 1,377 qualified hitter player-season observations and 50 variables.

The variables cover several different areas of player performance and characteristics. Traditional statistics include batting average, home runs, RBI, runs, stolen bases, strikeout percentage, walk percentage, slugging percentage, and OPS.

Advanced metrics include WAR, wRC+, wOBA, Off, BsR, Def, and ISO. Statcast variables include expected performance measures, exit velocity, launch angle, barrel percentage, hard-hit percentage, and other batted-ball characteristics.

The dataset also includes player characteristics and organizational variables such as age, service time, position, batting handedness, team, financial tier, hitter profile, and contract regime.

### Project Structure
#### 1. MLB Player Value Data

Research Question: How can information from multiple baseball sources be combined into a reliable dataset for analyzing MLB player performance, value, and salary?

##### Why It Matters

A reliable dataset is necessary before meaningful statistical analysis can be performed. MLB performance and salary information come from different sources, and combining them requires consistent player identification, season matching, variable definitions, and data quality checks.

This project provides the foundation for the other four repositories by creating a consistent player-season dataset that can be reused throughout the portfolio.

##### Methods

The project collects and combines information from Baseball Savant, FanGraphs, Baseball Reference, and Spotrac. It includes data preparation, duplicate and missing-value checks, variable organization, and exploratory data analysis.

The EDA examines summary statistics, salary and fWAR distributions, offensive and Statcast variable distributions, player characteristics, organizational categories, and yearly trends.

##### Results

The final dataset contains 1,377 qualified hitter player-season observations across the selected seasons, with no missing values or duplicate player-season records identified in the completed data checks.

The exploratory analysis showed that salary is strongly right-skewed, while fWAR is concentrated around the middle of the player-value distribution, with some negative seasons and a smaller number of exceptionally high-value seasons.

Average salary increased from approximately $7.05 million in 2015 to $10.03 million in 2025, while average WAR remained relatively stable. This provides an initial indication that salary and player performance do not necessarily change at the same rate over time.

#### 2. MLB Player Value / fWAR Modeling

Research Question: Which performance statistics and player characteristics best explain differences in MLB player value, as measured by fWAR?

##### Why It Matters

fWAR provides a broader measure of player value than any single offensive statistic. Examining its relationship with traditional statistics, advanced sabermetrics, and Statcast measures helps identify which variables are most strongly associated with overall player value.

This project also establishes a baseline for determining whether combining multiple statistics provides a better explanation of fWAR than examining individual predictors.

##### Methods

The analysis begins with simple linear regression models examining individual traditional offensive statistics, advanced sabermetric measures, and Statcast variables.

Multiple regression models then combine predictors from these groups to examine their relationships with fWAR while accounting for other variables.

The project also examines multicollinearity, regression diagnostics, nonlinear age effects, and interaction effects. Model performance is evaluated using R², adjusted R², RMSE, MAE, and residual standard error.

##### Results

Offensive Runs (Off) was the strongest individual predictor of fWAR, with an R² of approximately 0.736. Other strong individual predictors included wRC+, wOBA, and OPS.

The traditional offensive statistics generally explained less variation in fWAR than the strongest advanced sabermetric measures. Statcast measures were also associated with player value, although their individual explanatory power was generally lower than that of the strongest traditional and advanced metrics.

The multiple regression models showed that combining predictors improved explanatory power. However, the strongest models included statistics closely related to the construction of WAR itself, so their exceptionally high in-sample fit should not be interpreted as evidence of equivalent predictive performance for future player seasons.

#### 3. MLB Salary Modeling

Research Question: How do player performance and labor-market factors, including service time and contract regime, relate to MLB player salaries?

##### Why It Matters

MLB compensation is influenced by more than performance alone. Players can have different salaries depending on their service time, contract status, and position within the labor market.

Understanding these relationships helps explain why players with similar performance levels may receive substantially different salaries and why salary does not necessarily reflect a player's value in a given season.

##### Methods

The analysis examines salary relationships using simple and multiple linear regression, with particular attention to log-transformed salary because MLB salaries are strongly right-skewed.

The models include traditional offensive statistics, advanced sabermetrics, Statcast measures, WAR, age, service time, contract regime, financial tier, and position.

The project also evaluates nonlinear effects and interaction terms to examine whether the relationship between performance and salary changes across different stages of a player's career.

##### Results

Service time and contract regime were among the strongest factors associated with salary. The contract-regime model explained approximately 75% of the variation in log salary, demonstrating the importance of differences between pre-arbitration, arbitration, and free-agency compensation.

Performance measures also contributed to the salary models. Statcast expected-performance measures, particularly xwOBA, showed stronger individual salary relationships than several traditional statistics.

The multiple regression results indicated that contract regime, service time, WAR, and xwOBA were important salary-related factors. The nonlinear models further improved fit, particularly through the relationship between service time and salary.

Overall, the results suggest that MLB compensation reflects a combination of player performance and labor-market structure rather than performance alone.

#### 4. MLB Correlation and Outlier Analysis

Research Question: What relationships and unusual observations exist among MLB performance, player value, and salary variables?

##### Why It Matters

Many baseball statistics measure similar aspects of performance, meaning that some variables may contain overlapping information. Identifying these relationships helps explain why certain predictors perform similarly in regression models and why including highly related variables can create multicollinearity.

Outlier analysis also helps identify unusually high or low player-season observations that may influence statistical results.

##### Methods

The project uses correlation analysis to examine relationships among traditional offensive statistics, advanced sabermetrics, Statcast measures, player value, and salary.

Potential outliers are identified using the 1.5 × IQR rule. The analysis examines unusual observations in variables such as salary, WAR, OPS, stolen bases, and advanced performance measures.

The project focuses on understanding the structure of the data rather than automatically removing observations that fall outside typical ranges.

##### Results

Several groups of statistics showed strong relationships. For example, OPS and wOBA had a correlation of approximately 0.990, while wRC+ and wOBA had a correlation of approximately 0.967.

WAR was most strongly correlated with Off, wRC+, wOBA, and OPS. In contrast, the correlation between WAR and base salary was relatively weak.

Salary showed stronger relationships with service time and age than with individual performance statistics, reinforcing the importance of labor-market factors.

The outlier analysis identified unusual observations in salary and WAR, including exceptionally high-value seasons and negative-WAR seasons. These observations were retained because unusual values can represent legitimate player performance or compensation rather than data errors.

#### 5. MLB Value Beyond Linear Regression

Research Question: Can more advanced statistical models improve out-of-sample MLB salary prediction beyond standard linear regression?

##### Why It Matters

Linear regression provides an interpretable way to examine relationships between player characteristics and salary, but it may not capture every nonlinear relationship or interaction among variables.

Comparing additional modeling approaches helps determine whether more flexible methods improve salary prediction and whether predictive performance differs from the explanatory results of the earlier regression models.

##### Methods

The project uses a training and testing split to evaluate salary prediction outside the data used to fit the models.

The analysis compares multiple regression, best subset selection, stepwise regression, Ridge regression, LASSO regression, and random forest.

It also includes surplus value analysis, which compares actual player salaries with salaries predicted by the statistical models.

Model performance is evaluated using test-set R², RMSE, and MAE, with additional comparisons of model selection criteria where appropriate.

##### Results

The multiple regression benchmark provided a strong baseline for salary prediction, but random forest achieved the strongest test-set performance among the models examined.

Random forest produced a test R² of approximately 0.853, RMSE of 0.534, and MAE of 0.393. These results were better than the corresponding performance of the standard regression benchmark.

Ridge and LASSO did not improve prediction beyond the benchmark, while the stepwise models also produced weaker test performance.

The surplus value analysis identified player-seasons where actual salaries were substantially above or below model-predicted salaries. These differences provide a way to examine compensation relative to the model's expectations, although they should not be interpreted as definitive measures of whether a player was overpaid or underpaid.

Overall, the results show that more flexible models can improve salary prediction, while standard regression remains useful for interpreting the relationships between player characteristics and compensation.

### Overall Goal

The overall goal of this project is to develop a better understanding of how MLB player performance, player value, and compensation are related.

The project begins by building a reliable dataset and examining its characteristics through exploratory analysis. It then investigates player value using fWAR models, examines the factors associated with salary, studies correlations and unusual observations, and compares statistical methods for predicting player compensation.

By combining traditional statistics, advanced sabermetrics, Statcast measurements, player characteristics, organizational factors, and salary information, the project examines MLB player value and compensation from several different perspectives.

Ultimately, this project is intended to serve as a comprehensive MLB analytics portfolio that applies statistical analysis and regression methods to real baseball data while exploring both what makes a player valuable and what factors are associated with how much that player is paid.
