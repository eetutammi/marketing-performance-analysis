# Marketing Performance Analysis

## Overview

This project analyzes the relationship between marketing spending and weekly revenue using Meta's simulated weekly marketing dataset.

The analysis focuses on marketing performance, revenue prediction, seasonality, and whether delayed marketing effects improve model performance.

The project uses R and Quarto and combines exploratory data analysis, data visualization, regression modelling, out-of-sample prediction, and model comparison.

## Research Questions

### 1. Marketing Spending and Revenue

**How is marketing spending associated with weekly revenue after accounting for competitor activity and seasonality?**

The analysis examines:

- total marketing spending by channel
- the distribution of marketing investment across channels
- correlations between marketing channels and revenue
- the relationship between competitor sales and revenue
- regression estimates for individual marketing channels
- the role of seasonal revenue patterns

### 2. Revenue Prediction

**How accurately can weekly revenue be predicted using marketing spending, competitor activity, and seasonality?**

The analysis examines:

- training and test set performance
- out-of-sample revenue predictions
- prediction errors
- MAE, RMSE, and MAPE
- actual versus predicted revenue
- model diagnostics

### 3. Delayed Marketing Effects

**Do 1- and 2-week marketing spending lags improve revenue predictions?**

The analysis examines:

- current-week marketing spending
- one-week marketing lags
- two-week marketing lags
- whether lagged models improve predictive performance
- comparison between the baseline and lagged models

## Key Findings

### Marketing Spending and Revenue

[svg]

The regression analysis shows that marketing channels have different statistical associations with weekly revenue after controlling for competitor sales and calendar month.

TV spending shows the strongest statistical association among the marketing channels included in the model.

Print spending also shows a statistically significant positive association, while OOH, Facebook, and Search spending are not statistically significant in the baseline model.

Competitor sales are strongly associated with revenue and are therefore included as a control variable rather than treated as a marketing channel.

These results describe model-based associations and should not be interpreted as causal ROI or ROAS estimates.

### Revenue Prediction

[svg]

The baseline linear regression explains approximately **87% of the variation in revenue** in the training data.

The model is evaluated on a separate test set covering 2019.

Test-set performance:

| Metric | Result |
|---|---:|
| MAE | €109,102 |
| RMSE | €211,576 |
| MAPE | 8.31% |

The model therefore predicts weekly revenue with an average percentage error of approximately **8.3%** on the test data.

### Delayed Marketing Effects

[svg]

Adding 1- and 2-week marketing spending lags did not improve predictive performance.

The baseline model achieved:

- MAE: **€109,102**
- RMSE: **€211,576**
- MAPE: **8.31%**

The lagged model achieved:

- MAE: **€136,421**
- RMSE: **€225,036**
- MAPE: **9.85%**

The simpler baseline model therefore performed better on all three evaluation metrics.

This suggests that, for this dataset and model specification, adding simple one- and two-week marketing lags does not improve out-of-sample revenue prediction.

## Data

The project uses Meta's simulated weekly marketing dataset.

The dataset contains 208 weekly observations covering the period from November 2015 to November 2019.

Variables include:

- revenue
- TV spending
- OOH spending
- Print spending
- Facebook spending
- Search spending
- competitor sales
- newsletter activity
- events

The raw dataset is **not included in this repository**.

The dataset is available from the official Meta Robyn repository:

[Meta Robyn – Simulated Weekly Dataset](https://github.com/facebookexperimental/Robyn/blob/main/R/inst/extdata/dt_simulated_weekly.RData)

## Data Preparation

The data was checked for:

- missing values
- duplicate observations
- date range
- variable types
- marketing spending levels
- seasonal patterns

Calendar month was included in the regression models to account for recurring seasonal differences in revenue.

Events were not included in the main regression model because only two event observations were present in the dataset.

Competitor sales were included as a control variable because they show a strong relationship with revenue.

## Methods

The project uses:

- descriptive statistics
- data visualization
- correlation analysis
- seasonality analysis
- multiple linear regression
- train/test split
- out-of-sample prediction
- log-transformed regression
- lagged regression
- MAE
- RMSE
- MAPE

The training data consists of observations from 2015–2018, while the 2019 observations are used as the test set.

## Tools

- R
- Quarto
- tidyverse
- dplyr
- ggplot2
- lubridate
- broom

## Project Files

### `marketing_analysis.qmd`

The original Quarto source file containing the analysis code and written interpretation.

### `marketing_analysis.md`

The rendered Markdown version of the complete analysis, including results, tables, visualizations, and interpretations.

### `marketing_analysis_files/`

Supporting files generated by Quarto for the rendered analysis.

## Full Analysis

The complete rendered analysis is available here:

[View the full analysis](marketing_analysis.md)

The original Quarto source code is available here:

[View the Quarto source](marketing_analysis.qmd)

## Limitations

This project uses simulated data and therefore does not represent the performance of a real company's marketing channels.

The regression models describe statistical associations rather than causal marketing effects.

Marketing channels may also have carryover effects, diminishing returns, and interactions that are not fully captured by the models used in this analysis.

The lag analysis only tests simple one- and two-week delays and therefore does not provide a complete estimate of marketing carryover effects.

For a production marketing analytics project, this analysis could be extended using real business data and a more advanced Marketing Mix Modeling framework to account for carryover effects, saturation, and causal validation.

## Conclusion

The analysis provides three perspectives on marketing performance: marketing spending and revenue, revenue prediction, and delayed marketing effects.

TV spending shows the strongest statistical association among the marketing channels in the regression model, while competitor sales have a particularly strong relationship with revenue.

The baseline linear regression achieves an MAPE of approximately **8.3%** on the test set and performs better than the tested log-transformed and lagged alternatives.

Overall, the project demonstrates how regression-based marketing analytics can be used to investigate marketing performance, build revenue predictions, and evaluate alternative model specifications using out-of-sample data.
