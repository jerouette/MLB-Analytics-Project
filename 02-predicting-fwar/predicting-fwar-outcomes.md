# Predicting fWAR: Project Outcomes

## Project Overview

This project examines how traditional baseball statistics, advanced sabermetric measures, and Statcast metrics explain variation in FanGraphs Wins Above Replacement (fWAR).

The analysis uses 1,377 qualified hitter-season observations and progresses from simple linear regression to multiple regression, multicollinearity analysis, diagnostics, nonlinear effects, and interactions.

The primary goal is to identify which statistics are most strongly associated with fWAR while evaluating model fit, interpretability, and limitations.

## 1. Simple Linear Regression

### Traditional Statistics

Eight traditional statistics were modeled individually: BA, HR, RBI, R, SB, OPS, BB%, and K%. All eight had statistically significant relationships with fWAR, although their explanatory power varied considerably.

OPS was the strongest traditional predictor, with an R² of 0.5724, followed by runs scored at approximately 0.5236. BA explained 33.2% of the variation, HR 23.0%, and RBI 22.2%. BB% explained 12.7%, SB 9.6%, and K% only 1.1%.

Most coefficients were positive, while K% had a negative coefficient.

These results show that OPS and runs scored provide the strongest individual traditional-statistic relationships with fWAR. However, statistical significance alone does not indicate strong explanatory power.

### Advanced Sabermetric Statistics

Six advanced measures were modeled individually: wOBA, wRC+, ISO, Off, BsR, and Def. All six had statistically significant relationships with fWAR.

Off was the strongest individual predictor across all three statistical groups, with an R² of 0.7357 and adjusted R² of 0.7355. It explained approximately 73.6% of the variation in fWAR.

wRC+ followed with an adjusted R² of 0.6308, while wOBA reached 0.5994. ISO explained 27.2%, Def 15.0%, and BsR 11.0%.

Broad measures of offensive contribution were more strongly associated with fWAR than isolated baserunning or defensive measures when modeled individually.

### Statcast Statistics

Nine Statcast and expected-performance variables were modeled individually. All showed statistically significant relationships with fWAR, but their explanatory power was generally weaker than the strongest traditional and advanced measures.

xwOBA was the strongest Statcast predictor, with an R² of 0.3505. xSLG followed at 0.2647, xBA at 0.2089, and xISO at 0.1757.

Barrel%, average exit velocity, Hard-Hit%, Sweet Spot%, and launch angle explained considerably less variation.

### Simple Model Takeaways

The strongest individual predictors were Off, wRC+, wOBA, OPS, and xwOBA.

These results established a starting point for multiple regression and showed that Statcast metrics do not automatically outperform traditional or advanced statistics when modeled individually.

## 2. Multiple Regression

Multiple regression evaluated several predictors simultaneously, allowing each coefficient to represent its association with fWAR after accounting for the other variables in the model.

### Traditional Model

The traditional model included BA, HR, RBI, R, SB, OPS, BB%, and K%.

It produced an R² of 0.7097 and adjusted R² of 0.7080, explaining approximately 71.0% of the variation in fWAR. RMSE was 1.068 and MAE was 0.841.

Runs scored, stolen bases, OPS, and K% remained statistically significant. BA, HR, RBI, and BB% were no longer significant after accounting for the other predictors.

This suggests that several traditional statistics contain overlapping information about player value.

### Advanced Sabermetric Model

The sabermetric model included wRC+, Off, BsR, Def, and Age.

It produced an R² and adjusted R² of approximately 0.9897, with RMSE around 0.201 and MAE around 0.164.

This was substantially stronger than the traditional model. However, the extremely high fit requires caution because Off and Def are closely connected to the components used to calculate fWAR.

The model therefore explains existing fWAR values exceptionally well but does not establish equally strong forecasting ability.

### Statcast Model

The Statcast model combined expected-performance and contact-quality measures.

It produced an R² of 0.3853 and adjusted R² of 0.3826, with RMSE of 1.5547 and MAE of 1.2359.

The combined Statcast measures explained more variation than several individual contact-quality statistics, but the model performed substantially worse than the advanced sabermetric model.

### Combined Model

The combined model included OPS, runs scored, stolen bases, K%, wRC+, Off, BsR, Def, and xwOBA.

It produced:

- R²: 0.9939

- Adjusted R²: 0.9938

- RMSE: 0.1555

- MAE: 0.1246

The actual-versus-predicted plot showed predictions closely aligned with observed fWAR.

However, the model's exceptionally high fit reflects, in part, the inclusion of Off and Def, which are closely related to fWAR's construction. The results demonstrate strong explanatory fit within the dataset rather than proven future forecasting accuracy.

## 3. Multicollinearity and Diagnostics

### Multicollinearity

The correlation matrix and Variance Inflation Factor (VIF) analysis identified substantial overlap among predictors in the combined model.

The largest VIF values were:

- Off: 93.96

- wRC+: 83.73

- OPS: 10.94

- BsR: 5.10

Off and wRC+ correlated at approximately 0.974, OPS and wRC+ at 0.944, and OPS and Off at 0.929.

These results indicate serious multicollinearity among several offensive measures. Although the model achieved excellent overall fit, individual coefficients may be unstable or difficult to interpret because predictors contain similar information.

### Regression Diagnostics

Diagnostic plots were reviewed for the simple models and the strongest models from each statistical group: OPS, Off, and xwOBA.

Some residual and Scale-Location plots showed modest patterns that could indicate changes in residual variance. These patterns were not considered severe enough to invalidate the models as baseline comparisons, but they supported cautious interpretation of regression assumptions.

For the combined model, Cook's Distance, leverage, and standardized residuals identified potentially influential observations.

Observation 1294 had the largest Cook's Distance, approximately 0.0189. Observation 1157 had the highest leverage, approximately 0.0353, while observation 851 had the largest absolute standardized residual at approximately 3.93.

These observations were retained because there was no clear evidence that they were data errors. They may represent legitimate exceptional player seasons.

## 4. Nonlinear Effects

A nonlinear model added Age and Age² to the combined model to evaluate whether the relationship between age and fWAR followed a curve.

The model retained an R² of approximately 0.9939. RMSE decreased only slightly from 0.15548 to 0.15537, while MAE decreased from 0.12463 to 0.12447.

Neither Age nor Age² was statistically significant.

The quadratic age effect therefore provided no meaningful improvement in model performance and was not necessary based on the results.

## 5. Interaction Effects

Three interactions were evaluated: Position × Def, OPS × Def, and Off × BsR.

### Position x Def

The Position × Def model produced the strongest results among the interaction models:

- R²: 0.9941

- Adjusted R²: 0.9940

- RMSE: 0.1528

- MAE: 0.1219

The overall interaction was statistically significant, and several position-specific interactions, including those for second basemen, third basemen, and shortstops, were significant.

This suggests that the relationship between defensive value and fWAR differs across positions.

The model also had the lowest AIC and BIC among the tested interaction models. However, its improvement over the combined model was relatively small, and its high fit still reflects the relationship between defensive value and fWAR's construction.

### Other Interactions 

OPS × Def did not meaningfully improve the combined model, and its interaction term was not statistically significant (p = 0.563).

Off × BsR was also not significant (p = 0.799) and provided no meaningful improvement.

Position × Def was therefore the most useful of the tested interactions, while the other two were excluded.

## 6. Main Takeaways

  1. Off was the strongest individual predictor: It explained approximately 73.6% of the variation in fWAR, followed by wRC+, wOBA, and OPS.

  2. OPS and runs scored were the strongest traditional statistics: They provided more explanatory power than most individual traditional measures.

  3. xwOBA was the strongest Statcast predictor: However, Statcast-only regression performed substantially worse than the advanced sabermetric model.

  4. Multiple regression improved explanatory power: Combining predictors captured additional information, but overlapping statistics complicated coefficient interpretation.

  5. The combined model achieved an R² of approximately 99.4%: This should not be interpreted as equivalent future forecasting accuracy because Off and Def are closely tied to fWAR's calculation.

  6. Multicollinearity was substantial: Off, wRC+, and OPS had particularly high VIF values.

  7. Age² did not meaningfully improve the model: The nonlinear age effect was not statistically significant.

  8. Position × Def was the strongest tested interaction: Its results suggest that defensive value relates differently to fWAR across positions.

  9. Potentially influential observations were retained: They were not removed without evidence of data errors.

## Scope and Limitations

The analysis focuses on qualified hitter-season observations and evaluates relationships with fWAR within the available dataset.

The results are associations rather than causal explanations. The exceptionally high fit of the advanced and combined models must be interpreted cautiously because some predictors, particularly Off and Def, are closely connected to fWAR's construction.

The reported errors are based on the fitted observations and do not establish how accurately the models would predict future seasons or unseen players. Multicollinearity also limits the interpretation of individual coefficients.

Future work could evaluate a held-out test set and compare models using a smaller group of predictors that are less directly tied to fWAR's calculation.

## Conclusion

The project shows that the strongest relationships with fWAR depend on whether statistics are evaluated individually or together.

Off was the strongest simple predictor, while the advanced sabermetric model explained substantially more variation than the traditional and Statcast-only models. The combined model and Position × Def interaction produced the closest fits to observed fWAR.

However, these results primarily demonstrate how well the models explain existing player value, not how accurately they forecast future performance.

The main conclusion is that strong model fit must be balanced with interpretability, predictor overlap, and independent evaluation. Future modeling should focus on selecting meaningful predictors and testing performance on data not used to fit the models.
