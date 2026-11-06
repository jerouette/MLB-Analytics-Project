# MLB Salary Model: Project Outcomes

## Project Overview

This project examines whether Major League Baseball salaries are more closely associated with player performance or labor-market structure. Using 1,377 qualified hitter-season observations, the analysis compares traditional offensive statistics, advanced sabermetrics, Statcast metrics, player characteristics, contract regimes, financial tiers, and multiple-regression models.

The central finding is that contract regime and service time explain substantially more salary variation than individual performance statistics. Performance still contributes information, but its relationship with compensation depends partly on a player's position within the MLB labor market.

Salary was analyzed primarily using its natural logarithm to reduce the influence of extremely large contracts.

## 1. Simple Salary Models

### Performance Statistics

Individual regression models examined the relationship between salary and fWAR, traditional statistics, advanced sabermetrics, and Statcast measures.

fWAR had a positive relationship with salary, but its explanatory power was limited. The raw-salary model explained only 1.95% of salary variation, while the log-salary model explained 0.40%.

Traditional offensive statistics were also relatively weak individual predictors. RBI was the strongest traditional model, with an R² of 0.0424, followed by home runs (0.0308), OPS (0.0276), and runs (0.0204). Stolen bases and batting average explained less variation.

Advanced sabermetric measures also explained relatively little salary variation individually. BsR had the highest R² in this group at 0.0377, followed by wRC+ (0.0332), Def (0.0299), wOBA (0.0297), and Off (0.0229).

Among the Statcast models, xwOBA was the strongest individual performance predictor, with an R² of 0.0738. xSLG followed at 0.0579, while xISO, Hard-Hit Percentage, and Average Exit Velocity explained smaller portions of salary variation.

Although several individual performance statistics were statistically significant, their explanatory power was generally low. Even the strongest individual performance model, xwOBA, explained only about 7.38% of log-salary variation.

These results show that individual performance statistics are associated with salary but cannot explain the large differences in MLB compensation on their own.

## 2. Labor-Market and Financial Factors

Labor-market variables performed substantially better than individual performance statistics.

- Contract Regime: R² = 0.7500.

- Service Time: R² = 0.6043.

- Age: R² = 0.4459.

- Financial Tier: R² = 0.0256.

Contract regime was the strongest individual factor examined. The dataset contained 480 Pre-Arbitration, 430 Arbitration, and 467 Free Agency observations.

Using Pre-Arbitration as the reference category, the log-salary coefficients were 1.9233 for Arbitration and 2.7977 for Free Agency. Both differences were statistically significant.

Service time also explained substantially more salary variation than any individual performance measure. Adding WAR increased the service-time model's R² from 0.6043 to 0.6260. Both variables remained significant, although the improvement from adding WAR was comparatively modest.

Financial tier was much weaker on its own. Mid Market and Small Market players had lower salaries than Big Market players in the individual model, but financial tier explained only 2.56% of log-salary variation.

When contract regime and financial tier were combined, R² increased to 0.7569. Adding WAR increased it further to 0.7665, and WAR became significant after accounting for these factors.

Overall, these results indicate that contract status and career stage are much more strongly associated with salary than team financial tier alone.

## 3. Multiple Regression Models

### Baseline Model

The baseline model included contract regime, service time, age, WAR, and xwOBA.

- R² = 0.7807; adjusted R² = 0.7797.

- RMSE = 0.6418; MAE = 0.4627 on the log-salary scale.

- Contract regime remained the strongest component.

- Service time, WAR, and xwOBA were positive and statistically significant.

- Age was not significant after controlling for the other variables.

The baseline model shows that performance contributes information about salary after accounting for labor-market position. However, contract regime remains the dominant factor.

### Advanced Model

The advanced model added wRC+, financial tier, and position.

- R² = 0.7884; adjusted R² = 0.7860.

- RMSE = 0.6305; MAE = 0.4563.

- The improvement over the baseline model was statistically significant.

- Contract regime, service time, WAR, and xwOBA remained significant.

- Financial tier and position added information, while wRC+ was not significant after controlling for the other variables.

The advanced model improved fit, but the improvement was modest. AIC favored the advanced model, while BIC favored the simpler baseline model, reflecting the penalty BIC places on additional model complexity.

These results reinforce that adding more predictors can improve model fit, but the largest salary differences are still associated with labor-market structure.

## 4. Nonlinear Effects

Quadratic models examined whether salary relationships changed across levels of WAR, age, and service time.

The individual quadratic models showed that:

- WAR and WAR² explained only 1.37% of log-salary variation.

- Age and Age² increased R² from approximately 0.4459 to 0.4771, suggesting an inverted-U relationship in the simple model.

- Service time and Service Time² increased R² from 0.6043 to 0.7439.

The full nonlinear model included contract regime, quadratic service time, quadratic age, quadratic WAR, xwOBA, wRC+, financial tier, and position.

The model achieved an R² of 0.8028 and adjusted R² of 0.8002. RMSE decreased to 0.6086, and MAE decreased to 0.4364. The nested-model comparison favored the nonlinear model, and both AIC and BIC decreased.

Service Time² remained significant in the full model, while Age, Age², and WAR² were not significant. WAR was only marginally significant.

The clearest nonlinear result was service time. Salary does not appear to increase at a constant rate throughout a player's career. Instead, the relationship levels off as service time grows and contract status changes.

## 5. Interaction Effects

Four models examined whether the relationship between performance and salary varied by contract regime, service time, or financial tier.

Contract Regime × WAR: R² = 0.7907; RMSE = 0.6270. The relationship between WAR and salary was stronger in Arbitration and Free Agency than in Pre-Arbitration.

Contract Regime × xwOBA: R² = 0.7909; RMSE = 0.6268. The xwOBA interactions for Arbitration and Free Agency were significant.

Service Time × WAR: R² = 0.7911; RMSE = 0.6264. This model had the strongest overall fit among the four interaction models.

Financial Tier × WAR: R² = 0.7886; RMSE = 0.6301. The interaction was not statistically significant.

The Service Time × WAR interaction coefficient was 0.0107 (p = 2.67 × 10⁻⁵). This indicates that the relationship between WAR and salary became stronger as service time increased.

The contract-regime interactions also showed that performance was associated with salary differently across contract stages. In contrast, the Financial Tier × WAR interaction was not significant (overall p = 0.427).

These results suggest that performance is rewarded differently depending on a player's career stage and contract position, while financial tier did not significantly change the relationship between WAR and salary in the tested model.

## 6. Model Diagnostics and Limitations

Visual diagnostics showed departures from standard linear-regression assumptions. Q-Q plots showed tail departures, while residual-versus-fitted and Scale-Location plots suggested that residual variance was not constant.

Several observations had unusual residuals, higher leverage, or greater influence, although no single observation appeared to completely determine the results.

Actual-versus-predicted plots captured the broad salary pattern, but individual observations remained spread around the 45-degree reference line. Some lower-paid players were overpredicted, and unusual salary outcomes remained difficult to capture.

The analysis is limited to qualified MLB hitters rather than every professional player. The models show associations rather than causal effects, and the reported R² and error measures describe fitted models on the observed data. They should not be interpreted as evidence of out-of-sample predictive accuracy.

## 7. Main Takeaways

  1. Contract regime is the strongest individual factor examined. It explained 75.00% of log-salary variation on its own.

  2. Service time is highly informative. It explained 60.43% of log-salary variation in the linear model, while the quadratic model increased this to 74.39%.

  3. Individual performance statistics explain substantially less salary variation. xwOBA was the strongest individual performance predictor, with an R² of 0.0738.

  4. Performance remains relevant after controlling for labor-market structure. WAR and xwOBA were significant in the baseline and advanced models.

  5. The relationship between performance and salary depends on career stage. Service Time × WAR and contract-regime interactions were significant, while Financial Tier × WAR was not.

  6. Nonlinear service-time effects improve the model. The relationship between service time and salary is not adequately represented by a straight line alone.

## Conclusion

The project supports the conclusion that MLB salaries are associated with both player performance and labor-market structure, but labor-market structure appears to be the dominant factor in these data.

Individual measures such as WAR, traditional statistics, sabermetrics, and Statcast metrics were often statistically significant, yet their simple models explained relatively little salary variation. Contract regime and service time explained substantially more.

Performance was not irrelevant. WAR and xwOBA continued to contribute after controlling for major labor-market variables, and the significant interaction results suggest that performance is associated with salary more strongly as players gain service time or move into Arbitration and Free Agency.

The overall conclusion is that MLB salary cannot be understood through on-field production alone. Compensation also reflects the contractual system that determines when players gain bargaining power and how their performance is translated into salary.
