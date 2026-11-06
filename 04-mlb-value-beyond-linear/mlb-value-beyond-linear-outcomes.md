# MLB Value Beyond Linear: Project Outcomes

## Project Overview

This project evaluates whether alternative modeling methods can improve MLB player salary predictions beyond the multiple regression model developed in the previous salary analysis. The focus is on out-of-sample prediction rather than relying only on how well a model fits its training data.

The analysis compared multiple regression, best subset selection, stepwise selection, Ridge regression, LASSO regression, Random Forest, and surplus value analysis. Salary was modeled on the log scale, and the dataset was divided into 1,101 training observations and 276 testing observations using an 80/20 split. The same split was used to compare predictive performance consistently.

The main finding was that Random Forest produced the strongest test-set predictions, outperforming the multiple regression benchmark across R², RMSE, and MAE. However, multiple regression remained useful for explaining how individual predictors relate to salary.

## 1. Multiple Regression Benchmark

The final multiple regression model from the previous salary project served as the benchmark. It included Service Time, WAR, Contract Regime, Age, xwOBA, wRC+, financial tier, Position, and a Service Time × WAR interaction.

The model achieved a training R² of 0.7808 and adjusted R² of 0.7775, with a residual standard error of approximately 0.643.

Service Time, Contract Regime, and xwOBA were important predictors. Relative to Pre-Arbitration players, the training-model coefficients for Arbitration and Free Agency were 1.5537 and 1.9703. Service Time had a positive coefficient of 0.0691, while xwOBA had a positive coefficient of 3.7116. The Service Time × WAR interaction was also positive and significant, with a coefficient of 0.0105 (p = 0.0002).

On the held-out test data, the benchmark produced:

- Test R²: 0.8266

- RMSE: 0.5800

- MAE: 0.4231

These metrics established the standard for evaluating the alternative methods. Higher test R² and lower RMSE and MAE indicate stronger predictive performance.

## Best Subset and Stepwise Selection

Best subset selection compared combinations of predictors using the training data. Adjusted R² favored a larger model, Mallows' Cp favored a model with approximately 12 predictors, and BIC selected a simpler five-predictor model containing PA, Hard-Hit Percentage, Service Time, Mid Market, and Small Market.

These differences demonstrate how model-selection criteria balance explanatory fit and complexity. BIC penalized additional predictors more strongly, producing a more interpretable model, but a smaller model does not automatically provide better predictions.

Three stepwise approaches were also examined: forward selection, backward elimination, and bidirectional selection. AIC guided the selection process.

Backward elimination and bidirectional selection produced the same model, while forward selection produced a slightly different model. Their test-set results were:

- Forward selection: R² = 0.6696, RMSE = 0.8006, MAE = 0.6493.

- Backward elimination: R² = 0.6697, RMSE = 0.8004, MAE = 0.6497.

- Bidirectional selection: R² = 0.6697, RMSE = 0.8004, MAE = 0.6497.

All three approaches performed substantially worse than the multiple regression benchmark, which had a test R² of 0.8266, RMSE of 0.5800, and MAE of 0.4231.

Overall, reducing the number of predictors through stepwise selection did not improve salary prediction. The results also show that selecting a model based on AIC or BIC alone does not guarantee better performance on new observations.

## 3. Ridge and LASSO Regression

Ridge and LASSO regression were used to examine whether regularization could improve salary prediction.

Ridge regression shrinks coefficients toward zero while retaining all candidate predictors. Its penalty was selected using 10-fold cross-validation on the training data. The minimum-error lambda was 0.1047, while the value within one standard error of the minimum was 0.3196.

On the test data, Ridge produced:

- Test R²: 0.6680

- RMSE: 0.8024

- MAE: 0.6577

LASSO uses a similar penalty but can reduce coefficients completely to zero, allowing variable selection. Its minimum-error lambda was 0.00272, while the value within one standard error was 0.11222.

On the test data, LASSO produced:

- Test R²: 0.6767

- RMSE: 0.7919

- MAE: 0.6453

LASSO performed slightly better than Ridge across all three test-set metrics, but neither method outperformed the multiple regression benchmark.

These results indicate that regularization and variable selection did not improve predictive accuracy in this analysis, despite providing alternative ways to control model complexity and correlated predictors.

## 4. Random Forest

Random Forest tested whether a nonlinear, tree-based approach could improve salary prediction. The model combined 500 regression trees and included performance, Statcast, demographic, positional, service-time, and financial-tier variables.

Unlike ordinary linear regression, Random Forest can capture nonlinear relationships and interactions without specifying each one directly.

The model produced the following test-set results:

- Test R²: 0.8531

- RMSE: 0.5338

- MAE: 0.3929

Random Forest was the strongest predictive method among those examined. Compared with the multiple regression benchmark, test R² increased from 0.8266 to 0.8531, RMSE decreased from 0.5800 to 0.5338, and MAE decreased from 0.4231 to 0.3929.

Variable importance results highlighted Service Time and Age as particularly influential. Several performance and Statcast measures also contributed, including Hard-Hit Percentage, xwOBA, xSLG, Average Exit Velocity, and Barrel Percentage.

These results suggest that salary prediction benefits from combining labor-market information with measures of player performance and contact quality.

Random Forest provided stronger predictions, but its relationships are less directly interpretable than ordinary regression coefficients. The multiple regression benchmark therefore remains useful for explaining relationships, while Random Forest was more accurate on the held-out test observations.

## 5. Surplus Value Analysis

The surplus value analysis applied the multiple regression benchmark to the test data. Predicted log salaries were converted back to dollars before comparing predicted and actual salaries.

Surplus value was calculated as:

Predicted salary − actual salary

A positive value means the model predicted a salary higher than the player's actual salary. A negative value means the player's actual salary was higher than the model's prediction.

### Largest Positive Differences

The largest positive difference occurred for Alex Rodriguez in 2015. His actual salary was $21.0 million, while the model predicted approximately $48.4 million, resulting in a difference of about $27.4 million.

Other large positive differences included:

- Carlos Santana in 2024: approximately $18.0 million.

- Justin Turner in 2021: approximately $13.1 million.

- Jed Lowrie in 2021: approximately $12.1 million.

- Jose Bautista in 2015: approximately $8.5 million.

These examples show player-seasons where actual salary was substantially below the model's prediction.

### Largest Negative Differences

The largest negative difference occurred for Carlos Correa in 2022. His actual salary was $35.1 million, compared with a predicted salary of approximately $10.3 million, resulting in a difference of about -$24.8 million.

Other large negative differences included:

- Seiya Suzuki in 2023: approximately -$15.9 million.

- Francisco Lindor in 2021: approximately -$14.5 million.

- Bryce Harper in 2018: approximately -$14.1 million.

- Javier Baez in 2023: approximately -$14.1 million.

These differences demonstrate that the model did not fully reproduce actual salaries for every player-season. Contract timing, prior performance, reputation, team circumstances, negotiation details, and other factors may contribute to salary outcomes.

Surplus value should not be interpreted as a definitive measure of whether a player was objectively overpaid or underpaid. It identifies player-seasons where actual compensation differs substantially from the model's prediction, but it does not account for every factor influencing a contract.

## 6. Main Takeaways

  1. Multiple regression provided a strong benchmark. It achieved a test R² of 0.8266, RMSE of 0.5800, and MAE of 0.4231.

  2. Best subset and stepwise selection did not improve prediction. The stepwise models were simpler but performed noticeably worse on the test data.

  3. Ridge and LASSO also performed below the benchmark. LASSO was slightly stronger than Ridge, but neither produced more accurate predictions.

  4. Random Forest performed best. It achieved a test R² of 0.8531, RMSE of 0.5338, and MAE of 0.3929, improving on all three benchmark metrics.

  5. Labor-market and performance variables both contributed. Service Time and Age were influential in Random Forest, alongside several offensive and Statcast measures.

  6. Surplus value identifies prediction differences, not definitive contract value. Large positive or negative differences show where actual salary diverged from predicted salary, but other contract-related factors may not be represented in the model.

  7. Prediction and explanation are different goals. Random Forest provided the strongest test-set prediction, while multiple regression offered a more direct way to interpret relationships between predictors and salary.

## Conclusion

This project compared model-selection methods, regularized regression, Random Forest, and surplus value analysis to determine whether alternative methods could improve MLB salary prediction.

The multiple regression benchmark provided a strong baseline, but best subset selection, stepwise selection, Ridge, and LASSO all produced weaker test-set results.

Random Forest was the strongest predictive method, achieving a test R² of 0.8531, RMSE of 0.5338, and MAE of 0.3929. Its variable importance results highlighted Service Time, Age, and several performance and Statcast measures.

The surplus value analysis demonstrated how salary predictions can be applied to individual player-seasons, while also showing that actual contracts can differ substantially from model predictions. These differences are not definitive measures of whether players are underpaid or overpaid because contracts may reflect factors not included in the model.

Overall, the findings suggest that nonlinear relationships and interactions can provide additional predictive information about MLB salaries. At the same time, regression remains useful for interpreting how player performance and labor-market factors relate to compensation.

The best approach depends on the objective: Random Forest performed best for prediction in this analysis, while multiple regression provided a clearer explanation of the modeled relationships.
