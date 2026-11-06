# MLB Value Diagnostics: Project Outcomes

## Project Overview

This project examines outliers and correlations in the MLB hitter-season dataset used throughout the baseball analytics portfolio. The goal is to identify extreme observations, understand relationships among performance statistics, and evaluate how player value and salary are associated with different variables.

The analysis uses the 1.5 × IQR rule to identify potential outliers and Pearson correlations to examine linear relationships. These analyses are descriptive and do not establish causation.

## 1. Outlier Analysis

### Method and Findings

Potential outliers were identified using the 1.5 × IQR rule. Standardized boxplots were also used to compare the distributions of numeric variables on a common scale. Standardization was only used for visualization and did not change the original data.

Stolen bases had the most potential outliers, with 41, followed by OPS (33), Off (30), xwOBA and wRC+ (27 each), and Hard-Hit Percentage (26). These results show that extreme observations were common among offensive, Statcast, and value-related statistics.

Potential outliers were not automatically treated as errors. MLB player seasons can contain unusually high or low values that are legitimate and relevant to the analysis.

### Salary and WAR Extremes

Salary had 22 potential outliers. The median salary was $5.2 million, with the middle 50% ranging from $765,000 to $13 million. The highest salaries included Shohei Ohtani at $70 million in 2024 and 2025, Juan Soto at $61.875 million in 2025, and Aaron Judge at $40 million in 2024 and 2025.

These observations represent the upper end of the salary distribution rather than necessarily indicating data errors. Lower-paid players also recorded strong seasons, including Kris Bryant's 6.10 WAR at a $507,500 salary in 2015.

WAR had 20 potential outliers, with a median of approximately 2.76 and an interquartile range of 1.54 to 4.04. The highest seasons included Judge's 11.33 WAR in 2024, Judge's 11.08 in 2022, Bobby Witt Jr.'s 10.49 in 2024, and Mookie Betts' 10.19 in 2018. Chris Davis recorded the lowest WAR at -2.54 in 2018.

Outlier takeaway: Extreme salary and performance observations were retained because they can represent legitimate player seasons. Their potential influence was evaluated separately through regression diagnostics rather than removing them solely because they were flagged.

## 2. Correlation Analysis

### Overall Relationships

Pearson correlations showed strong relationships among statistics measuring similar aspects of offensive performance.

OPS correlated with wOBA at 0.990, SLG at 0.958, and wRC+ at 0.944. wOBA also correlated with wRC+ at 0.967 and Off at 0.950.

Statcast measures showed similar overlap. xISO correlated with xSLG at 0.947, Barrel Percentage with xISO at 0.946, and Hard-Hit Percentage with average exit velocity at 0.938. Expected statistics also correlated with their traditional counterparts: xBA and BA had a correlation of 0.791, while xwOBA and wOBA had a correlation of 0.845.

Batted-ball measures showed strong relationships with launch angle. Groundball Percentage correlated with average launch angle at -0.955, while Flyball Percentage correlated with launch angle at 0.834.

Player characteristics were also related. Service Time and Age correlated at 0.861, while Games and Plate Appearances correlated at 0.816.

### Correlations with WAR

WAR was most strongly associated with overall offensive value measures:

- Off: 0.858

- wRC+: 0.794

- wOBA: 0.774

- OPS: 0.757

- Runs: 0.724

Among Statcast measures, xwOBA had the strongest correlation with WAR at 0.592, followed by xSLG at 0.515 and xBA at 0.458.

Base salary had a correlation of only 0.140 with WAR. This indicates that salary and performance, when measured by WAR alone, had a relatively weak linear relationship.

### Correlations with Log Salary

Salary showed a different pattern from WAR. Service Time had the strongest relationship with log salary at 0.777, followed by Age at 0.668.

Performance statistics had considerably weaker relationships. xwOBA had the strongest Statcast correlation at 0.272, followed by xSLG at 0.241. Among traditional statistics, RBI correlated at 0.206, BB% at 0.200, and wRC+ at 0.182.

WAR had a correlation of only 0.064 with log salary. These findings suggest that salary is more closely associated with career stage and labor-market factors than with any single performance statistic.

### Multicollinearity and Regression Implications

Many predictors had absolute correlations of at least 0.70. The strongest relationships occurred among overlapping offensive measures, including OPS, wOBA, wRC+, Off, and SLG. Similar overlap appeared among Statcast measures such as xSLG, xISO, and Barrel Percentage.

These relationships are important because including several highly correlated predictors in the same regression model can create multicollinearity and make individual coefficients more difficult to interpret.

The salary analysis also showed that Service Time and Age were much more strongly associated with log salary than WAR or most individual performance measures. This supports examining labor-market variables alongside performance when modeling player compensation.

Correlation alone does not determine predictor selection. Model fit, coefficient uncertainty, and multicollinearity diagnostics must also be considered.

## 3. Main Takeaways

  1. Potential outliers were common: Stolen bases, OPS, and Off had the most, while salary and WAR also contained extreme observations.

  2. Extreme observations were retained: High salaries and standout or negative WAR seasons can represent legitimate player outcomes.

  3. WAR was most strongly associated with offensive value: Off, wRC+, wOBA, OPS, and runs had the strongest reported relationships.

  4. Salary was more closely associated with career stage: Service Time and Age had stronger correlations with log salary than most performance statistics.

  5. Predictor overlap was substantial: Highly correlated offensive and Statcast measures create potential multicollinearity in regression models.

  6. The analysis was descriptive: Correlations identify linear relationships but do not establish causation.

## Conclusion

The outlier and correlation analyses provide important context for the broader MLB value and salary projects. Extreme salary and performance observations were retained because they can represent valid player seasons and contribute meaningful information about differences in value and compensation.

WAR was most strongly associated with offensive value measures, while log salary was more closely associated with Service Time and Age than with most individual performance statistics. The analysis also identified substantial overlap among traditional offensive and Statcast predictors, highlighting the importance of careful variable selection and regression diagnostics.

Together, these findings support the portfolio's broader conclusion that MLB player value and compensation are related to both on-field performance and labor-market factors. They also reinforce the distinction between descriptive relationships and causal explanations.
