# Marketing Performance Analysis

This project analyzes the relationship between marketing spending and weekly revenue using simulated business data.

The analysis focuses on understanding marketing performance, accounting for seasonality, predicting revenue, and evaluating whether delayed marketing effects improve model performance.

## Objectives

The main objectives of the analysis are:

- Examine the relationship between marketing spending and revenue
- Compare marketing channels using regression models
- Account for seasonal revenue patterns
- Build a revenue prediction model
- Evaluate model performance on unseen data
- Test whether 1- and 2-week marketing lags improve predictions
- Compare linear and log-transformed regression models

## Data

The project uses Meta's simulated weekly marketing dataset.

The dataset contains weekly observations of:

- Revenue
- TV spending
- OOH spending
- Print spending
- Facebook spending
- Search spending
- Competitor sales
- Newsletter activity
- Events

The dataset contains 208 weekly observations covering the period from November 2015 to November 2019.

The dataset is available from the official Meta Robyn repository:

[Meta Robyn – Simulated Weekly Dataset](https://github.com/facebookexperimental/Robyn/blob/main/R/inst/extdata/dt_simulated_weekly.RData)

## Analysis

The analysis consists of several stages:

### 1. Exploratory Data Analysis

The project examines:

- Revenue trends over time
- Marketing spending by channel
- Marketing spend distribution
- Correlations between marketing channels and revenue
- Competitor sales
- Revenue seasonality

### 2. Regression Analysis

A multiple linear regression model is used to estimate the relationship between revenue and:

- TV spending
- OOH spending
- Print spending
- Facebook spending
- Search spending
- Competitor sales
- Calendar month

The regression model is used as an interpretable baseline for understanding the data.

### 3. Revenue Prediction

The data is divided into training and test sets.

The model is trained using data from 2015–2018 and evaluated on unseen data from 2019.

The following metrics are used:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Mean Absolute Percentage Error (MAPE)

### 4. Alternative Models

Two alternative approaches are evaluated:

- Log-transformed regression
- Regression models including 1- and 2-week marketing lags

The models are compared using the same test set.

## Key Results

The baseline linear regression explains approximately 87% of the variation in revenue on the training data.

On the test set, the baseline model achieved:

| Metric | Result |
|---|---:|
| MAE | €109,102 |
| RMSE | €211,576 |
| MAPE | 8.31% |

The baseline linear regression performed better overall than the log-transformed and lagged models based on test-set MAE and MAPE.

The regression results also show a strong statistical association between TV spending and revenue after controlling for the other variables in the model.

Competitor sales were strongly associated with revenue and were therefore included as a control variable rather than treated as a marketing channel.

## Business Interpretation

The analysis demonstrates how marketing analytics can be used to:

- Identify relationships between marketing investment and revenue
- Account for seasonality and competitor activity
- Compare marketing channels
- Build revenue prediction models
- Evaluate model performance using unseen data
- Support data-driven marketing decisions

The regression coefficients provide model-based estimates of associations between marketing spending and revenue. They should not be interpreted directly as causal ROI or ROAS estimates without additional causal validation.

## Limitations

This project uses simulated data and therefore does not represent the performance of a real company's marketing channels.

The regression approach also has limitations when estimating causal marketing effects. Marketing channels may have carryover effects, diminishing returns, and interactions that are not fully captured by the baseline model.

The dataset also contains only a small number of observed event occurrences, so events were not included in the main regression model.

For a production marketing analytics project, this analysis could be extended using real business data and a more advanced Marketing Mix Modeling framework to account for carryover effects, saturation, and causal validation.

## Tools

- R
- tidyverse
- ggplot2
- lubridate
- broom
- Quarto

## Project Structure

```text
marketing-performance-analysis/
│
├── marketing_analysis.qmd
├── marketing_analysis.html
├── marketing_analysis.md
└── README.md
```

## Author

Eetu Tammi
